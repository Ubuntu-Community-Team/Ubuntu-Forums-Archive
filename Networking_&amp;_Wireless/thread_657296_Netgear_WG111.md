---
title: "Netgear WG111"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by T_N_T on 2008-01-03
Hey guys,

I am trying to get my Netgear WG111 v4(I think( under Ubuntu. The blue light blinks, then it turns off. I can see it in network manager, but it shows no SSID's, and when I try to manually configure through network manager, the system freezes solid and I have to reboot. And when I do iwconfig, this is what i get.

tim@tim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What am I doing wrong? Any help I could get would be appreciated.

Tim

---

### Post by Hightide on 2008-01-03
HI TNT
I am using a Netgear WG111 v2 usb adaptor which automatically connected.

you could check this thread to clarify if  v4 which is i assume the latest Netgear offering is supported by ubuntu?

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

regards

---

### Post by T_N_T on 2008-01-03
It only shows up to v2 supported, guess I'm out of luck with the WG111, I have an onboard Realtek RTL8187B, but I can't get that to work either.

Tim

---

### Post by T_N_T on 2008-01-03
Scratch that, it works! I had to configure it through terminal but it works!

:guitar:

Have a good one

Tim

---

### Post by PS Nancarrow on 2008-01-14
How did you get it to work through the terminal???? I've been trying to get my WG111v2 working out of the box for some time now, and nothing seems to get it going. The blue light goes on, the network manager sees two or three wireless networks available (mine and the neighbors'), it asks for my WEP key, but it never connects. What can I do? It's getting to be too much trouble to put this much work in what is supposed to make my work *easier*!

PSN

---

