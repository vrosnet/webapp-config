#
# webapp-config/doc/Makefile
#		Simple Makefile to rebuild the documentation from the
#		docbook XML sources
#
#		Part of the webapp-config package
#
# Copyright (c) 1999-2005 Gentoo Foundation
#       Released under v2 of the GNU GPL
#
# Author(s)     Stuart Herbert <stuart@gentoo.org>
#               Renat Lumpau   <rl03@gentoo.org>
#               Gunnar Wrobel  <php@gunnarwrobel.de>
#
# ========================================================================

MAN_PAGES = webapp-config.8 webapp-config.5 webapp-eclass.5
HTML_PAGES = webapp-config.8.html webapp-config.5.html webapp-eclass.5.html

all: man html

html: $(HTML_PAGES)

man: $(MAN_PAGES)

clean:
	rm -f $(MAN_PAGES)
	rm -f $(HTML_PAGES)

%.html: %.xml
	@echo HTML $@
	@xmlto html-nochunks $< 2>/dev/null

%: %.xml
	@echo MAN $@
	@xmlto man $< 2>/dev/null
	@cat $@ | sed -e 's/$$/.fred/g;' | tr -d '\n' | sed -e 's/.fred.fred\./.fred./g;' | sed -e 's/.fred/\n/g;' > $@.temp
	@mv $@.temp $@
