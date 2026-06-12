---
title: "using b43 wireless driver in 7.10"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by VCSkier on 2007-12-06
I'm wondering if it is possible to install and use the new [b43]("http://linuxwireless.org/en/users/Drivers/b43") driver for broadcom wireless chipsets on Ubuntu 7.10.  This new driver should give improved performance, and I know it will be included in the kernel for Hardy (2.6.24), but is there a way to add just that module to the Gutsy kernel?  Thanks.

---

### Post by sbodas on 2007-12-09
I was able to get the b43 driver working under Gutsy by building the "wireless-compat-2.6" sources ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)) for 2.6.22 kernels.  The above link seems to be down, so here's the direct link:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

You'll have to compile the linux-2.6.22 kernel yourself first though, but it was worth it to get wireless working on my new HP laptop.

---

### Post by VCSkier on 2007-12-10
How does performance compare to that of ndiswrapper?  Things seems to be going well with it for me, so I may forgo compiling the kernel and just wait for Hardy to get the new drivers.

---

### Post by Robert Maciejewski on 2007-12-10
Go to the link [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133) and you will download driver for bcm in deb's.

---

### Post by sbodas on 2007-12-11
I couldn't tell you about ndiswrapper because I never tried it.  The performance of the b43 driver is good, and it worked right away with NetworkManager.  I prefer to use native Linux drivers when possible; since the b43 driver is working, I decided to build my own kernel to get it to work.  Last time I tried ndiswrapper, I wasted about a day trying to get it to work, so I figured building my own kernel would take less time.  Hardy is just too far away for me to wait...

Robert: I think the deb you linked to is for the bcm43xx driver, which doesn't work with newer broadcom cards.

---

### Post by Kapitan on 2008-04-16
I have a question about the driver loading,
i post here before opening a new one.

I have tryied the b43 with wireless-compat.
The driver work with the b43load utility that
comes with the driver.

But i want to load on boot.

so i have added a file in /etc/modprobe.d/ 
with a lonely line:

install b43-load /usr/sbin/b43load b43

The driver doesn't load on boot anyway. Why?

Maybe i miss something

---

### Post by Kapitan on 2008-04-24
i was missing something.

I add a line in /etc/modules,
that is the alias of the install
command...

so after "fuse" i'va added b43-load
and it perfectly loads at boot time.

:)

---

