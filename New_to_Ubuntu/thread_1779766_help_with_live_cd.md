---
title: "help with live cd"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by teckra on 2011-06-10
d/l unbuntu and created CD.  Booted from CD.   No network connection.  How do  I load drivers for my NIC on my Cpq/HP NX9600 ?   I have U v11.04.  Everything I have found on internet is for earlier versions of U.    appears to have new interface with v11.04.  any help or links ?  thanks

---

### Post by wildmanne39 on 2011-06-10
> **teckra said:**
> d/l unbuntu and created CD.  Booted from CD.   No network connection.  How do  I load drivers for my NIC on my Cpq/HP NX9600 ?   I have U v11.04.  Everything I have found on internet is for earlier versions of U.    appears to have new interface with v11.04.  any help or links ?  thanksHi, if you are connected with a ethernet cable you should have internet access, I am not sure about trying to connect a wireless card until you do any actual install. You can look in additional drivers to see if there is one for your wireless but you have to be connected to the net with a wired connection.
Also post the results of this command
```
lspci
```type that into a terminal. Open the terminal with ctrl+alt+t

---

### Post by beew on 2011-06-11
I think you should make a live usb with persistence if you want to install additional drivers as you may need to reboot and with the CD you lose everything on reboot, besides, it is painfully slow.

---

### Post by apollothethird on 2011-06-11
> **beew said:**
> I think you should make a live usb with persistence if you want to install additional drivers as you may need to reboot and with the CD you lose everything on reboot, besides, it is painfully slow.

Or he can use the live CD to install Ubuntu on his system then start searching and trying to get support for his nic.  I find the persistent installation to be slow also.

Also, there's so much support for various adapters that I don't recall having an adapter that wasn't supported.  So since this is so rare, unless your nic is builtin, I'd purchase another nic that is supported.  They are pretty inexpensive.

You can usually find a Neatgear wireless nic for around $5.00.  That should suffice while you're using the Live CD until you get the necessary driver support for your builtin nic.

When using Windows, I had always tried to get hardware that was supported for Windows, I believe Mac users do the same.  This is something that Linux users should consider also.  Spending a few dollars for the a supported device might be more economical time-wise in many cases than spending many precious hours trying to make something that isn't readily supported work.

But again, my suggestions is methods for minimising your downtime.  I'm sure your experience in researching and building support for problem hardware can be a good contribution to the Linux community also.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by I2k4 on 2011-06-12
Excellent step by step for Live USB here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

At end of Show Me How step 2, before running the installation procedure, configure the Pendrive installer to use at least half the USB drive for Persistence.

Persistence permits adding extras and saving settings between boots on Live USB, best way to test out different versions and configurations without committing to the main hard drive.

---

