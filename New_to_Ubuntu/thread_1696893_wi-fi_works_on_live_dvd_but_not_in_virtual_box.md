---
title: "wi-fi works on live dvd but not in virtual box"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-28
Hi there my question is. I have virtual box running with windoz xp working great. so I made another account on virtual box to run backtrack 4 r2 but after set up I have no wireless. but when I run the backtrack4 as a live dvd it runs "out of the box" with just about everything. but in virtual box (bt4)I go to the terminal and type in ifconfig and no wlan0 shows up and neither does the eth0. also when I run lspci It shows the eth0 but no wireless card. any one else have this happen to them or know how to fix this? thanks for thaking the time to read this.

---

### Post by zenwalker on 2011-02-28
Just check the configuration of that VirtualBox Network adapter section. It should show you the adapter and its virtualized MAC address.

---

### Post by josephmills on 2011-02-28
ok so I have tried every settings that in under the network part of the settings in virtual box and got nothing. yes I found a mac add but I still cant find my wireless card. lspci= no wireless card
ifconfig= eth0 and lo but no wlan0 
well if some one could do a step by step I would really like that thanks again

---

### Post by Ben Page on 2011-02-28
Have you installed the vBox additions? In what mode is networking on vBox? BT simply has no drivers for the wlan adapter your vBox is using. vBox hardware is not the same as your real hardware, thus it needs special drivers, BT was never meant to work in vBox.

Not sure if I can post external links, but here you have full tutorial on installing BT in vBox in any host OS:

[http://forums.techarena.in/tips-tweaks/1334608.htm](http://forums.techarena.in/tips-tweaks/1334608.htm)

---

### Post by josephmills on 2011-02-28
> **Ben Page said:**
> Have you installed the vBox additions? In what mode is networking on vBox? BT simply has no drivers for the wlan adapter your vBox is using. vBox hardware is not the same as your real hardware, thus it needs special drivers, BT was never meant to work in vBox.

Not sure if I can post external links, but here you have full tutorial on installing BT in vBox in any host OS:

[http://forums.techarena.in/tips-tweaks/1334608.htm](http://forums.techarena.in/tips-tweaks/1334608.htm)

yes I do have the additions added on to it. as far as the network I have selected and tried all of them but right now I have selected NAT dont know if that is what you are looking for. bummer that bt was never meant for  Vbox  should I install bt4 as my host then have ubuntu and windoz xp running on a Vbox?

---

### Post by Ben Page on 2011-02-28
You should use "bridged adapter" since your native adapter works. Here is a video tut on how to install BT in vBox, hope it helps:

[http://g0tmi1k.blip.tv/file/3129332](http://g0tmi1k.blip.tv/file/3129332)

It may be that your host OS drivers are conflicting with the BTs drivers.

---

### Post by josephmills on 2011-02-28
thanks for the replies, it did not help but, I just daul booted it once again thanks for the help

---

