pkgname=dwm-git
_pkgname=dwm
pkgver=6.3.r0.d39e2f34
pkgrel=1
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft')
makedepends=('git')
provides=('dwm')
conflicts=('dwm')
source=("$_pkgname::git+http://github.com/trevorsweigart/dwm"
  "config.h")
sha256sums=('SKIP'
  'SKIP')

prepare() {
  cd $_pkgname
  cp -fv "$srcdir/config.h" config.h
}

build() {
  cd $_pkgname
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $_pkgname
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -m644 -D README "$pkgdir/usr/share/doc/$pkgname/README"
  install -m644 -D dwm.desktop "$pkgdir/usr/share/xsessions/dwm.desktop"
}

# vim:set ts=2 sw=2 et:
