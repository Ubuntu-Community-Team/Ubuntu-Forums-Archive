---
title: "linux distro as server?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by Krewie on 2008-01-25
Hi, im currently looking for a linux distro to use as a server, there are many options but i was wondering if fedora core 8 is the way to go. Some people say xubuntu and other suse so i was wondering what linux distro to prefer and why?, thx!

---

### Post by gnelson on 2008-01-25
What kind of server do you want (Fileserver, webserver, etc)?

I did an Ubuntu server based on [this tutorial ]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html")and it has worked out great.  But it really depends on what your needs are.

---

### Post by bwtranch on 2008-01-25
I would go with Gentoo.

---

### Post by Mithrilhall on 2008-01-25
I would go with Debian.

---

### Post by HermanAB on 2008-01-25
It doesn't matter.  Linux is Linux is Linux...

The differences between distributions are largely superficial and mostly affects the desktop setup.  Most servers do not run X and on those that do, you want to use a light weight desktop, therefore Xfce or IceWM.  So, while your choice of desktop system matters, your choice of server system doesn't really.

Cheers,

Herman

---

### Post by maybeway36 on 2008-01-25
What do you know how to use? :P That's really what it comes down to.

---

### Post by salazar on 2008-01-25
ubuntu 7.04 server  + samba =  my fileserver

---

### Post by andguent on 2008-01-25
I would have to heavily agree with maybeway36. Use what you know, or be prepared to learn.

I personally recommend Debian or Ubuntu simply due to package management and ease of installing new software. apt-get and .deb files are so nice, especially for those that use the command line. Debian and Ubuntu are both very close in structure and configuration concepts, if you know one, you know 90%+ of the other (from the command line at least).

Debian moves significantly slower in updates and new software than Ubuntu. If you want to install a new server and expect patches to be around for years, make sure you go with either Debian, or Ubuntu LTS. If you have specialty hardware requirements that neither of those can handle, try the newer versions of Ubuntu, but plan on updating your core files every year or more.

Other distributions will do what you want, if you know how to configure them. Gentoo takes forever to install new software on though.

---

### Post by sloopveedub on 2008-01-25
I chose Xubuntu.  I'm not very experienced with the CLI yet so I knew I needed a GUI to help me out.  So, Xubuntu with its lightweight Xfce based desktop fit the bill.  Second, the forums/chat/etc. support for Ubuntu is excellent, which was my other key requirement.  Though, I must admit that my first server attempt was with SUSE 10.3 -- a very good disto, but the user support just isn't as good.

---

