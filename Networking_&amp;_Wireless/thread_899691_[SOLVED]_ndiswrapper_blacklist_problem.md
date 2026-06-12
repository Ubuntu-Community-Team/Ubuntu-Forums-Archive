---
title: "[SOLVED] ndiswrapper blacklist problem"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by fobos3 on 2008-08-24
Hi, I've installed Ubuntu today and I configured my wifi with ndiswrapper because it has max speed of 1Mb/s with the default drivers (but this way it has more detectability. Strange huh? ). So I did 
```
ndiswrapper -l
```
and it said that it had the alternative driver ssb so:
```
rmmod ssb
```
it said that it is used by b43
next:```

rmmod b43
rmmod ssb
modprobe ndiswrapper
```
And everything works fine.
I've entered b43,ssb in /etc/modprobe.d/blacklist and ndiswrapper in /etc/modules but when I reboot I cannot make the wifi to load.
Any help will be appreciated.

P.S.
Actually it's not a big problem since I've made a bash script to load every time and do the work.

Cheers

---

### Post by caljohnsmith on 2008-08-24
Just to clarify, in the /etc/modprobe.d/blacklist file, did you put "blacklist ssb" or just put the module name? I assume you used the former, but just want to make sure that's not the issue.

After blacklisting and rebooting, if you do:
```
lsmod | grep -e 43 -e ssb
```
Do you see any *43* variations or the ssb modules loaded?

---

### Post by fobos3 on 2008-08-24
> **caljohnsmith said:**
> Just to clarify, in the /etc/modprobe.d/blacklist file, did you put "blacklist ssb" or just put the module name? I assume you used the former, but just want to make sure that's not the issue.

After blacklisting and rebooting, if you do:
```
lsmod | grep -e 43 -e ssb
```
Do you see any *43* variations or the ssb modules loaded?

I put blacklist ssb, b43 of course, sorry. I don't see any 43 variations. The strange thing is that if I remove them manually everything is OK but if I put them in the blacklist it can't detect the wireless card even if I load 'em again.

---

### Post by caljohnsmith on 2008-08-24
> **fobos3 said:**
> I put blacklist ssb, b43 of course, sorry. I don't see any 43 variations. The strange thing is that if I remove them manually everything is OK but if I put them in the blacklist it can't detect the wireless card even if I load 'em again.
I've seen that happen before, but you can "brute-force blacklist" those modules by changing their file names to make them unavailable to the kernel:
```
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43/
sudo mv b43.ko b43.ko.backup
cd /lib/modules/`uname -r`/kernel/drivers/ssb
sudo mv ssb.ko ssb.ko.backup

```
That way the kernel won't even think those modules exist, so it certainly won't be able to load them. :)

---

### Post by dmizer on 2008-08-24
> **fobos3 said:**
> I put blacklist ssb, b43 of course, sorry.

Just to be sure, did you put these on separate lines like so?
```
blacklist ssb
blacklist b43
```
I don't think a comma is valid in blacklist, but I could be wrong.

---

### Post by fobos3 on 2008-08-24
> **dmizer said:**
> Just to be sure, did you put these on separate lines like so?
```
blacklist ssb
blacklist b43
```
I don't think a comma is valid in blacklist, but I could be wrong.

Yes. I did. I think comma is not valid.

---

### Post by overmetal61 on 2010-12-27
I've got this exact same problem

In /etc/modprobe.d/blacklist.conf  I've added the following:
blacklist b44
blacklist ssb
blacklist mii

Reboot...  Ethernet driver is still loading, blocking my NDISWrapper Driver for Wireless

Created a script in /etc/init.d  called KUWireless
#! /bin/sh

rmmod b44
rmmod mii
rmmod ssb
modprobe ndiswrapper


Schedule it to run:
update-rc.d KUWireless start 99 3 .


When I reboot my Ethernet Driver B44 keeps loading...

If I manually execute my script, the wireless starts working.

How can I keep this driver from loading so, I can properly block the interference with my Wireless?


Wireless device is BCM4306/2 with PCI ID: 14e4:4320

---

### Post by dmizer on 2010-12-27
> **overmetal61 said:**
> I've got this exact same problem

In /etc/modprobe.d/blacklist.conf  I've added the following:
blacklist b44
blacklist ssb
blacklist mii

Reboot...  Ethernet driver is still loading, blocking my NDISWrapper Driver for Wireless

Created a script in /etc/init.d  called KUWireless
#! /bin/sh

rmmod b44
rmmod mii
rmmod ssb
modprobe ndiswrapper


Schedule it to run:
update-rc.d KUWireless start 99 3 .


When I reboot my Ethernet Driver B44 keeps loading...

If I manually execute my script, the wireless starts working.

How can I keep this driver from loading so, I can properly block the interference with my Wireless?


Wireless device is BCM4306/2 with PCI ID: 14e4:4320

You'll be better off creating a new thread. This thread is too old to be of any use to you. Also, your card should work just fine without Ndiswrapper. Just connect your computer to the internet via a cable and check the "Hardware drivers" section in your administration menu. It should prompt you to download firmware. Once you've installed the firmware, you'll be able to connect wirelessly.

---

