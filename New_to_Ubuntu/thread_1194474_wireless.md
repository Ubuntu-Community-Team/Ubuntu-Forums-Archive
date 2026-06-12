---
title: "wireless"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by wpsmithii on 2009-06-22
When I updated to kernal 2.6.24-24 my wireless quit. It doesn't work in any of the older kernals either. I'm running 8.04 Hardy.

---

### Post by Dark006 on 2009-06-22
Does it show your driver is installed with this?

```
sudo ndiswrapper -l
```

---

### Post by Miljet on 2009-06-22
When I was running 8.04, one of the updates also broke my wireless. Instead of fighting it, I just upgraded to 8.10 and it "just worked."

Mine is an Atheros AR5006EG adapter.

---

### Post by nothingspecial on 2009-06-23
What wireless card is it?

```
sudo lshw -C network
```

---

### Post by wpsmithii on 2009-06-23
I have a Trendnet TEW-423PI PCI card with a Realtek RTL8185 chip in a custom computer that dual boots XP and Linux. When I typed: sudo ndiswrapper -1, I got: install/manage windows drivers for ndiswrapper with a list of options. When I typed:sudo ndiswrapper -l, I got: net 8185: driver installed
      device (10EC:8185) present

I'm not getting any error messages but when I boot up, its not looking for the wireless connection like it used too. No little green dots lighting up sequentually with another dot going in a circle between them. Thanks in advance Bill

---

### Post by caravel on 2009-06-23
Well... there is kernel support for that chipset, so I'm not sure why you've gone for ndiswrapper?  I tried ndiswrapper on my rtl8185 based card in the past and it was no better than the open source driver - if not worse.

---

### Post by wpsmithii on 2009-06-27
After going through the "complete ndiswrapper troubleshooting guide" by pytheas22, and finding nothing wrong, I compiled v1.54 from source and it did not help. When I enabled "roaming" in the wireless setup, that solved my problem. I learned alot though. Thanks. Bill Smith:D

---

### Post by LewRockwell on 2009-06-27
> **wpsmithii said:**
> After going through the "complete ndiswrapper troubleshooting guide" by pytheas22, and finding nothing wrong, I compiled v1.54 from source and it did not help. When I enabled "roaming" in the wireless setup, that solved my problem. I learned alot though. Thanks. Bill Smith:D

just remember to pay-it-forward, both here and IRL

---

