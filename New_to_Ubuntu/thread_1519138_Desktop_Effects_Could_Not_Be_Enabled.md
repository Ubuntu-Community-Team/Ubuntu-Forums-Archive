---
title: "Desktop Effects Could Not Be Enabled"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by DTHCND on 2010-06-27
I heard this means that my GPU isn't supported or I don't have the proper drivers for it... I'm not 100% sure what graphics card I have, but I think it's a integrated ATi Radeon 3xxx series or something... How do I install the drivers (If that's the problem)? And would upgrading to 10.04 fix anything (I'm currently running 9.10)?

---

### Post by Crazyatvspaz on 2010-06-27
this terminal command will tell you what graphics adapter you have:

 	Code:
 	lshw -C display

---

### Post by GlazedWicker on 2010-06-27
When you try to enable Desktop effects, do you get a dialogue box that says "searching for drivers" or something similar?

---

### Post by Dustin2128 on 2010-06-27
you may try downloading and executing the drivers on ATI's site... they're not the greatest linux drivers available, but they beat the default. An ATI card should have no trouble running compiz, even an integrated card.

---

### Post by DTHCND on 2010-06-27
> **Crazyatvspaz said:**
> this terminal command will tell you what graphics adapter you have:      

   Code:     lshw -C display
 Ok I did this and it said:
```
        description: VGA compatible controller
       product: RS780MC [Radeon HD 3100 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff(prefetchable) ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff

```

> **GlazedWicker said:**
> When you try to enable Desktop effects, do you get a dialogue box that says "searching for drivers" or something similar?
Ya I did... It said that for a while and then my computer seemed to freeze for a while then said Desktop Effects Could Not Be Enable...

> **Dustin2128 said:**
> you may try downloading and executing the drivers on ATI's site... they're not the greatest linux drivers available, but they beat the default. An ATI card should have no trouble running compiz, even an integrated card.
Ok I will try this...

---

### Post by DTHCND on 2010-06-27
Ok I went to the ATi website to download the drivers... Currently I am running 32 Bit... I know this is a dumb question but do I want to download the x86 or x86_64 version... I'm going to guess x86?

---

### Post by nick_goodfate on 2010-06-27
> **DTHCND said:**
> Ok I went to the ATi website to download the drivers... Currently I am running 32 Bit... I know this is a dumb question but do I want to download the x86 or x86_64 version... I'm going to guess x86?

yes, x86 for 32bit

---

### Post by nick_goodfate on 2010-06-27
if you havent download the drivers yet, try System->Administration->hardware drivers . it may have detect the driver you need ...

---

### Post by DTHCND on 2010-06-27
Ok it says ATi/AMD Proprietary FGLRX Graphics Driver is not activated... So I clicked activate, now it is installing some drivers...

---

### Post by DTHCND on 2010-06-27
Ok now it requires a restart... So I'm going to go do that...

---

### Post by DTHCND on 2010-06-27
Thanks, it's working great now... :D... Just another question... Right now my computer is sort of messed up and I'm going to reformat it when I install 10.04... What are the main differences from 9.10?

---

### Post by nick_goodfate on 2010-06-27
> **DTHCND said:**
> Thanks, it's working great now... :D... Just another question... Right now my computer is sort of messed up and I'm going to reformat it when I install 10.04... What are the main differences from 9.10?

even faster boot ;). i dont have noticed major differences ... check those technical overviews if you want :

9.10 : [https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview)
10.04 : [https://wiki.ubuntu.com/LucidLynx/TechnicalOverview](https://wiki.ubuntu.com/LucidLynx/TechnicalOverview)

EDIT : you may find it useful : [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by DTHCND on 2010-06-28
Thanks... I just formatted and am now running Lucid... It looks good :D

---

### Post by nick_goodfate on 2010-06-28
mark this thread as solved from thread tools at the top if you want . if you installed proprietary graphics driver as you did yesterday,  you may noticed that splash screen (purple screen before login screen) has smaller resolution than it should have. if you have this "problem" follow this guide : 

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

