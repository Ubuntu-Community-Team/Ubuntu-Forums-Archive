---
title: "wifi usb adapter DLINK dwl-g132 vs hardy-heron 64 bits"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by jimendeath on 2008-07-26
Hi,

I'm trying to run my usb wifi adapter DLINK DWL-G132 with my new installation of ubunt 8.04 Desktop.

I follow some intructions of anothers post but I got nothing. I download teh last drivers from Dlink page (dwlG132_drivers_130.zip) and the (ndiswrapper-1.53.tar.gz)

I guess that I dont have the right drivers but I dont even know if they exist for the 64 bits edition.

If I cannot, which usb adapter can I use with the hardy-64bits distro ? I would like to solve this as soon as possible because maybe I have a chance to go to the shop and change the usb adapter.

Thanx in advance.

---

### Post by pytheas22 on 2008-07-26
The DWL-G122 version C1 (the version number can be important so pay attention to it) works well for me on 64-bit Hardy.  I didn't need to do anything; I just plug it in and it works.

But instead of spending more money, I'd recommend trying to get your DWL-G132 to work.  I'm not sure which chipset it uses, but if you post the output of the command:
```

lsusb
```

I can try to tell you what you need to do to make it work.  It should not be too difficult, and you probably don't need to use ndiswrapper--you should be able to use native Linux drivers.

Also, when you tried using ndiswrapper before, did you remember to install the 64-bit version of the Windows driver with it?  You can't use a 32-bit Windows driver with ndiswrapper on 64-bit Linux.  This may be why it's not working for you now.

---

### Post by jimendeath on 2008-07-26
Hi pytheas22 !!

First of all thanx for your interest.

the output for the lsusb comand is:
> 
Bus 004 Device 003 ID 2001:3a03  D- Link Corp. [hex]
Bus 004 Device 001 ID 0000:0000 
Bus 002 Device 001 ID 0000:0000
Bus 003 Device 003 ID 12f7:1d00 
Bus 003 Device 001 ID 0000:0000
Bus 001 Device 003 ID 046d:c517  Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001 ID 0000:0000

At that moment I had a cordless keyb/mouse, an usb pendrive and the usb wifi adapter.

I download the ndiswrapper-1.53.tar.gz from 
[[COLOR="Blue"][SIZE="3"]here[/SIZE][/COLOR]]("http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=kent&filename=ndiswrapper-1.53.tar.gz&22684477") 
and the Drivers from [[COLOR="Blue"][SIZE="3"]here[/SIZE][/COLOR]]("ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlG132_drivers_130.zip")

I dont know if there are the 64 bits version but I guess they are not.

Will be wait for your answer.

Thanx

---

### Post by pytheas22 on 2008-07-27
hmmmm, actually it looks like there is no way to make this work on a 64-bit system, simply because D-Link won't 64-bit release drivers.  [Here]("http://support.dlink.com/products/view.asp?productid=DWL-G132#") they have only 32-bit available.  You could contact D-Link and complain, but I doubt it will make a difference, as they say also that:
> 
D-Link Systems, Inc. has issued an End of Life (EOL) Notice for the DWL-G132 and has discontinued it as of Wednesday, August 01, 2007. Technical and RMA support for this product shall continue, with proof of purchase, until Friday, August 01, 2008.

International Customers: Please contact your local D-Link office for product availability in your region.

There may be some other things to try, so don't give up entirely at this point (let me do some more searching tomorrow and see if it turns up anything), but I'm doubtful that it's going to be possible.

On the other hand, the DWL-G132 definitely works with ndiswrapper on a 32-bit kernel, according to [this page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/") (scroll down to entry 16).  So if you want to use a 32-bit system, it would work.  Otherwise the only option is probably going to be to buy a new wireless card (but as I say, maybe there's a solution somewhere).

---

### Post by jimendeath on 2008-09-11
Hi!

the solution I thought is to move the wifi router to my ubuntu pc and the wifipendrive to my wxp pc,... and this way everything woks fine.

 Thanx anyway
:guitar:

---

