---
title: "bluetooth poor results"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by nsklaus on 2017-12-11
i'm getting very bad bluetooth results.
especialy with audio, but not only.
basicaly, everything "works" but overall experience is really bad.

laptop:      ubuntu 17.10 artful on macbookpro (single boot, uefi).
headset:   apple airpods
keyboard: magickeyboard2 
trackpad:  magictrackpad2
mouse:     magicmouse2
gamepad: ps4 controller

```

$ sudo dmidecode --type 1
Product Name: MacBookPro12,1

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10

$ pulseaudio --version
pulseaudio 11.0-89-g922f0

$ dpkg -l|grep bluez
ii  bluez    5.47-1

$ dpkg -l |grep magictrackpad
ii  hid-magictrackpad2-dkms    
(https://github.com/ponyfleisch/hid-magictrackpad2)

$ uname -a
Linux box 4.14.5-041405-lowlatency #201712101332 SMP PREEMPT Sun Dec 10 13:35:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

i've updated everything i could think of.
yes the results are like this:

- audio: lots of skips, loong pauses, crackling noises, loss of signal if i get farther than few centimeters from laptop (around 30cm)
- mouse and keyboard: slow to reaction, movement is choppy
- gamepad: slow to reaction, keeps acting like if buttons or dpad are pressed while they are not, miss some events..
 
keyboard and mouse/trackpad are the one working best. it's possible to use them. experience isn't great though.
gamepad: it defeat the point of being wireless. i must be so close to the laptop i'd better use a wired gamepad instead. 
audio is the absolute worst. while technically: 'sound do get transmitted to my headset' in practice it is useless. and as with gamepad i must stay very close to the laptop otherwise signal is lost.

by the way, as a comparison point: the same headset works fantastic (!) with my android phone. (and of course with macos too).
i suspect the rest of the equipment would work nicely too on android, but as i've only used the airpods with my phone i can't comment on the other elements. yet compared to linux it's like night and day.


would anyone be able to suggest something ? is there anything that could be done ?

thanks.

---

### Post by jeremy31 on 2017-12-11
If you use/need wifi there isn't much that can be done as you likely need the bcmwl-kernel-source module for wifi to work and there isn't a way to change the bluetooth coexistence setting.  You could try ```
rfkill block wifi
```
See if the bluetooth performs better

---

### Post by nsklaus on 2017-12-11
thanks for the reply jeremy31
unfortunately that doesn't improve the situation.

the same machine with the same conditions, same equipments, works fine on macos. so it's not a hardware problem.
on the linux side, bluetooth is working, equipment can be paired and connected.
but it look like it's underpowered or like if the signal was jammed or something like that. so i'm getting a lot of problems, interferences, weak or loss of signal.
the strange thing is blueman tells me the signal is 'optimal' ..
i've updated everything i could to the last version. i tried to disable wifi too. 
i even tried more bleeding edge distros, like manjaro (arch linux based).
 nothing seems to improve the signal strength.

i don't know what could be tried next.

---

