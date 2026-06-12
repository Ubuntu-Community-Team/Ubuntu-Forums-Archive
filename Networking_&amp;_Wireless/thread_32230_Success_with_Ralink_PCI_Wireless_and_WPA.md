---
title: "Success with Ralink PCI Wireless and WPA"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by joudbren on 2005-05-06
Finally!  Just a quick note to let everyone know that it is actually possible to have working WiFi-G with WPA encryption in Ubuntu.

My card is an Asus PCI Wireless G card (Gave up on the D-Link G520 "rev B3/4.10" card with Atheros chipset).  Can't see a model number on the Asus card, just "WiFi-G R1.33". The Chipset is a Ralink 2500 series and this card also has a seperate antenna on a 3 foot wire if that helps to identify it further.

I followed the instructions by Yaniv (and thank you Yaniv!) posted at [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo) and I can confirm that they work perfectly without using ndiswrapper and without using wpa_supplicant.

You will have to make the RaConfig program though as identified in the wiki as this is where you enable the WPA-PSK and enter your passphrase.  System is now booting and loading everything perfectly with no additional intervention on my part. (Yayyyy!)

Driver set being used is RT2500-cvs-20050505.  This is a "gotcha" in the wiki as the names of the subdirecty created and used by the above does not match perfectly with the name used in the Wiki but pretty straight forward to figure that one out.  Also the files you need to download to do the RaConfig2500 utility are now QT3-dev-tools and libQT3-dev.  You'll also see a note at the bottom of the Wiki confirming this as well.

Thanks again Yaniv for a job well done!  Ubuntu just keeps getting a little more amazing every day......

James   8-)

---

### Post by defkewl on 2005-05-07
Thank you so much for sharing it with us. Could you please write this down in wiki?

---

### Post by microsnot on 2005-05-07
I have no internet connection on my laptop right now so it's a matter of downloading from the XP box, putting it onto a usb key/flash drive and copying it from there.

On a fresh install:
kdebase or kde-base, qt3-dev-tools and libQT3-dev don't exist in my Synaptic.

I've downloaded them and tried to install using "sudo dpkg -i <PACKAGE>" (I'm a newbie...just found it on google). Can't install.

The wiki doc was pretty good until the section titled "Installing RaConfig?, and using it". Searched the forums and still can't work it out.  ](*,)

---

### Post by joudbren on 2005-05-08
Sorry guys, I'm pretty much a noob myself at this stuff!   Those files definitely show up in my synaptic listings but I have "Universe" and "Multiverse" repositories enabled on mine so maybe that's it?  I haven't added any additional repositories to mine other than enabling those two in addition to the default repositories.  Sorry couldn't be more help but they are definitely there and they load additional support files as well when you install them through synaptic.   Mine went without a hitch after that and then to run Raconfig you will need to do the "Sudo Nautilus" in a terminal window and then navigate back to the directory where you built RaConfig.  Cheers!

James   8-)

---

### Post by microsnot on 2005-05-08
Thanks for that. Added the comment into the wiki. So much to learn  :-?

---

