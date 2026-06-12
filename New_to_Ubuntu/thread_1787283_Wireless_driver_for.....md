---
title: "Wireless driver for...."
date: 2011-06-20
forum: New to Ubuntu
---

### Post by shaifeyna on 2011-06-20
i have acer aspire n i new in linux.. i install ubuntu 11.04 but my wireless not work?? what can i do?? the easy way

---

### Post by overdrank on 2011-06-20
Hi and welcome, I have moved your post to it's own thread. :)

---

### Post by garvinrick4 on 2011-06-21
> **shaifeyna said:**
> i have acer aspire n i new in linux.. i install ubuntu 11.04 but my wireless not work?? what can i do?? the easy way
Tell us what wifi card you have: Open a terminal (ctrl/alt/t) and copy and paste below
```
sudo lshw -C network
```
wait 10 seconds or so to work and then post results here.

---

### Post by GaryR46953 on 2011-06-29
I tried it , problem is, I'd have to print it out and type it in here. Windows won't read the file saved under Linux.  The disk that came with the wifi card was supposed to install it like it did under windows. It won't.  

The manual install menu asks for input in 2 diff places like " 00:e0:4c:03:9c:9d "   I have no idea where to look for the other number. 

Maybe if somebody could explain the menus a little, we could do this our selves.

---

### Post by wep940 on 2011-06-30
Try:

lspci

and

lsusb

From the lspci, look for any lines that say ethernet or network and only copy those lines back here.  From the lspci that would only be 2 lines max.  Just write them down and put them in a response back here.  Without that, we don't know what wifi chipset it's using, so we can't tell you directly what to do.

---

### Post by grahammechanical on 2011-06-30
You say:

> The disk that came with the wifi card was supposed to install it like it did under windows.

Are you sure? A lot of us will be surprised if the maker of the Wifi card provided Linux drivers as well as Windows drivers.

The core part of the Linux operating system has drivers for all kinds of hardware coded into it because hardware makers do not usually provided drivers on discs for the Linux operating system. But this does not cover every make or design of hardware.

To work toward solving your problem - Can you connect to the router/modem by cable? If you can do this then do it. You may be seeing an icon on the top panel that links to a utility called Additional Drivers. Click on that icon and activate any additional drivers offered to you. This action will download and install any driver being provided by a hardware maker for your machine. This is the way it is usually done. Not by drivers on discs.

You can also get to Additional Drivers by clicking on the Power icon and selecting System Settings. Additional Drivers will show up in the Control Centre panel that appears.

Things are done this way because some of us will refuse to use any computer program or driver where the maker refuses to allow the programming code to be available for anyone to study and modify. Others (like myself) just want the machine to work as it should. So, the Ubuntu people give us all the choice and make it easy to implement our choice.

By the way, do you see a network icon? Have you tried clicking on it. Do you see any wireless networks listed as available? Is your wireless network in the list? What happens if you try to connect to one of these networks?

You need to give us more information if we are to help you. Imagine a friend telephoning you and saying that he is lost. But he does not tell you where he is or what the location looks like or how he got there. How can you give him directions? It is like that for us. 

Regards.

---

### Post by GaryR46953 on 2011-06-30
lshw -c network   returns:

description: wireless interface
id: 1
logical name: wlan0
serial: 00:e0:4c:03:9c:9d
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgh

lspci  and lsusb  returns a list of switches


rt3070_linuxSTA_v2.3.0.1_20100208.tar.bz2   is the driver file on the install disk I believe.
Archive manager shows an error, so it may be unusable. 

using 10.4 , the one packaged with emc2

The terminal isn't bad to work with. Reminds me of DOS only easier.  My first conputer was a TRS-80, so I'm new to linux, not new to computers. :)

And yes, I'm replying on it booted under windows.

---

### Post by GaryR46953 on 2011-06-30
This one:
[http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_1?ie=UTF8&qid=1309446684&sr=8-1](http://www.amazon.com/External-Antenna-Wireless-802-11G-Network/dp/B0037G2BMY/ref=sr_1_1?ie=UTF8&qid=1309446684&sr=8-1)

Some of you may want to go to Ralink's site. Interesting reading.



GaryR46953

---

### Post by wep940 on 2011-06-30
Also, lspci and lsusb should not return "switches" (not sure what you mean by that).  They should each return a list of known PCI and USB devices on your system.  The lspci should show something similar to this for a network device (my wireless is USB so it doesn't show in this list):

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```Any lines returned like that are what we need to see - notice the chipset is listed.

The lsusb should return something similar to this:

```
dave@dave-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dave@dave-desktop:~$
```Here you can see my wilreless adapter and the chipset.

Having the chipset is needed to determine the true driver you need.  Many adapters keep the same model name/number but change chipsets from 1 revision to the next.

Please do the lsusb and lspci again and post back the lines as asked.

BTW - since the driver you seem to have from the disk has STA in it, I'd be willing to bet it's going to be some sort of Broadcom chipset requiring the STA driver.  It would also seem to indicate a RaLink 3070.  It will also probably be source code that will require compiling.  We can HOPEFULLY get you a driver without needing to do all of that.  This is where the outputs I requested come in - they alone can tell us the chipset, and drivers are dependent on the chipset.

---

### Post by wep940 on 2011-06-30
Also, try the following: 

[LIST]
[*]copy the file to your home folder in Ubuntu
[*]via the command line:
[/LIST]
   tar -xvf RT3070_LinuxSTA_V2.3.0.1_20100208.tar.bz2

This will unpack the file and place the resulting files in a RT3070_LinuxSTA_V2.3.0.1_201002008 folder.


[LIST]
[*]now use "Places" to look in that folder.  There should be a readme file of some sort.  Take a look at it and if you have questions post back with those.  If should also be noted that a patch may be needed to make this work
[/LIST]

It will probably be source code which will require compiling.  The normal procedure for this is as follows:

[LIST]
[*]First be sure you have the build-essential package installed. If you have no other way (i.e., a hardwire connection) to get on the net, so that you are unable to run the package manager, the package is available on the LiveCD.
[/LIST]
At the command line:

cd RT3070_LinuxSTA_v2.3.0.1_20102008

./configure

make

sudo make install


That is the normal sequence for compiling from a package source, however please do read the readme file to see if there are any alterations to those steps.

---

### Post by DannStarr on 2011-06-30
Hey OP, I've just managed to overcome the exact same problem, albeit on a different laptop, and we seem to be using slightly different wifi chips.

Here is a link to the procedure that helped me: [http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010](http://www.6by9.net/b/2011/04/25/hp-dm1z-laptop-running-ubuntu-1010)

The info in the link is directly for my laptop, however it refers to 32 bit ubuntu 10.10, where as I am running ubuntu 11.4 64 bit.

What that means for both you and me, is that the procedure will be exactly the same, my only difference was that I needed to patch an additional file (owing the the 64 bit) - your only difference will be the driver that you download, as you will need to get one specific for your chip.... are you running a 32 or 64 bit system? as that will effect which one you download too.

Once you find the right driver, the process in the link I gave will get it all installed and ready to go for you

---

### Post by wep940 on 2011-07-01
And hence why we need the outputs I have requested....

---

