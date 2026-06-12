---
title: "Dell Truemobile 1350 and Apple Airport"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by timmah on 2006-09-16
**any help would be greatly appreciated!**

i have a dell latitude d505 using a truemobile 1350 wifi card and i was also hoping to use my apple airport express. 

i've had -0- luck searching the forums, the wiki, the help.support.etc, anywhere.

soooo....


[LIST=1]
[*]can someone direct me to the correct drivers for the truemobile card
[*]how to install drivers for truemobile card
[*]and also answer if i can install the software to use the apple airport or confirm that that is impossible
[/LIST]

i fear if i cannot get this working in a couple days...i'll need to finally give up and return to xp. :-(

---

### Post by MikePMurphy on 2006-09-18
I have a Dell Inspiron 1150 with a 1350 wifi card, and I got it to work by following this how to: 

[http://ubuntuforums.org/showthread.php?t=185174&highlight=1350](http://ubuntuforums.org/showthread.php?t=185174&highlight=1350)

I first uninstalled the ndiswrapper driver, which did not work for me by running the command: ndiswrapper -e <driverName>

Also you need to get your machine on the internet by plugging into the ethernet port, to allow the above How To, to download the driver files.

Once you complete the How To, simply set your wireless settings under: System --> Administration --> Networking.

You can use the command iwconfig, to see if the computer is connecting to the router. Try man iwconfig for more details. Also [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) has some useful information.

It took me several hours to get my wifi to work.

Don't give up.
Good luck.

---

### Post by timmah on 2006-09-19
thanks mike...i'll try that!

do you know about being able to use the apple airport express?

---

### Post by MikePMurphy on 2006-09-19
I've never used an Apple Airport, but it is an 802.11 b/g wireless standard device, so there should be no issue with it.

Once I got my wireless card to work with Ubuntu, I connected it to three different brands of routers.

You are going to want to set you Security Options in you Apple Airport to WEP, and the (WEP Security Encryption) Authentication Type to Open System.

Use the command iwconfig to see if you computer picks up your Apple router. When it connects you will see the MAC address of your router next to the words Access Point, and the channel/freqency that it is connecting with.

---

### Post by timmah on 2006-09-23
**yippie! it worked!** in spite of me being ubuntu-mentally-challenged!

you are indeed correct mike....just stick to it and it works.

thanks a bunch for the help!

if you ever vaca in virginia beach...i know you canadians love to....let me know.

---

### Post by MikePMurphy on 2006-09-23
Great to hear it.

Have fun.

---

