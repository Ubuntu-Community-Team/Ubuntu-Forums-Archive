---
title: "No Wifi adapter found, Ubuntu 20.04, Lenovo I deapad 320 15IKB"
date: 2020-06-05
forum: Networking &amp; Wireless
---

### Post by beta-me on 2020-06-05
[COLOR=#242729][FONT=Arial]I did a fresh install of Ubuntu 20.04 on my laptop Lenovo ideapad 320 15IKB, and since then I am not able to use wifi(bluetooth works fine). 
It says wifi adapter not found. Previously I have used Fedora 31, Ubuntu 18.04 on my laptop and wifi was working fine. 
Currently using LAN cable for internet.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I have posted the question here -> [https://askubuntu.com/questions/1246844/lenovo-ideapad-320-15ikb-ubuntu-20-04-wifi-adapter-not-found](https://askubuntu.com/questions/1246844/lenovo-ideapad-320-15ikb-ubuntu-20-04-wifi-adapter-not-found)

Attaching output of following : 
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \[/FONT][/COLOR]
chmod +x wireless-info && \ [COLOR=#000000][FONT=&amp]./wireless-info[/FONT][/COLOR]
```

[https://pastebin.com/RL6MF0sM](https://pastebin.com/RL6MF0sM)
[COLOR=#242729][FONT=Arial]

I can provide more information if needed.
Please help me out here.
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]     
[/FONT][/COLOR]

---

### Post by grahammechanical on 2020-06-06
I do not think that I can help much. The good news is that rfkill reports

> ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

This usually means that the wireless adapter is not switched off by software in the OS or by some switch on the machine. Now for the bad news.

iwconfig reports

> enp2s0    no wireless extensions.

lo        no wireless extensions.

enp2s0 is the ethernet adapter. Elsewhere in the report you will see that enp2s0 has a driver installed. But iwconfig should also be reporting the wireless adapter as being present and it does not. For a wireless adapter it would show something like wl followed by a combination of letters and numbers and other information including signal level, transmitting power. Useful stuff to give confidence that any problem lies elsewhere.

I am guessing that the adapter needs a driver. I am not much help I am afraid. You can try running this command

```
sudo lshw -C network
```

That will show your ethernet interface and it should also show your wireless interface. If it doesn't then I guess that a driver is needed. I wonder if Software & Updates>Additional Drivers will find you a wifi driver?

Regards

---

### Post by jeremy31 on 2020-06-06
Check BIOS settings, see if WLAN is enabled and possibly do a BIOS reset to defaults.  The results show an Intel bluetooth adapter but it doesn't show the Intel wifi adapter that it is part of

---

