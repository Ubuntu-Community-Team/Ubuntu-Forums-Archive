---
title: "wireless switch not working"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by bharath1097 on 2008-05-16
i have a dell vostro 1500 laptop with  Broadcom Corporation BCM94311MCG wlan mini-PCI wireless card. i am unable to get my wireless card to switch off using the switch on my laptop. the wireless switch worked perfectly on windows, fedora 8 and ubuntu gutsy. can anybody help me ? thanks in advance

---

### Post by chili555 on 2008-05-16
May I assume you are using the native modules, b43, ssb, etc.? A look at *modinfo b43* says it depends on a module: rfkill. > modinfo b43
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
---snip---
depends:        mac80211,ssb,input-polldev,led-class,rfkillI wonder if rfkill got loaded in your case. Check with *lsmod | grep kill*. If no module named rfkill is reported, then do:```
sudo modprobe rfkill
```Did that fix the switch? Let us know. If it does, you can make the fix permanent by adding *rfkill* to */etc/modules.*

If you are using ndiswrapper and not b43, post back and we'll help.

---

### Post by bharath1097 on 2008-05-16
rfkill did get loaded. the output of lsmod | grep kill is
rfkill_input     5504      0
rfkill           8592      3    rfkill_input, b43

---

### Post by bharath1097 on 2008-05-16
i am not using ndiswrapper. I am using b43

---

### Post by chili555 on 2008-05-16
From here on, it's conjecture, guesswork and a lot of beard scratching. I looked at *modinfo b43* and saw this:> chili@LAPTOP60:~$ modinfo b43
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
---snip---
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt: Disable hardware encryption. (int)I do not know if *hwpctl* is what we're looking for or not, but it's easy to try. *sudo gedit /etc/modules* to add:```
b43 hwpctl=1
```Save and close gedit. Reboot and tell us if the switch now works. I hope it does, I'm about out of ammo.

---

### Post by bharath1097 on 2008-05-17
It is not working

---

### Post by bharath1097 on 2008-05-17
Thanks anyway. I think i'll keep the wireless always on

---

### Post by darshanp on 2011-02-24
I'm using Dell inspiron 1370 and adding the line to [I]/etc/modules worked really well for me. 

Thanks a lot!!
[/I]

---

