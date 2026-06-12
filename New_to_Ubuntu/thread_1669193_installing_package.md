---
title: "installing package"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by gupta_sumesh63 on 2011-01-17
hello there,

I have downloaded the package cairo 1.8.10 tar.gz from their site.
I uncompressed it using the following command

[PHP]tar -xzvf cairo_1.8.10-2ubuntu1.debian.tar.gz
[/PHP]

When I go to the uncompressed dir (debian in this case) there is no configure file there. Following files / folders have been extracted

[PHP]patches - folder
source  - folder
changelog
compat
control
copyright
libcairo2.install
libcairo2.install.in
libcairo2.install.opt
libcairo2.symbols
libcairo2-dev.install
libcairo2-doc.doc-base
libcairo2-doc.install
libcairo-directfb2.links
libcairo-directfb2-dev.links
libcairo-directfb2-dev.postinst
libcairo-directfb2-udeb.install
rules
watch
[/PHP]

Can anybody tell me how can I install it?

I'll be grateful. I want to use the package with tovid.

Thanks in anticipation.

---

### Post by Smart Viking on 2011-01-17
try
```
autoconf
```
You need the package installed first with
```
sudo apt-get install autoconf
```

---

