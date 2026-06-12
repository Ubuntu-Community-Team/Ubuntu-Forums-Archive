---
title: "cannot boot if sata drive is connected"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by northstar67 on 2009-08-25
i installed ubuntu 9.04 on an ide drive,. if i attach a sata drive the grub loader stops and nothing happens, unless i detach the sata cable and reboot. then ubuntu lods fine from ide.
I can install on sata drive but at first reboot it hangs again.
live cd sees both ide and sata and i can write and read from both, but not from permanent install.
if anyone could suggest some commands to issue to a conf file i would be grateful.
Thank you

---

### Post by inobe on 2009-08-25
if the sata is set to boot in the bios it will boot before your ide hard drive.

some system bios are different by settings for a specific motherboard.

you must review the motherboard manual to know the settings to make to get it to do as you wish.

for an example my motherboard model is intel dp35dp.

with that information i can google the manual

[http://www.google.com/search?q=dp35dp+bios+manual&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=dp35dp+bios+manual&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)


you can use the computer model if you don't know about the motherboard.

---

### Post by northstar67 on 2009-08-25
hi inobe, thanks for reply.

i can set the boot order in the BIOS and i set hdd0 - the ide one- because even if i install ubuntu on the sata one and set the boot order from SCSI first, it just hangs.
It hangs even if i just connect the sata drive, which i would like to use as storage given that my working ubuntu drive is only 40 GB.
i have seen that many other users recommend some commands to add to menu.lst but i am not sure which ones to use.

---

### Post by inobe on 2009-08-25
from personal experience i had the same problems

i believe i switched it from ahci to sata/ide or the other way around.

---

### Post by northstar67 on 2009-08-25
i explored my bios so many times i know it by heart now.the mobo is not that old, 3 years....
no  ahci settings though. will try to update bios to see if it makes a change. 
do you know where to find a list of known working chipsets for these kind if issues?
thanks again

---

### Post by inobe on 2009-08-25
mines is also a few years old though it's not a locked bios, i purchased the motherboard from the manufacturer !

if your pc is a compaq or dell' these settings may not be unlocked to you.


some things you could try, setting the ide drive to cable select rather than master to eliminate what boot device is master, or set the sata for slave..


a sata without jumpers is master.

---

