---
title: "Can't connect to wireless router when password-protected; can when open."
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by andylutes on 2007-06-12
Hello everyone. I have a Dell Inspiron with a broadcom wireless card. I'm using ndiswrapper and it is working fine; I can connect to my school's public wireless network, and even to a password protected network at a government building I work at, but for some reason can't connect to my own wireless router if it is password protected. I have tried it with WEP, WPA, all the possible options, also tinkered with hexadecimal vs. ascii for the password -- nada.

Additionally, for some reason my laptop stopped being able to download torrents. I used to leave the laptop on downloading torrents while I used my other machine to do work; at some point, it stopped being able to connect, even when it is definitely connected to the internet. Can anyone help?

---

### Post by doobey on 2007-06-13
If u find out how to connect to a password protected router, please let me know. I am trying using a wired connection, and don't have a clue.

you are not using a Dell Inspiron 1300, by any chance?

~d

---

### Post by andylutes on 2007-06-17
close. inspiron 9400.

---

### Post by kevdog on 2007-06-17
Are you using knetworkmanager or network-manager-gnome (both GUI interfaces) or trying to pass these passwords through /etc/network/interfaces file??

Im assuming your using network-manager

---

### Post by andylutes on 2007-06-18
yeah, i'm using gnome network-manager. i tried wi-fi radar and one other, wi-fi assistant i think, but i have never been able to get them to connect to any network, password-protected or not, and always had to fill the ssid into the gnome network manager anyway.

---

### Post by Brighid on 2008-07-15
I don't have any answers, unfortunately, but I am having this same problem, though with a different machine and router (iMac & Airport Extreme).  Disappointing that over a year has passed and this thread is still without a solution.  If I figure it out I'll certainly post here. :-k


Edit:  It's working for me now.  To be honest .. I'm not sure what I did.  I am using Wicd as a network manager, and it had no trouble connecting when the network wasn't passworded.

There are only two things I remember doing that may have had some effect.

First, I had typed, as a final step of setup, "sudo ndiswrapper -m" into the Terminal, as I'm using ndiswrapper for my driver.  But I don't think that's what did it.

The second thing I did was go to System > Administration > Network and ensure that the Wireless connection was enabled.  I think I had already input the password and ESSID earlier on.  I guess this is what made it work properly, I really don't know.

Sorry that it's not more help, but I thought it would be wrong of me to post saying "It works!" without even a hint of how I did it.  I hope the rest of you can solve your issues, too.

---

