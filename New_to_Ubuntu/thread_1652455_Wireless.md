---
title: "Wireless"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by wtf? on 2010-12-24
Hey all.
Just replaced my old laptop and I thought it would be cool to install a Linux program on the old one since I'd love a change from windows.  So I finally figured out how to download and burn a disc, replaced my os with Ubuntu 10.10 and eureka!  No wireless adapter detected, says firmware not installed. (Is that like software?)  Now I am no fan of Windows but the wlan has worked problem free for 4 years on this Compaq Presario now the first thing I find with Linux is I have no internet.  Pretty discouraging, read lots of forums and googled everything I could think of and it seems like since I'm not a rocket scientist (or a geek) I am screwed.  Don't understand anything I read.  Any easy answer???  Any help would be very much appreciated.
Thanx.

---

### Post by wtf? on 2010-12-24
BTW, Merry Christmas!:KS

---

### Post by hpadrick on 2010-12-24
Hello wtf? and welcome to the world of linux were creators of hardware do not choose to share their software. Some wireless cards require firmware that needs to be installed manually do to licensing issues or what have you.

In the newer Ubuntu these are usual picked up under Menu --> Administration --> Hardware Drivers 

Check there first for any firmware or drivers that do not have a green dot beside them. You can hightlight the one you need and click activate.

Let us know how that goes before digging deeper.

Merry X-Mas!

---

### Post by sandyd on 2010-12-24
> **wtf? said:**
> Hey all.
Just replaced my old laptop and I thought it would be cool to install a Linux program on the old one since I'd love a change from windows.  So I finally figured out how to download and burn a disc, replaced my os with Ubuntu 10.10 and eureka!  No wireless adapter detected, says firmware not installed. (Is that like software?)  Now I am no fan of Windows but the wlan has worked problem free for 4 years on this Compaq Presario now the first thing I find with Linux is I have no internet.  Pretty discouraging, read lots of forums and googled everything I could think of and it seems like since I'm not a rocket scientist (or a geek) I am screwed.  Don't understand anything I read.  Any easy answer???  Any help would be very much appreciated.
Thanx.
Go to applications -> accessories -> terminal
post output of
```

lspci
```

---

### Post by _0R10N on 2010-12-25
> **sandyd said:**
> Go to applications -> accessories -> terminal
post output of
```

lspci
```


You can also post the output of

```
lshw -C network
```
It will complain, saying that you should run the command as a super user, ignore it.

Kind regards!

---

### Post by wtf? on 2010-12-25
> **sandyd said:**
> Go to applications -> accessories -> terminal
post output of
```

lspci
```
I assume you meant type that in and hit enter?  If so, there's a whole page of info there that would take a day to type.  Anything particular that's relevant?
Thanks

---

### Post by wtf? on 2010-12-25
> **hpadrick said:**
> Hello wtf? and welcome to the world of linux were creators of hardware do not choose to share their software. Some wireless cards require firmware that needs to be installed manually do to licensing issues or what have you.

In the newer Ubuntu these are usual picked up under Menu --> Administration --> Hardware Drivers 

Check there first for any firmware or drivers that do not have a green dot beside them. You can hightlight the one you need and click activate.

Let us know how that goes before digging deeper.

Merry X-Mas!
Finally found a file called "administration" in "system" but it contains no file called "hardware drivers."  There is a file called "Additional Drivers" but that just tells me I am not connected to the internet and no drivers are installed.  Just about ready to give up.
Good night and thanks.

---

### Post by TNT1 on 2010-12-25
Don't look for a file called administration, go to the menu, then click on system > administration > hardware drivers


.

---

### Post by 3rdalbum on 2010-12-25
Don't give up yet, this could be really really easy.

First, find an Ethernet cable and plug your computer straight into your modem/router. You should get a wired internet connection automatically.

Next, go to Applications > Ubuntu Software Center, then Edit and "Software Sources". If asked, type your password.

