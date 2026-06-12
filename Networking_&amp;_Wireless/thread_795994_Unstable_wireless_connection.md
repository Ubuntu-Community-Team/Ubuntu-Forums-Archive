---
title: "Unstable wireless connection"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by tzach on 2008-05-16
I have a dual Intel cpu system, with EDIMAX PCI wireless card, and a 8.04 desktop (kernel 2.6.24-16-rt)

Initially the system recognized the WiFi and connoted, but the connection is lost after a few minute of use, and a restart is required.
The WiFi is from a standard LinkSys, and does not require password (only MAC filtering).
I notice it happen relatively fast when I'm opening multiple tabs on Firefox, but I'm not sure there is a correlation.

I already try to use Wicd with no help.
Any help would be appreciated.

Thanks
Tzach

---

### Post by Chainz on 2008-05-16
I have something similar.

After fresh install (Ubuntu 8.04), working on wireless (LinkSys router), I started Firefox and opened few sites (mostly Ubuntu Documentation).
after few minutes (2 or 3) some sites stopped opening, then more stopped opening, after about 5 min. I couldn't open a single page.

I decided to install Opera - exactly same result.

Then I turned to wired connection - still the same! :(

And now I don't know what might be the problem, since all other computers in the network work fine, windows on the same machine works fine... :'(

---

### Post by tzach on 2008-05-19
Thank Chainz
Any idea? This issue practically makes my desktop useless :(

---

### Post by roofchop on 2008-05-19
I have a similar issue with wireless on my laptop connecting to a linksys router.  It seems to just randomly loose the connection, typically after a minute of inactivity.  I found that reentering my WPA network key in the settings will restore the connection, but I think this is just because it prompts ubuntu to reestablish the network settings.  I am still looking for answers, but I agree makes it hard to do anything.

Good Luck,
roofchop

---

### Post by olemagnus on 2008-05-20
> **tzach said:**
> I have a dual Intel cpu system, with EDIMAX PCI wireless card, and a 8.04 desktop (kernel 2.6.24-16-rt)

Initially the system recognized the WiFi and connoted, but the connection is lost after a few minute of use, and a restart is required.
The WiFi is from a standard LinkSys, and does not require password (only MAC filtering).
I notice it happen relatively fast when I'm opening multiple tabs on Firefox, but I'm not sure there is a correlation.

I already try to use Wicd with no help.
Any help would be appreciated.

Thanks
Tzach
Mine is eaven WORSE! I use hardy and got an (obsolete? lol) D-link DWL-122 USB Wireless Adapter. The "usbprism2"-driver supports my adapter, but not my WAP-PSK incryption - so i cchange to WEP-incryption instead. Now i can connect. This is what happends:
1. The icon is two grey balls placed diagonally at 45 degrees (50gon lol) with a blue "cloud" sircling the diameter of the two
2 The lower ball turns green
3 The upper ball turns green
4 The blue "stairs" that show i have full signal strength appears
5 After half a secound - a secound it's offline.

ERGO - totally useless.

I have been trying to get my wireless to work for a month with my WAP-PSK and found that that just won't work. So now i am SOOOO close. I can practically taste it!

HELP ME! Thanks.  Being n00b am I...

---

### Post by olemagnus on 2008-05-20
> **olemagnus said:**
> Mine is eaven WORSE! I use hardy and got an (obsolete? lol) D-link DWL-122 USB Wireless Adapter. The "usbprism2"-driver supports my adapter, but not my WAP-PSK incryption - so i cchange to WEP-incryption instead. Now i can connect. This is what happends:
1. The icon is two grey balls placed diagonally at 45 degrees (50gon lol) with a blue "cloud" sircling the diameter of the two
2 The lower ball turns green
3 The upper ball turns green
4 The blue "stairs" that show i have full signal strength appears
5 After half a secound - a secound it's offline.

ERGO - totally useless.

I have been trying to get my wireless to work for a month with my WAP-PSK and found that that just won't work. So now i am SOOOO close. I can practically taste it!

HELP ME! Thanks.  Being n00b am I...

OK.... Now it's working fine.... I havent tutched it! Well, hop it's stable now then....

---

### Post by Chainz on 2008-05-20
Please see this one for some updates:
[http://ubuntuforums.org/showthread.php?t=796044]("http://ubuntuforums.org/showthread.php?t=796044")

Seems like it is not connected with wireless devices only.

---

