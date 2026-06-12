---
title: "Need help with RTL8180"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by xbeaudet on 2007-04-25
Hello there,

isee i had a very common problem : i can't make my RTL8180 wifi card working.

I tried downloading realtek drivers [,here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L") but when i try to make / make install, I've got the error message Makefile: No such file or directory, and the directory is empty.

I tried to install the .deb package, but it's for a 2.6.18 kernel, and my Feisty one is a  2.6.20

I tried with ndiswrapper, but it doesn't seem to work (no wireless card in "networking"), and when trying lsmod, i see ndiswrapper loaded in dependency of an usb module...

can someone explain me why i can't compile realtek's modules ? or make a package for Feisty's kernel ?

thanx

by the way, i'm very surprised to see these drivers out of Feisty : they where perfect with the 6.20 version... I don't understand the reason to suppress something that works...

---

### Post by xbeaudet on 2007-04-25
I saw people over there succeed... But i didn't see any explanation...

if somebody could help...


thank's

---

### Post by Cynical on 2007-04-25
The module wasn't removed, just blacklisted. (not sure why)

I just fixed it on my mom's computer by adding r818x in /etc/modules and changing my essid in /etc/network/interfaces from "essid" to "essidX". (you can use any character in place of X, for some reason the last letter of your essid is dropped, and putting a garbage character after it fixes the problem)

---

### Post by ggratto on 2007-04-25
I was trying all sorts of editing and conf strings to get this to work. when i noticed that there was a ndiswrapper gui.... I did not pay this any mind since i could not get it to work with the cmd line ndiswrapper..but after a bit I thouhg twhat the hey i'll ttry it..... Anyway long story short. i got the rtl8180 windows drivers from realtek (the 98/200/XP one) uncompressed it,  and selected the XP inf file with the ndiswrapper gui...
it run and gave a odd error about hardware not avalible, i thought another dead end... BUT then in the network config tool the WLAN interface showed up and then after about about 2 minutes, fiddling witht eh settings for the wlan0, wep key, etc... I had my connection with WEP and the WPC11 v.4 card... Next step WPA.

---

### Post by xbeaudet on 2007-04-26
to Cynical : i'll try this, but it would be strange it works : when i try "insmod r818x" i receive "no such file"...

to ggratto : thank's for the tip... But :
- in my numerous tries, i suppressed by error the kernel module for ndiswrapper
-when i try the GUI, i've an error message explaining that ther is already an alias...

by the way, thank's to try to help... I really don't know what to do... And i would prefere not to make a fresh install : there are to many important data on my hdd...

maybe someone could send me ndiswrapper.ko (and say to me where it has to be in the modules tree).. And if someone knows where ndiswrapper registers its aliases, i could give a chance to the GUI...

---

### Post by soundguy666 on 2007-04-26
Thanks Cynical - that worked perfectly for me (Netgear MA521 PCMCIA card on a Dell laptop).

xbeaudet - use the command "modprobe r818x" rather than insmod.

---

### Post by xbeaudet on 2007-04-26
it's a good idea... But finally, ndiswrapper acepted to work (in text mode, not with the GUI)... and i really don't understand why...

If i feel some taste for risk, i'll try to replace ndiswrapper/windows driver with modprobe r818x...

by the way, thank's a lot for the help provided... really : everything works fine now, and i feel VERY HAPPY !!!

thank's again, all you here !

---

### Post by Peacemaker/Dispatch on 2007-04-26
This is my first Linux question W00T
i installed edgy last month, it worked great on my crappy off brand laptop
also my D-link DWL-650 wireless card with a RTL8180 chipset worked great
but i upgraded to Feisty Fawn and my wifi was broke and in the "hardware information" 
it did not show the card.  i think you have found the problem but Im a linux noob and i dont know how to remove the "whatever" from the Blacklist:confused: 

How Im i going to be a good linux nerd without internet:mrgreen:

---

### Post by Peacemaker/Dispatch on 2007-04-27
nvm i got :) thanks for the tip Cynical

---

### Post by motorbelly on 2007-05-15
I just spent more than a day wondering why so many of you found Cynical's fix working for you.

In the module file I edited essid to be essidx and it didn't help.

I happened to be looking at my Access Point's config and realized what the essid is, in my Netgear default the ID is "wireless" and so making it "wirelessx" did the fix! (After reboot) 

So if there are other non-geeks in here wondering how to fix their wireless access that worked perfectly before upgrading to Fiesty, look above and Cynical's post, it *DOES* work!  :)

---

### Post by ethos101 on 2007-05-18
My Dlink DWL520d with RTL8180 works in windows just fine.  It doesn't work in feisty.  The driver installs fine with ndiswrapper but in ndisgtk it says "Hardware Present: no."  Have you ever seen this before?  I remember being able to use it about a year ago.  If it was a hardware problem why would it work in windows but not feisty?

---

### Post by darkoz on 2007-06-03
> **Cynical said:**
> The module wasn't removed, just blacklisted. (not sure why)

I just fixed it on my mom's computer by adding r818x in /etc/modules and changing my essid in /etc/network/interfaces from "essid" to "essidX". (you can use any character in place of X, for some reason the last letter of your essid is dropped, and putting a garbage character after it fixes the problem)

Works perfect! Cheers Cynical!!

---

