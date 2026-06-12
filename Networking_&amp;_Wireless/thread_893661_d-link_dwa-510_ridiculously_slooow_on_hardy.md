---
title: "d-link dwa-510 ridiculously slooow on hardy"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by dexter.deepak on 2008-08-18
i am fed up with my bad-luck now ](*,)
just bought a new wireless card (d-link dwa-510) for my ubuntu-hardy system, which sucks over ubuntu but works pretty good on my windows system.i have a slooow (slower than dial-up modems) speed on ubuntu; all my friends are rolling down their ways using the same card on their windows machine...and this is the time i was looking to kick windows out of my life!!
please help me now now now, or i am thinking of a suicide :cry:

---

### Post by jimv on 2008-08-18
You could return it and get a different one.  

You can check this page to see if it's compatible:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by dexter.deepak on 2008-08-19
doesnt seem to be a good option ..
my uncle bought it miles from my present location, an  am in an urgent need of internet connection right now.
any other ideas ?

---

### Post by dexter.deepak on 2008-08-19
i know i am being desperate, but i really need help here. please.

---

### Post by DavidTangye on 2008-08-19
So did you do what Jim advised and check out your card at [_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?_]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by dexter.deepak on 2008-08-19
internet was so slow that time that i couldnt open that page at that time on ubuntu. i had a view from windows, and couldnt see my card in the supported list..also fould some bug related to the card  on hardy.
so what should i do now ? is there some hope for me ..or should i reconsider a suicide ?

---

### Post by jimv on 2008-08-19
The only other thing I can think of is to try using Ndiswrapper with the Windows driver instead.

---

### Post by dexter.deepak on 2008-08-20
i have already tried this, but still its all the same for me.

---

### Post by dexter.deepak on 2008-08-21
i just got this page saying that my card is supported on linux.
linux-wless.passys.nl/query_part.php?brandname=D-Link

i have downloaded the drivers seperately, but sont know how to install it, can someone help me...i am attaching the file too.

---

### Post by DavidTangye on 2008-08-21
So perhaps the ndiswrapper-windows driver is clashing and fighting with a linux driver that is also loading. If so you need to remove and also 'blacklist' the linux driver so it will not start in future. See: 

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[*][http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) (See the section on Troubleshooting. The example uses a Broadcom chipset, adjust for your own)
[/LIST]

---

### Post by divague on 2008-09-26
Maybe you've already solved your problem but anyway, i had this problem too with this same card, i solved it running this command in a terminal:

sudo iwconfig wlan0 rate 54M

and then reconnecting the wireless card to the signal of my network.

Hope it helps.

---

### Post by galacticcraft on 2008-12-28
> **dexter.deepak said:**
> i just got this page saying that my card is supported on linux.
linux-wless.passys.nl/query_part.php?brandname=D-Link

i have downloaded the drivers seperately, but sont know how to install it, can someone help me...i am attaching the file too.

Hi,Dexter.deepak,I have now the same problem You have some period of a year ago-may You sent now me the same file of drivers that You download that forum-I need it very-very much
thanks of Universe-measure

---

