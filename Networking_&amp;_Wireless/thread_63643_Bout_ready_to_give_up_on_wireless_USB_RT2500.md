---
title: "Bout ready to give up on wireless USB RT2500"
date: 2005-09-08
forum: Networking &amp; Wireless
---

### Post by Belistner on 2005-09-08
Hi,
I just installed Ubuntu today and have spent at least 6 hours trying to get my wireless USB adapter to work with no luck.

The adapter is a Belkin F5D7050 USB.

I have tried everything. ](*,)  Firstly i tried ndiswrapper and the native windows driver. This allowed the adapter to be recognised but I kept getting "OPERATION NOT SUPPORTED" when i tried to set anything via iwconfig. The GUI wireless managed to set the essid but seemed to ignore the key.

So i completely removed that and tried native drivers form serialmonkey and from ralink themselves. In both cases after instering the module nothing happens and the adapter is just not listed (in the list given by iwconfig).

I am a linux newbie and would appreciate any help. The driver the adapter uses under windows is RA2500usb.sys if thats any help.

Has anyone got ANY ideas?

Thanks.
Lewis

---

### Post by Steve1961 on 2005-09-09
I've had a look at the ndiswrapper sourceforge page and you should be able to get this card up and running.  If it has the ralink chipset I'm surprised the native rt2500 drivers didn't work.  You card is listed here as one that should work with this driver.  There's good how to on the wiki for this at [https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo).

Failing that, you need to extract the .inf and .sys files from your driver CD.  Put them in the same directory but you only need to ndiswrapper the .inf file.  If you have problems with the version of ndiswrapper supplied by ubuntu download and complie version 1.2.  It often works when the earlier version doesn't.

---

### Post by Belistner on 2005-09-09
Hey thank you for the reply

Yes I have read countless posts bout people getting this card to work but as of yet I have been unable to replicate the results.

I would prefer to use the native linux drivers. I have installed the rt2570 drivers which are the only ones that recognise my adapter. However when using Iwconfig to set ANY option they all return as below:

lewis@BlueAngel:~$ iwconfig rausb0 channel 11
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device rausb0 ; Operation not permitted.

lewis@BlueAngel:~$ iwconfig rausb0 key baa2dc2429141db0af7bec9fbf
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device rausb0 ; Operation not permitted.

Whats worse it that ONCE i was running these commands and it SEEMED to be working (no erorrs). Now again all I can get is this.

EXACTLY the same thing happens if I use ndiswrapper.

What the hell is it!? :-)

Thanks.
Lewis

---

### Post by Belistner on 2005-09-09
Oh my GOD.

You don't have to be root do you for iwconfig to work? It seems to work when I'm root?

I seriously spent hours on this. Thats not SERIOUSLY it is it?

---

### Post by Steve1961 on 2005-09-09
Looks like you might have found the answer.  I always sudo when I run these commands.

---

### Post by Belistner on 2005-09-09
yeh she's up and running. Still a little shakey though. When i change certian options sometimes the system locks up so just have to be careful.

Thank you for the help! 

One more question if I may? What file does linux define the DNS server in. /etc/network/interfaces defines the interfaces and their various options but does not seem to include the DNS I provided in System->Administration->Networking.

Lewis

---

### Post by Steve1961 on 2005-09-09
Sorry, I don't have the answer to this as I've never needed to configure it - it just appeared when the card obtained its IP address from my router.

As for being a little shaky after you change settings, I've found that as well with wireless cards.  After making changes I've always found the best course of action is to reboot.  That seems to stabilise everything.

---

