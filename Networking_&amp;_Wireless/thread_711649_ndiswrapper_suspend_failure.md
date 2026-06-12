---
title: "ndiswrapper suspend failure"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by prlancas on 2008-02-29
Hi
   I have an acer Aspire 1360 which have just stuck gutsy on (2.6.22-14-generic) it almost all works out of the box except the wireless. The suspend and hibernate are fine. So to get the wifi working I have added ndiswrapper and the neti2220 inf file. Got the wifi working but had to do a bit of a tweak to get it to connect automatically which involved adding ndiswrapper to /etc/modules and adding:

iwconfig  wlan0 essid home2
iwconfig wlan0 key "<key>"

into the start) section of /etc/init.d/networking
it now starts up fine and will switch between wireless and wired correctly preferring the wired unfortunately when the wireless has connected it fails to wake up after a suspend (mem) it goes to sleep ok spins the fans down lights the Zs and then wakes up to a black screen. I can't switch to the ttys and have to hold the big button to turn it off.

I have tried:
modprob -r ndiswrapper
and
rmmod ndiswrapper
before I suspend (from the menu item) but this drops the network and still fails to resume after a suspend. The only thing I have found that works is to press the network physical switch on the computer. That makes the resume work but has the unfortunate side effect that the wifi never works again even if i don't suspend (just turn it off and on). I have tried taking the interface down ifconfig wlan0 down then up various stuff with iwconfig etc but with no luck.

This is a major issue for me as I use my laptop to control another machine connected to the tv so wake it and suspend it around 10 times a night. It means I have to resort to using windows ;-(.

I have spent ages trying to sort this out and will be more than happy to provide any more info.

Thanks in advance

Paul

---

### Post by prlancas on 2008-04-27
I have now done an install of Hardy and suspend now works but on a resume the lite on my wireless (just above the keyboard) is off and won't turn back on using the button. I cannot connect to wireless networks any more. So I am no better off :(

Is anyone else having the same kind of problems or is it just me?

---

