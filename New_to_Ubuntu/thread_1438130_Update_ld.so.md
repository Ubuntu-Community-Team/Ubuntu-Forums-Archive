---
title: "Update ld.so"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Ranemills on 2010-03-24
Hello,

I'm installing XFree86 at the moment because it's a requirement for the ATI driver I'm trying to install. However, I got the message in the attached image during the installation process.

What is ld.so? and how do I go about updating it?

I looked in the package manager and I've googled it and can't find anything.

Thanks in advance

---

### Post by Didius Falco on 2010-03-26
> **Ranemills said:**
> Hello,

I'm installing XFree86 at the moment because it's a requirement for the ATI driver I'm trying to install. However, I got the message in the attached image during the installation process.

What is ld.so? and how do I go about updating it?

I looked in the package manager and I've googled it and can't find anything.

Thanks in advance

Try updating libc-bin. That is, according to this manpage, the file that provides ld.so:

[http://manpages.ubuntu.com/manpages/karmic/man8/ld.so.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/ld.so.8.html)

I hope this helps...

Regards,
Didius

---

### Post by Ranemills on 2010-03-29
Hey Didius,

Thanks for the reply, but it didn't seem to work.

I found [http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/) and ran the code they said after installing git:

```
git clone git://sourceware.org/git/glibc.git
cd glibc
git checkout --track -b glibc-2_11-branch origin/release/2.11/master
```That didn't seem to work as I still got the same response from the installer.

This site [http://www.unixguide.net/linux/faq/05.05.shtml](http://www.unixguide.net/linux/faq/05.05.shtml) says to get ld.so at [http://tsx-11.mit.edu/pub/linux/packages/GCC/](http://tsx-11.mit.edu/pub/linux/packages/GCC/) but I can't access that, it times out. 

Anyone have any ideas?

---

### Post by Didius Falco on 2010-03-30
Try this FAQ out:

[http://www.faqs.org/docs/Linux-HOWTO/XFree86-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/XFree86-HOWTO.html)

Here is a section that looks like it may be what you need:

> Remember that these tar files are packed relative to /usr/X11R6, so it's important to unpack the  files there.You need to make sure that /usr/X11R6/bin  is on your path.  This can be done by editing your system default /etc/profile or /etc/csh.login (based on the shell that you, or other users on your system, use). Or  you can simply add the directory to your personal path by modifying .bashrc or .cshrc,  based on your shell.
You also need to make sure that /usr/X11R6/lib can be located by **ld.so**, the runtime linker. To  do this, add the line:


```
/usr/X11R6/lib
```

to the file /etc/ld.so.conf,  and run /sbin/ldconfig, as root.






Post back on if this is the fix - I've never used XFree86, so I'm just doing searches to try and find an answer to this.

Regards,

Didius

---

### Post by Ranemills on 2010-03-30
Hey,

Thanks for your help so far but that didn't seem to work either. The contents of /etc/ld.so.conf was originally```
include /etc/ld.so.conf.d/*.conf
```
so I thought it would be odd just to put```
/usr/X11R6/lib
``` on the end. But that didn't work and neither did trying with include at the start.

However, I hadn't done anything on that howto to install it. On the bright side, I should now hopefully run into less problems once we fix this.

Any more ideas?

Thanks again

---

### Post by 3rdalbum on 2010-03-30
> **Ranemills said:**
> Hello,

I'm installing XFree86 at the moment because it's a requirement for the ATI driver I'm trying to install.

Whoa, no! The ATI driver will work fine with Xorg (the X server that ships with Ubuntu). You don't need to install XFree86, and in fact I'd recommend you DON'T do that. You'd probably break your system.

Why not just install the ATI driver from System > Administration > Hardware Drivers?

---

### Post by Ranemills on 2010-03-30
When I tried the Hardware Driver that you are suggesting, it just blacked out my screen when I restarted and the caps lock light started flashing.

So I dug around the net a bit and found an ATI driver specifically for my card on the AMD website. I downloaded this and the documentation stated XFree86 as a dependency. 

However, looking over the documentation again, there are two sections for minimum system requirements. The documentation is here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat102-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat102-inst.pdf)

The sections are on page 2 and 3.

One section states Xorg and the other states XFree86.

So you say don't install XFree86? How about the ATI driver?

My card is a Radeon HD3400, I think.

---

