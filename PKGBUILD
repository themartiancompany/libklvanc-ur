# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Daniel Bermond <dbermond@archlinux.org>

_os="$( \
  uname \
    -o)"
pkgname=libklvanc
pkgver=1.6.0
_pkgver="vid.obe"
pkgrel=1
_pkgdesc=(
  'Library for parsing/generation'
  'of Vertical Ancillary Data (VANC)'
)
arch=(
  'x86_64'
  'i686'
  'arm'
  'armv7l'
  'armv6l'
  'mips'
  'pentium4'
  'powerpc'
)
_http="https://github.com"
_ns="stoth68000"
url="${_http}/${_ns}/${pkgname}"
license=(
  'LGPL'
)
depends=(
)
if [[ "${_os}" == "GNU/Linux" ]]; then
  depends+=(
    'glibc'
  )
elif [[ "${_os}" == "Android" ]]; then
  depends+=(
    'ndk-sysroot'
  )
fi
source=(
  "${url}/archive/${_pkgver}.${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha256sums=(
  '5076ca48455a4ef4ead2cd880ba189b21937a9ad8fd458adfc133d7bb1c948c3'
)

prepare() {
  cd \
    "${pkgname}-${_pkgver}.${pkgver}"
  ./autogen.sh \
    --build
}

build() {
  cd \
    "${pkgname}-${_pkgver}.${pkgver}"
  ./configure \
    --prefix='/usr'
  make
}

package() {
  make \
    -C \
      "${pkgname}-${_pkgver}.${pkgver}" \
    DESTDIR="${pkgdir}" \
    install
  # the -debug package is preventing
  # binary executables from being stripped
  strip \
    "${STRIP_BINARIES}" \
    "${pkgdir}/usr/bin"/*
} 
