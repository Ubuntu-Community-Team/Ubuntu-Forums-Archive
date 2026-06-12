---
title: "i can't find any drivers for my laptop ( HP 550 ) ... PLZ HELLP"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by mohameds102004 on 2010-01-30
[CENTER][COLOR="DarkRed"][SIZE="5"]i'm new wz ubuntu but it's amazing tell nw ... my main issue that i can not find any drivers for my laptop ... i need the drivers for the video card and the audio card .... PLZ HELP ME :([/SIZE][/COLOR][/CENTER]

---

### Post by NightwishFan on 2010-01-30
**Video:**
Did you look for video drivers under" System -> Administration -> Hardware Drivers?" You can also run it by pressing ALT+F2 and typing:
```
jockey-gtk
```

If there are no drivers listed, the open a terminal by pressing ALT+F2 and typing:
```
gnome-terminal
```

At the terminal enter this command and post the output here.
```
lshw -c video
```

**Audio:**
For help with audio try following these steps at:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by warfacegod on 2010-01-31
> **NightwishFan said:**
> **Video:**
Did you look for video drivers under" System -> Administration -> Hardware Drivers?" You can also run it by pressing ALT+F2 and typing:
```
jockey-gtk
```

If there are no drivers listed, the open a terminal by pressing ALT+F2 and typing:
```
gnome-terminal
```

At the terminal enter this command and post the output here.
```
lshw -c video
```

**Audio:**
For help with audio try following these steps at:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

The Terminal will complain about that last code not being sudo.

---

### Post by mohameds102004 on 2010-01-31
the code for the video is

> 

  *-display:0             
       description: VGA compatible controller
       product: Mobile GME965/GLE960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:e4400000-e44fffff memory:d0000000-dfffffff(prefetchable) ioport:4000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GME965/GLE960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e4500000-e45fffff




---

### Post by mohameds102004 on 2010-01-31
[COLOR="DarkRed"]my problem about the sound card is that i cant find my microphone ... usually i'm using skype on windows and when i installed ubuntu i cannot find my microphone ... i tried to find it more than time from the sound device but i couldn't find it .... but when i play any sound it's clearly OK .... what i can do about my MIC !!!! [/COLOR]

---

### Post by mohameds102004 on 2010-02-01
upppppppp

---

### Post by sailor2001 on 2010-02-01
in synaptics (system/admin/synaptic) download gnome-alsamixer if using alsa....... if using pulse, try searching synaptics for pulse configs    right click sound icon

---

### Post by mohameds102004 on 2010-02-02
ooooooh ... i dont know how i could thank u for ur help ... it's working ... thank u for ur help ..... thank u :)

---

### Post by mohameds102004 on 2010-02-03
ok , i have another request plz ..... i've a new scanner " Canon LiDE 100 " and i tried to use it wz Xsane but no usefulness .... wht i can do to to get my scanner work .... and my scanner isn't supported from Xsane .... is there any other program support my scanner and from where can i get it's driver .. ?????

---

### Post by mohameds102004 on 2010-02-03
uppppppppppp

---

### Post by samantha_ on 2010-02-03
> **mohameds102004 said:**
> ok , i have another request plz ..... i've a new scanner " Canon LiDE 100 " and i tried to use it wz Xsane but no usefulness .... wht i can do to to get my scanner work .... and my scanner isn't supported from Xsane .... is there any other program support my scanner and from where can i get it's driver .. ?????

nope.
Its officially a paperweight. and a huge one at that.

---

### Post by eriqjaffe on 2010-02-03
> **samantha_ said:**
> nope.
Its officially a paperweight. and a huge one at that.I have the same issue with my LIDE 90 (which I bought before I was running Ubuntu), so I just run an XP install in VirtualBox and scan to a "shared" drive.  It's not a perfect solution, but at least I don't have to reboot to scan things.

---

