---
title: "WLAN under dapper drake"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by dapissarenko on 2006-08-30
Hello!

I have an Intel PRO/Wireless 2200 BG card and want to install it under ubuntu.

I followed the instructions on

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

but could not establish a connection.

I tried to install ndiswrapper files (ndiswrapper_1.8.orig.tar.gz and ndisgtk_0.6.orig.tar.gz) from

[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

but this didn't work - I could not execute "sudo dpkg" since there were no deb files in extracted ndiswrapper_1.8.orig.tar.gz and ndisgtk_0.6.orig.tar.gz.

Please tell me how I can install "Windows wireless drivers" tool for ubuntu (ndisgtk_0.6.orig.tar.gz).

In which archive are the deb files located?

TIA

dapissarenko

---

### Post by lorre on 2006-08-30
I added the 'ubuntu live cd' to the sources file and installed ndiswrapper from synaptic

---

### Post by dapissarenko on 2006-08-31
Thanks!

---

