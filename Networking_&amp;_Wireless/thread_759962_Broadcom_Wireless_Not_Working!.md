---
title: "Broadcom Wireless Not Working!"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Tibco on 2008-04-19
Help! Im a total noob at ubuntu and i would like some help. I installed ubuntu 8.04 on my hp dv6000 and everything seemed fine during installation. After logging in the internet was not working...so i went back to windows and looked at what to do...it seems that broadcom is really hard to set up...if anyone could give me instructions on what to do,  that would be awsome.

 PS: i searched the forums and googled several things, but it seems that this person got it to work: [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)
but some of the commands are cut off so...im not sure what to do. Thanks for the help!

---

### Post by leo_rockway on 2008-04-19
What's the output of the following command?

```
lspci | grep Broadcom
```

I made a post about the Broadcom wireless cards in my blog [0]. My card is model "(0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01))". Depending on the model of your wireless card this might work for you.

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o
```

This may create a problem with the name of the device (it may not happen to you, since it is a fresh install). If that happens let me know or take a look at my blog.

[0] [http://leorockway.wordpress.com/2008/03/23/exit-gutsy-enter-hardy-ii/](http://leorockway.wordpress.com/2008/03/23/exit-gutsy-enter-hardy-ii/)

---

### Post by Tibco on 2008-04-21
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
 
That link got it working! I had a Hp dv6646us, with a Broadcom wireless chip, so if anyone has something similar, this is the link to follow, easy step by step instructions, made it work fast. Also, it says that its for Feisty 7.04, but it also worked for me in Hardy 8.04. Thanks anyway for the help!

---

### Post by leo_rockway on 2008-04-21
I'm glad you have your wireless card working now. :-)

---

### Post by jasonpeinko on 2008-04-21
I have been having the same problem
i have tried several things most recently the fwcutter.
I have tried hdiswrapper which is what i had on fiesty and it did not work. 

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
this post says it should apear under restricted but it does not.

lspci
```

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

above method did not work either
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by leo_rockway on 2008-04-21
@jasonpeinko: depending on which version of Ubuntu you're using the driver is different. With hardy the bcm43xx driver was switched for b43 which apparently works better. If you're still on Gutsy (or something even older) you may want to wait until Hardy and see if b43 solves your problem.

---

### Post by jasonpeinko on 2008-04-21
i have hardy, i install b43_fwcutter, tried 
and i followed this guide
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

---

### Post by davsha77 on 2008-04-21
I am completely new to Ubuntu (and linux for that matter).

I am running Feisty Fawn 7.04

my lspci says:

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I am not sure how I have rev 03 since the computer is over 3 years old and the link ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)) has rev 02 as the latest.

I can see the card in the Device Manager, but I can't turn on the wireless antenna.

---

### Post by jasonpeinko on 2008-04-21
still dont have it working, can someone please help. i have tried every method i found.

---

### Post by jasonpeinko on 2008-04-22
anyone? i really need this working.

---

### Post by lswest on 2008-04-22
Sorry to say, you've got the same card as i do, and with a fully up-to-date Hardy, the kernel has lost support for that card, as the patch broke compatibility with other chipsets, which was deemed too steep a price.  Only way to get it working now is to ndiswrapper a bcmwl5 driver.

---

### Post by MetalMusicAddict on 2008-04-22
This is just my opinion but I would really say anyone with a cursed Broadcom minipci card buy a [IPW 220 for $20 on Ebay]("http://search.ebay.com/intel-2200_W0QQcatrefZC6QQdfspZ32QQfposZQ5AIPQ2fPostalQQfromZR40QQfsooZ2QQfsopZ32QQftrtZ1QQftrvZ1QQsabfmtsZ1QQsacatZQ2d1QQsadisZ200QQsaobfmtsZinsifQQsargnZQ2d1QQsaslcZ2QQsbrftogZ1QQsofocusZbs"). Works OTB. No probs.

I've bought 3 of them from the 1st reseller. Happiest HW purchase I've had in years.

---

### Post by jstueve on 2008-04-22
yeah,I solved my broadcom card problems by swapping the bcm with an intel pro in a windows lappy... the windows drivers works fine there, and the ubunutu likes the ipw...  even steven.

---

### Post by jasonpeinko on 2008-04-22
thats pretty lame, how hard is it to swap wireless inside a laptop? also ndiswrapper never worked.

---

### Post by jasonpeinko on 2008-04-22
what i dont get is why the patch would not be optional. It seems to me that there are quite a few people with these chips.

---

### Post by zetsumei on 2008-04-23
I did a simple sudo apt-get install ndisgtk and it installed my broadcom wifi like that.

---

### Post by Don_Dragon on 2008-04-24
Actually, I have the same laptop and broadcom card... as well as the same problem.  Upgrading completely broke the roundabout solution I had found in 7.04

---

### Post by jasonpeinko on 2008-04-24
i have nothing still, with the ndisgtk it says my driver is installed and the hardware is present but there is still nothing to do with wireless in the network manager, you are using hardy right?

---

### Post by notoriousdbp on 2008-04-24
I too am having trouble.  Ndiswrapper has worked like a charm for me up to now.  This time around I started with the b43 driver which worked great when Hardy was Alpha but now works with a really unstable connection.  I have installed ndiswrapper and got it working but can't connect to my router at all using eith network manager or wicd.  So I'm currently using a Belkin USB stick which works out of the box but it's a USB stick and I want my built in card to work like it always has up to now.  I might even roll back to Gutsy at this rate.  I just can't see any other option.

---

### Post by notoriousdbp on 2008-04-24
> **jasonpeinko said:**
> i have nothing still, with the ndisgtk it says my driver is installed and the hardware is present but there is still nothing to do with wireless in the network manager, you are using hardy right?

[[COLOR="Blue"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=734003") thread might get your ndiswrapper to spark into life at startup

---

### Post by jasonpeinko on 2008-04-24
as you were posting that i got it to work with this guide. [http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+4311+rev](http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+4311+rev)

---

### Post by Don_Dragon on 2008-04-25
Worked for me as well :)
Thanks!

---

### Post by FatmanC on 2008-04-25
> **jasonpeinko said:**
> as you were posting that i got it to work with this guide. [http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+4311+rev](http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+4311+rev)


This HowTo has fixed my broadcom wireless. Definitely worth a try.

---

