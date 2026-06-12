---
title: "dlink usb wlan adapter detected but no connection"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by kosiew on 2005-10-22
I just intalled ubuntu 5.10.

Ethernet LAN working fine but it does not detect any WLAN.

I thought it was because it did not detect the DWL-G122 usb wireless lan adapter.

lsusb

I can see this entry :
Bus 001 DEvice 012: ID ....... D-Link Corp. (hex) 
....<I have only 1 D-Link device, so this must be it. Confirmed further by pulling it out. lsusb does not list it anymore.>

But the adapter does not light up.

When I System->Administration->Networking, there is also no Wirelss Network.
There are:
Ethernet connection
Modem connection


Then I resorted to ndiswrapper to 'install' the Windows XP driver although I did not think it necessary because ubuntu already detected the device.

After installing:

ndiswrapper -l
.. netrtusb   driver present, hardware present

but adapter still will not light and there is still no wireless network.

  iwconfig

lo  no wireless extensions
eth0 no wireless extensions
sit0 no wirelss extensions


The adapter works fine when I dual boot to Windows XP.

From what I have picked up in this forum, there is often no problem or the problem could be resolved with ndiswrapper.

I am a 2 day old ubuntu user (who just survived a GRUB Error 18) and would appreciate some guidance and detailed instructions on how to troubleshoot this ?

Thanks in advance

---

### Post by ras on 2006-01-13
Did you ever figure this out?  I'm in the exact same situation.

---

### Post by nijinsky on 2006-01-13
[QUOTE=ras]Did you ever figure this out?  I'm in the exact same situation.[/QUOTE]

Try this. I sometimes dont get the wlan0 in network manager.

Open a terminal and type

sudo ifup wlan0


this may allow recognition of the router and you will then see the wlan already active in network manager.

cheers
bob

---

### Post by ironwoodca on 2006-03-20
I have a similar problem except that my DWL-122 lights up and the device manager sees it. BUT, I don't see it in the Network connections. I tried the sudo command and it came back  'ignoring unknown interface wlan0"

I hope someone can help us.

---

### Post by lingon on 2006-03-24
I have that problem too. Very anoying.

---

### Post by trorion on 2006-03-31
[QUOTE=lingon]I have that problem too. Very anoying.[/QUOTE]
The dwl-g122 rev. B card is not supported in Breezy but it is supported in Dapper.  The driver for this card is the rt2570 (rt2500usb) which can be found at: [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")

If you install this driver you can get your card working.  There is a howto [on this thread]("http://www.ubuntuforums.org/showthread.php?t=106846&highlight=2500") on installation.

This card must be configured for secure connections manually using iwconfig.  It can be easily configured for open (non-secure) connections.  Be careful, if you try to set up secure connections I've had issues with it locking up my system.  No I haven't yet figured out how to do the WPA on this card but I understand it can be done.

---

### Post by Mr_Welfare on 2006-04-14
[QUOTE=trorion]The dwl-g122 rev. B card is not supported in Breezy but it is supported in Dapper.[/QUOTE]

What is the **rev. B** card? How do you tell what card you have? I am looking at the box for my D-Link DWL-G122 right now and all it says on the side of the box is "DWL-G122"

Is the normal G122 card (which I'm assuming is what I have) supported by Breezy?

So far, I haven't gotten anything to work yet. The adapter light comes on, but whenever I try to go go Google.com on Mozilla, I get a message saying that the ite couldn't be found.

I also have another similar question that can be found [here]("http://www.ubuntuforums.org/showthread.php?p=921093")

---

