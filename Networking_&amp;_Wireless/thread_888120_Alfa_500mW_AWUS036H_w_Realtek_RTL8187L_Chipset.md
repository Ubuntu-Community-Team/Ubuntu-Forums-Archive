---
title: "Alfa 500mW AWUS036H w/ Realtek RTL8187L Chipset"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Kalister on 2008-08-12
I recently bought this wireless card, and the thing does not keep a steady connection. I installed the aircrack-ng custom drivers, and while this did keep the connection from dropping every half hour, the card still has constant slowdowns (for a couple seconds, the speed drops to zero). Signal strength is still excellent though.

I read that this card was high recommended, so I was quite surprised when it started failing on me.

Also, this card works perfectly under Windows XP.

---

### Post by Kalister on 2008-08-12
No one has heard of this? :confused:

---

### Post by Kalister on 2008-08-12
Odd. I just booted up a LiveCD with Backtrack. Lo and behold, the card works perfectly. It doesn't slowdown ever, and the speed overall is incredibly fast.

Could there be an inherent differnce between KDE and Gnome?

---

### Post by Kalister on 2008-08-13
Well, I fixed the problem...


By uninstalling Ubuntu.

And installing Kubuntu.

Case closed. Kubuntu works flawlessly. Sorry Stallman, Kubuntu uses proprietary drivers for my wifi card. Too bad the GNU Licensed ones don't work :mad:

---

### Post by kamal057 on 2008-12-22
hey, i have the same problem, with BT3 the device works 100% fine, but with ubuntu, weak signal with alot of troubles, I tried to install kubuntu, but same troubles.
I have a feeling that it is something that related to the power the the USB 2.0 tried to take, because the LED doesnt blink at all, but in vista it works 100% fine. 
I got a CD that came with the device package, tried the linux driver there, but every time I try "make", i get tons of errors.

---

### Post by kamal057 on 2008-12-24
Ok, here is the solution that everyone would absulotely love to have :) 
follow this step by step:

[http://www.aircrack-ng.org/doku.php?id=r8187#general](http://www.aircrack-ng.org/doku.php?id=r8187#general)

---

### Post by andersja on 2009-06-17
Has this problem been fixed? If not - I suggest you provide as much detail as possible in a bug report on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux]("https://bugs.launchpad.net/ubuntu/+source/linux")

---

### Post by JayUK20 on 2009-07-21
I followed the the inscurtions on the said site above but I get the following errors when trying the make command:

> wubi@ubuntu:~/rtl8187_linux_26.1010.0622.2006$ make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/wubi/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.28-13-server/build M=/home/wubi/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.28-13-server/build: No such file or directory. Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/wubi/rtl8187_linux_26.1010.0622.2006/ieee80211'


I'm a bit confused as to why I have this error and I do not know what an unknown directory is?

---

