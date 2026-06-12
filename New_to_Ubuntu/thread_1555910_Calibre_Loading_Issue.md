---
title: "Calibre Loading Issue"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by yalç&#305;n can on 2010-08-18
Hello folks, I'm using Ubuntu 10.04 with calibre 0.6.42. My problem is Calibre do not load when I'm using Ubuntu Turkish. When i use Ubuntu in English there is no problem at all. Everything works like a charm. I started Calibre from command line and here is the output. Thanks for the help.

```
Traceback (most recent call last):
  File "/usr/bin/calibre", line 18, in <module>
    from calibre.gui2.main import main
  File "/usr/lib/calibre/calibre/gui2/__init__.py", line 18, in <module>
    from calibre.ebooks.metadata.meta import get_metadata, metadata_from_formats
  File "/usr/lib/calibre/calibre/ebooks/metadata/meta.py", line 9, in <module>
    from calibre.ebooks.metadata.opf2 import OPF
  File "/usr/lib/calibre/calibre/ebooks/metadata/opf2.py", line 14, in <module>
    from lxml import etree
  File "lxml.etree.pyx", line 183, in init lxml.etree (src/lxml/lxml.etree.c:140535)
LookupError: unknown encoding: ASCII

```

---