Make sure that the first four checkboxes are ticked in this window, then click Close. If you are asked if you want to reload the package list, then yes, do it - and then go straight to the Additional Drivers program and you should hopefully be offered the firmware to download.

If you're not asked to reload the package list, then either open a terminal and type:

```
sudo apt-get update
```

or go to System > Administration > Synaptic Package Manager and click the Reload button. Then close Synaptic. Now go to the Additional Drivers program and you'll be offered some firmware to download.

After a restart, you'll be able to pick up wireless networks and connect to them.

With Ubuntu, probably around 50% of wireless cards work "out-of-the-box". When they have open-source firmware available, or firmware included inside the device, and open-source drivers, support can be included on the CD. For non-open-source drivers or firmware, for legal reasons these cannot be included on the CD and must be downloaded separately.

If you really can't get this wifi device working (unusual, but possible I guess) then consider purchasing a card that is known to work out-of-the-box with Ubuntu. Won't cost much, but could save you some hassles, and would save you the cost of upgrading Windows every couple of years.

---

### Post by IndyGunFreak on 2010-12-25
> **wtf? said:**
> Finally found a file called "administration" in "system" but it contains no file called "hardware drivers."  There is a file called "Additional Drivers" but that just tells me I am not connected to the internet and no drivers are installed.  Just about ready to give up.
Good night and thanks.

Look in lspci output, and find your wireless device and tell us what it says.  You would think since you're having wireless problems, this would be fairly obvious when you were given that command.

Also, your wireless device didn't "just work" on Windows either.  When they built your laptop, they installed the driver for you... If you had installed a bare MS OS on the laptop, you would have had to search out a driver for it.

Honestly, if you're ready to give up that quickly.. You're probably better off staying w/ a Microsoft OS.  Linux is not Windows, and it will be a learning process... so if you're not prepared to learn how to use a totally new OS.. don't frustrate yourself.  Reinstall MS, and use what you know.

---

### Post by wtf? on 2010-12-25
> **3rdalbum said:**
> Don't give up yet, this could be really really easy.

First, find an Ethernet cable and plug your computer straight into your modem/router. You should get a wired internet connection automatically.

Next, go to Applications > Ubuntu Software Center, then Edit and "Software Sources". If asked, type your password.

Make sure that the first four checkboxes are ticked in this window, then click Close. If you are asked if you want to reload the package list, then yes, do it - and then go straight to the Additional Drivers program and you should hopefully be offered the firmware to download.

If you're not asked to reload the package list, then either open a terminal and type:

```
sudo apt-get update
```

or go to System > Administration > Synaptic Package Manager and click the Reload button. Then close Synaptic. Now go to the Additional Drivers program and you'll be offered some firmware to download.

After a restart, you'll be able to pick up wireless networks and connect to them.

With Ubuntu, probably around 50% of wireless cards work "out-of-the-box". When they have open-source firmware available, or firmware included inside the device, and open-source drivers, support can be included on the CD. For non-open-source drivers or firmware, for legal reasons these cannot be included on the CD and must be downloaded separately.

If you really can't get this wifi device working (unusual, but possible I guess) then consider purchasing a card that is known to work out-of-the-box with Ubuntu. Won't cost much, but could save you some hassles, and would save you the cost of upgrading Windows every couple of years.
Got it!  Didn't go exactly like you advised but once I was connected was able to do a search for wireless drivers, downloaded and installed them, and I am now sending this message via wireless and Ubuntu. 
Thanks to all for the help, much appreciated!  Now I can really see what this is all about, so far it looks good.
Hope everybody is having a great Christmas.  Cheers!

---

### Post by wep940 on 2010-12-25
For others reading this thread, and for some of the posters in this thread, remember that this is a laptop and  many laptops have their built-in wireless actually connected to internal USB, so it wouldn't show in lspci.
 
The best request is to ask for both  lsusb and lspci, plus the lshw -C network, ifconfig and iwconfig.

---

