---
title: "[SOLVED] Intel 3945 ABG w iwl3945 problem"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Orion2000za on 2008-06-26
I installed an HP laptop with Kubuntu 8.04 and only found out afterwards that wireless was disabled in the bios. Switched it on, install backports-modules for Hardy and WICD (as I prefer that to KNetworkmanager). 

the card is detected and as far as I can see drivers are loaded etc but no scanning seems to take place. Whether I try using Wicd or via iwscan etc.

What (except for total reinstall) can I do to get it to start scanning? :confused:

---

### Post by chili555 on 2008-06-26
> but no scanning seems to take place.May we please see your:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Orion2000za on 2008-06-26
You are the iw3945 man, I see you in other threads on this subject. Thanks for all the efforts!

As it is we sorted it by pure chance: the w/less is only active if there is no wired cable inserted!! I have never seen this behaviour before, dont know if it is HP specific or something. 

any way around it? Not that it is very important in all honesty, I consider this SOLVED.

Regards,
Sinclair

---

### Post by chili555 on 2008-06-26
> any way around it? Not that it is very important in all honesty[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

See this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed

---

### Post by Orion2000za on 2008-06-26
Just never experienced that behaviour before, I can have the cable in and choose w/less if I want to. Good to know though! Thanks again for taking your time!

Sinclair

---

