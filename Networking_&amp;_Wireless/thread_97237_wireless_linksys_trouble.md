---
title: "wireless linksys trouble"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by smlrwd on 2005-11-30
ive started the wifi howto but my linksys wusb11 v2.6 isn't compatible. Ive download this patch here [http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html) but have no clue on if it's compatable on ubuntu or how to patch it. i am also new to linux and dont understand any of the other post on this subject. can anyone give me a kind of step by step to installing the linksys driver. thank you

---

### Post by Lambert on 2005-11-30
There is an atmel module/driver in breezy. Did you make sure that didn't load for the device and you just need to configure the network?

from a terminal

sudo lshw -businfo

look for your device in the list and notice it's class. then...

sudo lshw -C <class>
(where <class>= the class of the device found from first command with out the <>)

Then find the device in the output and look for a line configuration: should be a driver=xxx part. If not then the driver didn't load.

This thread might help also as it looks liek you need atmel-firmware also.

[http://ubuntuforums.org/showthread.php?t=29554](http://ubuntuforums.org/showthread.php?t=29554)

---

### Post by smlrwd on 2005-12-01
I checked what you told me and it has a driver listed. and i tried the sudo apt get for the atmel firmware and it said that the file was missing. i tried it twice thinking that i misspelled it and the same thing both times. and then the computer freezes. It frozes two times in a row. could this problem with the wireless card be causing it to freeze?

---

### Post by smlrwd on 2005-12-02
ok, here is what's going on now. i dont understand this wireless stuff there seems to be so many different things to configure and i know im forgeting one. i went through the wiki wireless help and no help there. 

i got the computer to stop freezing, i have to start the computer without the adapter in the usb port. once it starts up i can plug it back in and its fine

the lshw shows the card and driver

iw and if configs show the routers mac address and my ip address

it says that over like a ten minute period i recieved 8 packets and trans 12 pakets. that seem kind of low to me, but i only have my windows laptop wired connection to compared to

ping didnt work for microsoft or google's web site. and thats all the help the wiki wireless troubleshooting can give.

there is one thing that i am not sure if i have to do or how to do it and that is the dns server stuff. i think the dns is how the computer gets the numbered address for a name? but do i need to tell it a dns server to talk to or is that automatic?

---

