---
title: "Should I give up on ubuntu? Wireless download too slow."
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by eperrone on 2008-05-24
Hey folks,

I had posted a few questions about my wireless connection before and so far I have been unable to get the connection working at a reasonable speed.  My general question is is it likely that new updates will help me eventually? Or should I just throw in the towel...

Basically my problem is that my wireless connection does connect but the download speed is absolutely horrible.  The upload speed seems to be ok and on par for this machine when I boot it with Windows. But my download speed is slower than upload.

Anyway turns out my machine has the Dell 1505 Wireless Draft 802.11n card with broadcom 4328 chip (rev 03).  I have the it working with what I think is the ndiswrapper (since I am using the GUI - Windows Wireless Driver applet).  

I was poking around a bit on and reading about fwcutter and it seems that this might be a solution but from what I can see this chip is not yet supported. 

What do you folks think... is it likely to ever be supported or is there anyone out there who has this chip working?  

Thanks
Hoping to get this going someday.

---

### Post by pytheas22 on 2008-05-24
Yeah, it says at [http://linuxwireless.org/en/users/Drivers/b43#supported](http://linuxwireless.org/en/users/Drivers/b43#supported) that your model is not supported by the b43 driver (the native Linux driver for Broadcom chipsets, which involve fwcutter).  Unfortunately Broadcom cards are really tough to get working because Broadcom is really fascist about cooperating with Linux, so it's only possible to write drivers very tediously via reverse-engineering.  Before giving up on Ubuntu, though, you could try asking the developers of the b43 driver what the status of your chipset is; they should know if/when it will be supported.

Also, have you tried using different versions of the Windows driver via ndiswrapper?  It could be that the poor performance you're experiencing would go away if you tried running it under a different Windows driver.

---

### Post by nzadLithium on 2008-05-25
I know this isnt very helpful but if you wanted to you could go by another wireless network card that would work with ubuntu. This is the one i have [http://etccomputers.co.nz/shop/main/product.asp?pid=160](http://etccomputers.co.nz/shop/main/product.asp?pid=160) and it works fine. I don't have any performance issues with it. Its about $40NZD. Which is about $30 USD.
Just check that it will work with your router.

---

### Post by eperrone on 2008-05-25
Thanks folks,

I'll ask the b43 folks about it to see what/when a native driver might be available.  I wonder if I could find a nearlier driver from dell?  I have the latest driver.

I could look into to a new usb wireless dongle or something, (this is a laptop). I would prefer to find someway to get the built in card working of course.

It seems like eventually these things come along thanks. 

Anyone else have this problem with a Dell Latitude laptop?

---

### Post by pytheas22 on 2008-05-25
> I wonder if I could find a nearlier driver from dell? I have the latest driver.

Yeah, you might have better luck with an earlier driver.  It's been my experience that ndiswrapper is more reliable with older Windows drivers, I guess because the developers have spent more time testing them.

---

### Post by eperrone on 2008-05-25
Any idea where you can earlier drivers form dell?

---

### Post by pytheas22 on 2008-05-25
> Any idea where you can earlier drivers form dell?

I don't know which version you're using, but from this [thread]("http://ubuntuforums.org/showthread.php?t=297092") is this link: [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE) .  You should be able to just gunzip the .exe to get at the you need, or if you want, run the installer in wine and figure out where it puts them.  The Dell CD that came with your computer should also have some version of the wireless drivers on it, I imagine.  Otherwise there must be different versions of it at random places around the Internet.

Also, did you try following the how-to that I linked to above?  It's for the kind of card you have, and most of the commenters indicated having success with it.  Compiling ndiswrapper from source, as that tutorial describes, might do the trick for you too.

---

### Post by chili555 on 2008-05-25
> You should be able to just gunzip the .exe to get at the you need, or if you want, run the installer in wine and figure out where it puts them.When you download this, you should put it in it's own folder which you might call, for example, 'dell.' Then do:```
cd dell
unzip  R151517.EXE
```You will see all kinds of things are inflated, which is why you put it in its own folder. You will see, in a folder called 'Driver' a file called bcmwl5.sys, which is probably what you need.

---

### Post by eperrone on 2008-05-25
Hey guys thanks very much for the help.  Here is the story well it turns out that that it is WPA causing all the problems.  Just for fun I set my wireless AP to use no security and then only WEP security and in either case the system works great!

It is only when I enable WPA does the system slow to a crawl.  Anyideas what that might mean?

I am going to try the earlier driver version to see if that helps at all.

Anything else to hel with WPA?  It seems like the WPA just kills the download speed only.  Upload is more or less the same.

Weird.

---

### Post by eperrone on 2008-05-25
Well I tried the earlier driver and it was worse than the latest one I had.  I could not get it to connect to the WPA network at all.

I have reverted to the Latest driver and now I am connecting very speedily through WEP.  However this will not help me much when I get to the office and in other places where WPA is prevalent.

I guess I am still hoping for the magic WPA bullet.

---

### Post by bsell on 2008-05-25
@epperone

Have you tried any of the solutions on the [help.ubuntu.com site for wireless workarounds ]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-9192b3c227e128044894727c4b85a57abee8a0c9")for your Broadcom chip? While the site says Feisty, Hardy workarounds are included. The BCM4328 (rev 03) instructions on downloading and extracting the driver are in step 2d.

---

### Post by eperrone on 2008-05-26
Thanks I just tried these steps and it actually got worse.  I could not connect to the WPA network at all.  Howver I could connect to the WEP network.

Maybe they need to be done on a clean install.  I'll try that if I run out options.

The driver that the author mentions is not from dell would that matter?  I have drivers from dell for this hardware should I try those steps inserting the dell drivers?

How do these steps compare to adding the driver vis the ndisgtk applet?

Sorry for all the questions completely new to linux here.

---

### Post by eperrone on 2008-05-26
Hey all,

Today I did upgrade to Kernel.... 2.6.24.17 and all is fine now my WPA works great and very speedy!

For the record:

My problem was that I could connect to WPA access points but download was very slow.  I upgraded to the .17 Kernel from .16 and all is now well.


I have Broadcom 4328 1505 Draft 802.11n wireless adapter on a Dell Latitude D830.

I used the latest Dell drivers with ndiswrapper I did not do anything fancy at the command line I just installed using the ndiswrapper gui tool available in Hardy.

The dell Drivers were labeled: R174291 Driver was version:

4.170.25.12 - A17

Thanks everyone for their help and suggestions!!!
Eric

---

