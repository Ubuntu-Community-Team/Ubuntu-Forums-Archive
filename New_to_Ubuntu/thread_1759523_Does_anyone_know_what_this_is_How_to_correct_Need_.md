---
title: "Does anyone know what this is? How to correct? Need to correct?"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-05-15
From my machine (Ubuntu 10.04), here is a portions of the output from --

```
dmesg
```

```

[  809.698947] operapluginwrap[2116]: segfault at 0 ip (null) sp bfa3b93c error 4 in libm-2.11.1.so[110000+24000]
[  809.762668] operapluginwrap[2120]: segfault at 0 ip (null) sp bf8546bc error 4 in libdl-2.11.1.so[110000+2000]
[  809.796490] operapluginwrap[2121]: segfault at 0 ip (null) sp bfad326c error 4 in libpthread-2.11.1.so[110000+15000]
[  810.205912] operapluginwrap[2124]: segfault at 0 ip (null) sp bfd306ac error 4 in libstdc++.so.6.0.13[110000+e9000]
[  810.222576] operapluginwrap[2125]: segfault at 0 ip (null) sp bff267fc error 4 in libgcc_s.so.1[110000+1d000]
[  810.239050] operapluginwrap[2126]: segfault at 0 ip (null) sp bfd44f2c error 4 in libstdc++.so.6.0.13[110000+e9000]
[  810.255744] operapluginwrap[2127]: segfault at 0 ip (null) sp bfefd3ec error 4 in libdl-2.11.1.so[110000+2000]
[  810.319863] operapluginwrap[2129]: segfault at 0 ip (null) sp bf860dac error 4 in libXt.so.6.0.0[110000+4f000]

```

What is it? Do I need to correct this? How?

Thanks in advance for any feedback guys.

---

### Post by conradin on 2011-05-16
Using opera?
Maybe try removing opera?
Or maybe its some like it says, some plugin in opera is misbehaving. you could try using flash aid (im guessing flash is misbehaving, or installing gnash.) I like opera too, so I would understand if you didnt want to remove it.

---

### Post by Matt__ on 2011-05-16
first try this to fix packages.
```
sudo apt-get update

sudo apt-get install -f
```

if the problem is still there reinstall the culprit c++ libraries or possibly the older versions

look here
[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)

and if that dosnt work here
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145)

---

### Post by ClientAlive on 2011-05-16
> **Matt__ said:**
> first try this to fix packages.
```
sudo apt-get update

sudo apt-get install -f
```

if the problem is still there reinstall the culprit c++ libraries or possibly the older versions

look here
[http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)

and if that dosnt work here
[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/#comment-145)


sorry I went mia for a bit there. I had something else come up. I did try that first thing and I still get the errors but it looks like a couple of them have changed to a different error now. Doh!

I'll check out those links as soon as I get a chance.

Thanks

---

