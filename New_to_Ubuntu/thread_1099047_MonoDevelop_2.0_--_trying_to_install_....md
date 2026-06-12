---
title: "MonoDevelop 2.0 -- trying to install ..."
date: 2009-03-17
forum: New to Ubuntu
---

### Post by cwmoser on 2009-03-17
I am trying to install MonoDevelop 2.0 on Gutsy (Ubuntu 8.04).

I get this error:
[COLOR="DarkRed"]configure: error: Please install mono version 2.0 or later to install MonoDevelop.
[/COLOR]



***_This is what I did to try to install MonoDevelop 2.0 Beta 2 (1.9.3):_***

[FONT="Courier New"]

$ sudo apt-get install  build-essential mono-gmcs libmono-dev libpango1.0-dev libgtk2.0-dev libgtksourceview2.0-cil libgecko2.0-cil monodoc libmono-system-runtime2.0-cil libmono-cairo2.0-cil gettext



$ wget [http://go-mono.com/sources/monodevelop/monodevelop-1.9.3.tar.bz2](http://go-mono.com/sources/monodevelop/monodevelop-1.9.3.tar.bz2)
$ bunzip2 monodevelop-0.16.tar.bz2
$ tar xvf monodevelop-0.16.tar
$ cd monodevelop-0.16


$ sudo apt-get install mono-2.0-devel




$ ./configure --prefix=`pkg-config --variable=prefix mono`
[COLOR="DarkRed"]configure: error: Please install mono version 2.0 or later to install MonoDevelop.
[/COLOR]

$ make
$ sudo make install
[/FONT]

Any help is appreciated.

Carl

---

### Post by yeats on 2009-03-17
Looks like you've installed everything but this.  Try:

```
sudo apt-get install mono
```

Then re-run the ./configure script.

---

### Post by cwmoser on 2009-03-17
Below shows what happens when I try to install mono:

$ sudo apt-get install mono

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidate

---

### Post by directhex on 2009-03-17
Gutsy is 7.10. There's your first issue.

Hardy (8.04) does not have Mono 2.0, there's your second issue.

If you want MD2, run Jaunty & use the packages in there.

---

### Post by cwmoser on 2009-03-17
> **directhex said:**
> Gutsy is 7.10. There's your first issue.

Hardy (8.04) does not have Mono 2.0, there's your second issue.

If you want MD2, run Jaunty & use the packages in there.


Opps.  I get those names confused.  I run 8.04

[COLOR="DarkRed"]$ cat /etc/issue
Ubuntu 8.04.2 \n \l[/COLOR]

So, how do I get Mono 2.0 in Hardy 8.04?

Thanks

Carl

---

### Post by directhex on 2009-03-17
> **cwmoser said:**
> Opps.  I get those names confused.  I run 8.04

[COLOR="DarkRed"]$ cat /etc/issue
Ubuntu 8.04.2 \n \l[/COLOR]

So, how do I get Mono 2.0 in Hardy 8.04?

Thanks

Carl

You don't. Hardy shipped with 1.2.6. The highest version you can safely upgrade to via packages is 1.9.1. After that, packaging structure changed, and an upgrade would cause severe issues. You could compile it yourself to a private prefix...

---

