---
title: "AddOn ADD-GWU180 and Ubuntu 6.06 won't work together"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by Paulplex on 2007-01-07
Hi all: new to this forum and also new to Linux - I've tried it before using Knoppix bootable CD's but upon the recommendation of a friend, I've installed it and plan to be Windows free within six months :) 

However, I'm having a few problems and thought I'd test the waters on this forum to see if anyone can help.

I've downloaded 6.06 LTS and installed it quite happily on a 3GHz P4 computer: all works well and all hardware is detected correctly - except my wireless card.

According to the WifiDocs Ubuntu page, my card is supported: an AddOn ADD-GWU180:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

However, despite this assurance, my wireless card is not listed with other network adapters inside my computer and thus I can't configure it.

It appears that there are more than one release of the ADD-GWU180 card however: I have revision 3 and that I presume to the be the problem.

[IMG]http://www.addon-tech.com/image/GWU180.jpg[/IMG]
 - This one works on Ubuntu from the box

[IMG]http://www.addon-tech.com/image/GWU180v3.jpg[/IMG]
 - This one doesn't :-k 

There is a Linux driver for it, available from [http://www.addon-tech.com/wldl.html#]("http://www.addon-tech.com/wldl.html#") - however, I really am a complete noob with Linux and would really appriciate some help from somebody who understands the readme more than me ](*,)

Ta for your help, whoever my knight in shining armour will be :-D

---

### Post by hal10000 on 2007-01-07
As a first hint you may check if your card is recognized by the system:
open a terminal window and type [COLOR="Red"]lsusb[/COLOR]
This lists all your usb devices.
Post the output of the command.

---

### Post by Paulplex on 2007-01-07
> **hal10000 said:**
> As a first hint you may check if your card is recognized by the system:
open a terminal window and type [COLOR="Red"]lsusb[/COLOR]
This lists all your usb devices.
Post the output of the command.

Hiya: thanks for your reply.  Currently there is only one USB device connected which is the wireless USB adapter: looking through forums, I'd already noted the [COLOR="Red"]lsusb[/COLOR] command and that does show that a device is connected.

Here is the result of the command:

[INDENT][FONT="Fixedsys"]Bus 005 Device 002: ID 07b8:b21d D-Link Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000[/FONT][/INDENT]

...so it appears that *something* is connected but apparently not the USB adapter I thought.  I suppose however that many many vendors use each others hardware, simply badging them as a different make and model.

...so how do I install a driver so that Ubuntu recognises what I've got connected?

---

### Post by hal10000 on 2007-01-07
Hi,
in the meantime I looked through the links in your post and noticed that there are probably two methods to get your card work. I don't have such a card and thus can not verify the steps I suggest.
1. The driver from the ADDON site is a packed rar file, so you first have to unpack it and then compile the driver as described in the README file.
But notice that in the README under "Build instructions" step 1 there is mentioned the tar command, but you have no tar.gz file but a rar file; so you have to use here the [COLOR="Red"]unrar[/COLOR] command:
```
cp GWU180v3LinuxDriver.rar /tmp
cd /tmp
unrar x GWU180v3LinuxDriver.rar

```
After uncompressing the file, cd into the new directory and follow the steps in the README. It seems that there are a lot of things to be configured, so I suggest you first try the second method, which (if it works) is much easier to get it work:

2. In the first link you mentioned above we can see that the native linux driver for the card is called zd1211. So first try if this kernel module is already loaded:
```

lsmod | grep zd1211

```
If so, and if it not work when configuring your network with network admin, then it seems not to work and you have to try the first method (with the rar file).

If the module is not listed when performing the lsmod command, then try to load it first:
```
 sudo modprobe zd1211 
```
verify if it is really loaded by using [COLOR="Red"]lsmod | grep zd1211[/COLOR] again.
When this is done, then you can configure your network with your preferred config tool. I hope this works, otherwise try the rar file.

Good luck

---

### Post by tturrisi on 2007-01-07
The site has a linux driver for the version 3 usb adapter which has a Ralink chipset.  If your device is a version 3 the driver should work.  The version should be printed on the device.

---

### Post by Paulplex on 2007-01-08
> **tturrisi said:**
> The site has a linux driver for the version 3 usb adapter which has a Ralink chipset.  If your device is a version 3 the driver should work.  The version should be printed on the device.

Thanks for your help fellas: I'll give it a try later tonight.

The revision of the USB adapter is not printed on the box incidently - I have ascertained that it is version 3 from the design of the box and adapter itself, based on the AddOn website.

I'll give Hal's suggestions a try tonight though - if I have any problems, I know where to ask!

Ta again :D

---

