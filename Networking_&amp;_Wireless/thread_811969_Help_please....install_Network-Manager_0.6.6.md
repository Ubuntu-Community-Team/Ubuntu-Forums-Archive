---
title: "Help please....install Network-Manager 0.6.6"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Amstell on 2008-05-29
I am having issues with my network manager 0.6.5.  I downloaded 0.6.6 from

[http://www.nabble.com/Release:-0.6.6-td15886049.html](http://www.nabble.com/Release:-0.6.6-td15886049.html)

 I have tried compiling it but am getting this issue with ./configure

```
checking for GNOME_KEYRING... yes
checking for LIBNL... configure: error: Package requirements (libnl-1 >= 1.0-pre8) were not met:

Requested 'libnl-1 >= 1.0-pre8' but version of libnl is 1.0-pre6

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBNL_CFLAGS
and LIBNL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I have done

apt-get install build-dep networkmanager

apt-get install ppp-dev

I'm using 7.10 (don't like hardy-too many problems) so i would just like to upgrade my network manager to see if that fixes the problem.

Thanks for any help you all may have.

Cheers

---

### Post by jimv on 2008-05-29
You could try using WICD instead of Network Manager.  A lot of people make the switch and end up like WICD a lot more.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Amstell on 2008-05-29
I have tried wicd.  I switch between wireless networks a lot and I run into a lot of problems with wep/wpa verification with wicd.

Thanks for the advise though, any other suggestions.

---

