---
title: "Nocat"
date: 2005-08-22
forum: Networking &amp; Wireless
---

### Post by asimon623 on 2005-08-22
I need to use this for authentication into my wireless network..I dont really know where to start...can anybody help me?

---

### Post by ape on 2005-08-23
Best place to start is probably [http://nocat.net](http://nocat.net) .  This should have the info you need to get started with your particular network.

---

### Post by Spring on 2008-04-27
Hello Nocat users,

I am a newbie for Nocat software. I hope you can help me a little.
I want to introduce my self a little...normaly i am a webdesigner and on the weekends i am working on my wireless project, this project i started on 2003 we have 8 nodes in and 50 users. The users have a free access to internet, we use cbq init script, dns, dhcp, snortsam on a ubuntu7, But every thing is open to the internet, some users don&#65533;t now who we are, so i wanne show on the first connection our information and than the users can continu on clicking on a button.  I am looking for software to give the users a welcome page and then click on the okay button and have internet access. We have a second server (dns server, redhat 9) on the same subnet (only eth0, no gateway) so i can install Nocat software!? But this is not the real gateway, i can change the users dhcp setting the new gateway (dns server, Nocat) The users see the welkom page i continu to the real (old gateway). My question, can Nocat do this white NoCatSplash? I try to install this on the a test server but i get a error on install. 
See this is my logs, and i have install glib but a newer version... 
So can anybody help me i do the right solution and help me to install to see how its working, NoCatSplash.

Thank you to read my (good?) solution and problem.... 

[root@auth NoCatSplash-nightly]# /configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets ${MAKE}... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets ${MAKE}... (cached) yes
checking for ranlib... ranlib
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: You must have glib-1.2 installed.

---

