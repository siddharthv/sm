XS_INCLUDE ?= /usr/include

PREFIX ?= /opt/xensource/sm/snapwatchd
INITDIR ?= /etc/rc.d/init.d
DESTDIR ?= 

PYTHON_INCLUDE_DEFAULT := $(dir $(shell find /usr/include/ -maxdepth 2 -path \*/python\*/Python.h -type f | head -1))
PYTHON_INCLUDE ?= $(PYTHON_INCLUDE_DEFAULT)

CFLAGS ?= -O2
CFLAGS += -I$(PYTHON_INCLUDE) -I$(XS_INCLUDE) -fPIC

.PHONY: all
all: install
	@ :

.PHONY: install
install: xslib.py snapwatchd
	mkdir -p $(DESTDIR)$(PREFIX)
	install -m 644 $^ $(DESTDIR)$(PREFIX)
	chmod +x $(DESTDIR)$(PREFIX)/snapwatchd
	cp xslib.py $(DESTDIR)$(PREFIX)/snapwatchd
	mkdir -p $(DESTDIR)$(INITDIR)
	cp snapwatchd.init $(DESTDIR)$(INITDIR)/snapwatchd
	chmod +x $(DESTDIR)$(INITDIR)/snapwatchd

.PHONY: clean
clean:
	rm -f xslib.pyc xslib.pyo

