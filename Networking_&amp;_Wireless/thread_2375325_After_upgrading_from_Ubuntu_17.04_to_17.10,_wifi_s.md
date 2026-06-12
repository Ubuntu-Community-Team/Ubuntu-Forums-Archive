---
title: "After upgrading from Ubuntu 17.04 to 17.10, wifi stopped working"
date: 2017-10-23
forum: Networking &amp; Wireless
---

### Post by andre.luchetti on 2017-10-23
I'm new to Ubuntu and Linux, so I followed the instructions by "bapoumba" in "Before posting in Networking & Wireless" and I'm attaching here the "wireless-info" file.

Thank you!!!

[ATTACH]277240[/ATTACH]

---

### Post by wildmanne39 on 2017-10-23
The output shows a hardblock which means your physical switch is off, if you have a switch turn it on or wifi may be turned on with a key combination like fn+ f5.

---

### Post by andre.luchetti on 2017-10-24
Hi, wildmanne39! Thanks for helping!
I've tried it. I always did it when entering Ubuntu. Now, after the update, the status change from "airplane mode" to "airplane mode disabled", yet the Wifi light in my notebook doesn't turn on, and the sarting menu keep displaying "Wi-Fi hardware disabled".
Can it be a driver problem? I use dual boot with Windows 10, and the Wi-Fi continues to work normally there.

---

### Post by wildmanne39 on 2017-10-25
I have an issue in 17.10 when I reboot I do not have wifi but if I shut down then boot I do, can you please try that and if it remains off post new wireless script please.

Thanks

---

### Post by andre.luchetti on 2017-10-25
I've shut down, then boot. The problem persists. :(
I've also done the updates from "Software updater".
I'm attaching the new wireless script.
Thanks!

[ATTACH=CONFIG]277277[/ATTACH][ATTACH]277277[/ATTACH]

---

### Post by wildmanne39 on 2017-10-25
What is the brand of this computer?

---

### Post by andre.luchetti on 2017-10-27
[SIZE=2][FONT=arial]It's an Acer.
Acer Aspire 4752. [/FONT][/SIZE][COLOR=#000000][FONT=arial]64 bits.[/FONT][/COLOR][SIZE=2][FONT=arial]
[/FONT][/SIZE][COLOR=#000000][FONT=Calibri][SIZE=2][FONT=arial]Intel Core i5-2450M CPU @ 2.50GHz x4[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][SIZE=2][FONT=arial]RAM: 4,00 GB (3,82 GB)[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by wildmanne39 on 2017-10-27
The wifi icon is suppose to turn your wifi on and off, you can also check it by pressing the fn+f3 keys, please run:
```
rfkill
```
if it shows blocked press the fn+f3 keys once then run the command again, did the hardblock change to no? make sure the wifi is turned on in windows if it is off in windows it will be off in ubuntu and of course make sure airplane mode is off as well.

Thanks

---

### Post by andre.luchetti on 2017-10-28
Using fn+F3 works well on Windows 10 (I'm using dual boot) and it worked well on Ubuntu 16.04 and 17.04. It alternates between "Wi-Fi on" and "Airplane mode on". It also turns a physical light for Wi-Fi on my notebook on and off.
But since I updated Ubuntu to 17.10, althought fn+F3 still works the same on Windows, in Ubuntu it now alternates between "Aiplane mode off" (or "Wi-Fi harware disabled") and "Airplane mode on" (or "Wi-Fi off"). Also, the physical light doesn't turn on in Ubuntu, anymore.

When I run
```
rfkill
```
it returns me only instructions on how to use it.

But if I run "rfkill list", I get:
```
andre_luchetti@andre:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

```

If I use fn+F3 again, I get:
```
andre_luchetti@andre:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```




I tried
```
rfkill unblock wifi
```
and
```
rfkill unblock all
```
[FONT=arial]but the status doesn't change: "phy0" is still hard-blocked.

Thanks.[/FONT]

---

### Post by wildmanne39 on 2017-10-28
There is a bug causing 17.10 to only connect with a VPN connection on some machines turn it on and see if you can connect of if at least your wifi light comes on.

---

### Post by andre.luchetti on 2017-10-29
This bug is probably going to be fixed soon, right? Should we notify Ubuntu developers somehow, or they've recognized it already?

I'm using Ubuntu with cable connection for internet, so I think I'll wait for the bug to be fixed.

Thank you so much for your help!!!

---

### Post by wildmanne39 on 2017-10-29
I can not say for sure it is a bug, I was hoping you would try to connect by clicking on the VPN and report back with if it helped or not.

---

### Post by andre.luchetti on 2017-11-06
I didn't get to turn the VPN on (it asked me to configure it first), but after a common update and a reboot, Wi-Fi came to work normally again.

Anyway, thank you so much for helping!!! :D

---

### Post by wildmanne39 on 2017-11-06
Your welcome and I am glad it is working!

---

