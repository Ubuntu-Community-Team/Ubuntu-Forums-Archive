---
title: "No WLAN on HP Pavilion dv2000"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by mr tobin on 2008-05-04
Just installed ubuntu today and I can't get my wireless to work. In add/remove I cannot add "Windows Wireless Adapter" said it was not compatible with my computer type: i386.

So I downloaded the drivers it needed for my broadcom 802.11b/g.
Drivers being bcm43xx-fwcutter. and I made sure it was for the i386 .

I read elsewhere people who installed the drivers got prompted 
right away to install more driver items, but not the case for me.

---

### Post by Ayuthia on 2008-05-05
Did you get b43-fwcutter from the Ubuntu repositories?  If so, the script that it runs is located found under /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

If not, you can grab the files from:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Download the files into the same directory and then run the following from that directory:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
```If your wireless does not start up immediately, you might need to start it up by typing ifconfig wlan0 up.

Hope that helps.

---

### Post by mr tobin on 2008-05-05
Wicked! thanks. 
my friend suggested I try ndiswrapper? is that a good idea?
or should I try this first?

---

### Post by Ayuthia on 2008-05-05
I don't really have a good answer for you unless you are an owner of a 14e4:4312 rev 02 or 14e4:4311 rev 02 (You can see that by typing lspci -nn at the terminal).  Those two do not work with the b43 driver right now.  

The b43 driver works for most people, but more people that use ndiswrapper are happy with ndiswrapper and will say that it works better.  For me, I have used both and both work the same for me now so I don't really have a favorite.

There are definitely more steps to NDISwrapper now than in previous versions so if you are new to Linux, you might want to try the b43-fwcutter process first.  Then if it does not work for you, switch over to NDISwrapper.  This is the easier way to go than to start with NDISwrapper and switch back to b43.  I say this because you have to back out most things that you installed for NDISwrapper.  However if you start with b43, you don't have to back anything out before you start installing NDISwrapper.

Hope that answers your question.

---

### Post by Paris Heng on 2008-05-05
> **mr tobin said:**
> Wicked! thanks. 
my friend suggested I try ndiswrapper? is that a good idea?
or should I try this first?

yes just compile it.

---

### Post by mr tobin on 2008-05-05
I was trying to run the files with that code you gave me, but I am assuming it has to be in that folder? lib/firmware?

Well I can't move anything to there, says access denied. Is there something I am missing?

Guessing for whatever reasons I don't have permission as an owner?

---

### Post by Ayuthia on 2008-05-05
> **mr tobin said:**
> I was trying to run the files with that code you gave me, but I am assuming it has to be in that folder? lib/firmware?

Well I can't move anything to there, says access denied. Is there something I am missing?

Guessing for whatever reasons I don't have permission as an owner?

The files I said to download should go into your home directory.  From there you can do the following
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
```
The b43-fwcutter application will extract the firmware that it needs and install it into /lib/firmware for you.  /lib/firmware is a protected directory so you cannot do a direct copy into there without root privilege.

If you notice that the command for calling b43-fwcutter does ask for sudo privilege.  Then you will see that it has the -w which will move the firmware to /lib/firmware.  The last portion is the file that it is extracting.

Hope that helps.

---

### Post by mr tobin on 2008-05-05
Yeah, I got online with an ethernet and now issue is resolved. I have my wireless all set up now. 
Thanks alot!

---

