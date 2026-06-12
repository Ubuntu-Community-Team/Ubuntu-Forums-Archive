---
title: "Problem With Skype"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by the.dark.lord on 2011-06-04
I installed Skype both from their website, and from the Ubuntu repository- and I get the same error when I try to run it:

```
Fatal: Cannot mix incompatible Qt libraries
Aborted

```

The results of "ldd /usr/bin/skype | grep -i qt" are:

```
	libQtDBus.so.4 => /usr/lib32/libQtDBus.so.4 (0xf7619000)
	libQtGui.so.4 => /usr/local/bin/ztemtApp/bin/libQtGui.so.4 (0xf6cf1000)
	libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf6bca000)
	libQtCore.so.4 => /usr/local/bin/ztemtApp/bin/libQtCore.so.4 (0xf698f000)
	libQtXml.so.4 => /usr/lib32/libQtXml.so.4 (0xf656a000)

```

I'm using 64-bit Lucid Lynx (10.04).

What shall I do now?

---

### Post by HermanAB on 2011-06-04
Howdy,

Go back to the Skype web site and download the Static version.  It includes *all* libraries in a statically linked program.  Put it in your home directory ~/skype-static, or in /usr/local/skype-static and run it.  La voila.

---

### Post by the.dark.lord on 2011-06-04
> **HermanAB said:**
> Howdy,

Go back to the Skype web site and download the Static version.  It includes *all* libraries in a statically linked program.  Put it in your home directory ~/skype-static, or in /usr/local/skype-static and run it.  La voila.

Thanks a bunch, Herman! That worked. :)

---

