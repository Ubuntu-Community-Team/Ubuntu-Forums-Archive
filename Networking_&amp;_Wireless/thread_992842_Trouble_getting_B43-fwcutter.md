---
title: "Trouble getting B43-fwcutter"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by jstrowe on 2008-11-25
I have 8.10 installed on my laptop. It does not want to connect with the internal Broadcom B4306 based wireless adapter. I got a Netgear WG111 V2 USB adapter that was listed as working in the compatibility list. Indeed, it worked as soon as I plugged it in! However, I want to get the internal wireless working so that I don't have a big USB dongle poking out the side where it can get broken.

Here's where the problem arises. When I try to install fwcutter, it times out accessing mirror2.openwrt.org. I can access openwrt.org or any other site that I try, but just not mirror2.openwrt.org. I have tried Firefox, apt-get and the other package managers and none of them can access mirror2.openwrt.org. Is there any way that I can get this package from another (non-Ubuntu) machine and put it onto a removable drive so that I can get it onto my Ubuntu machine? Alternately, is there some other site that I can direct Ubuntu to use to fetch this driver?

Conversely, can anyone tell my why I would only be having problems with this one site? When I reboot my machine in XP, I can access it with no problems so there is nothing in my network that is blocking access.

Thanks,
John

---

### Post by kevdog on 2008-11-25
Are you trying to fetch the wl_apsta.o driver specifically?

Obviously it looks like you have read this page where to obtain the driver:
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

However I just accessed [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) without a problem.

The other thing you could do would be to download this file with another computer, and then bring the tar.bz2 file over on a USB stick or something similar.

---

### Post by Ayuthia on 2008-11-25
Here are some instructions on how to get this to work without a working connection in Ubuntu.  Of course, you will need to download the files from another computer with a working internet connection.

[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

@kevdog - I do plan on creating some kind of wiki for this in the community section.  I just need to quit procrastinating!

---

### Post by kevdog on 2008-11-25
Thanks for those instructions -- those were really thorough.  My only problem is with the actual firmware itself.  If you look at the b43 website (which obviously you have done), there are different firmware packages depending on kernel version and whether you need the b43, b43legacy, or bcm43xx (which is no longer recommended).  The specific b43 version is also kernel dependent. 

After downloading a particular b43 package, I noticed there are a lot of .o files with the Driver section.  The instructions stated to install the wl_apsta.o file, however your instructions state to install the wl_apsta_mimo.o file.  Why are you recommending this wl_apsta variant?

---

### Post by Ayuthia on 2008-11-25
> **kevdog said:**
> Thanks for those instructions -- those were really thorough.  My only problem is with the actual firmware itself.  If you look at the b43 website (which obviously you have done), there are different firmware packages depending on kernel version and whether you need the b43, b43legacy, or bcm43xx (which is no longer recommended).  The specific b43 version is also kernel dependent. 

After downloading a particular b43 package, I noticed there are a lot of .o files with the Driver section.  The instructions stated to install the wl_apsta.o file, however your instructions state to install the wl_apsta_mimo.o file.  Why are you recommending this wl_apsta variant?

I think that you might have looked at the 2.6.24 version instead of the 2.6.25 and newer version.  The 2.6.25+ version does have the  wl_apsta_mimo.o file listed at the linuxwireless.org site.  

However, I usually base the information based on /usr/share/b43-fwcutter/install_bcm43xx-firmware.sh (that comes with the b43-fwcutter package).

---

### Post by kevdog on 2008-11-25
Oh -- very nice catch -- you were right.  Good spot!!

---

### Post by jstrowe on 2008-11-25
> **kevdog said:**
> Are you trying to fetch the wl_apsta.o driver specifically?

Obviously it looks like you have read this page where to obtain the driver:
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

However I just accessed [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) without a problem.

The other thing you could do would be to download this file with another computer, and then bring the tar.bz2 file over on a USB stick or something similar.

That's exactly my problem. I can access mirror2.openwrt.org with every other computer including the machine that has Ubuntu on it, but only when that machine is running XP.

Ubuntu + my machine = no mirror2.openwrt.org!

However, I was trying to use various package managers to do the downloading, and all of them refer to that site which I cannot reach. The instructions to get wl_apsta.o directly and install it off-line look to be just what I need.

Kevdog and Ayuthia, thank you. I'll try it tonight.

John

---

### Post by jstrowe on 2008-11-25
> **kevdog said:**
> Are you trying to fetch the wl_apsta.o driver specifically?

Obviously it looks like you have read this page where to obtain the driver:
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

However I just accessed [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) without a problem.

The other thing you could do would be to download this file with another computer, and then bring the tar.bz2 file over on a USB stick or something similar.

Kevdog,

I got the files on another machine and copied them to the Ubuntu machine. I followed the instructions the that you quoted for the legacy B43. One thing that was missing was that I needed to run the hardware drivers app to activate the driver. Once I did that, my on-board wireless adapter came on-line and connected right up to my network!

Many thanks!

John

---

### Post by kevdog on 2008-11-25
Can you be more specific with your last statment?  You mean you had to bring the device up or online?

---

### Post by jstrowe on 2008-11-26
> **kevdog said:**
> Can you be more specific with your last statment?  You mean you had to bring the device up or online?

I downloaded b43-fwcutter-011.tar.bz2 and wl_apsta-3.130.20.0.o to another machine and put them on a USB drive. Then I copied these files to my Ubuntu machine. I ran the following:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

Then I ran:
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
sudo ./b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o

At this point, there was no obvious change to the system. It saw my wireless adapter, but it did not see my wlan. I ran the hardware drivers app and activated the B43 driver which was shown as being deactivated. As soon as the driver finished activating, the network icon started to swirl, indicating that it was trying to negotiate a connection and a couple of seconds later, it showed a signal strength and I was connected.

Does this answer what you asked?

John

---

### Post by Ayuthia on 2008-11-26
I have not taken a look at the code for Hardware Drivers (jockey I think) in a while, but it sounds like the activation might have just unloaded and reloaded the module.  I could be wrong though.

---

### Post by jstrowe on 2008-11-26
> **Ayuthia said:**
> I have not taken a look at the code for Hardware Drivers (jockey I think) in a while, but it sounds like the activation might have just unloaded and reloaded the module.  I could be wrong though.

I wouldn't be surprised. I had previously gotten fwcutter on my machine, but without being able to get wl_apsta-3.130.20.0.o, it couldn't work fully. Once I had all the files, it worked like a charm.

John

---

### Post by Zeroedout on 2009-02-01
Hi, I seem to be having a similar problem. Activating it with the restricted driver manager did not work so I built fw cutter as per the instructions and copied the firmware to /lib/firmware/ yet it still won't find my network. iwlist eth1 scan says nothing found. Any idea what else I can do?

---

### Post by Ayuthia on 2009-02-01
> **Zeroedout said:**
> Hi, I seem to be having a similar problem. Activating it with the restricted driver manager did not work so I built fw cutter as per the instructions and copied the firmware to /lib/firmware/ yet it still won't find my network. iwlist eth1 scan says nothing found. Any idea what else I can do?

Can you post the results of:
```
lspci -nn
lshw -C network
```
It will help us identify which chipset you are using along with giving us some information about what you wireless card is trying to use.

---

