---
title: "Can't get the right resolution"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by Monkihunta on 2010-10-02
Hi,
 I'm having trouble making Ubuntu detect my monitor and it displays at the wrong resolution. The details of the monitor:

H22W-D 22" LCD Monitor 
1680x1050 
1000:1 
300cd/m2 
5ms 16:9 DVI Silver

I also gather that this infomation might be relevant:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff(prefetchable) memory:fdee0000-fdefffff ioport:ef00(size=128)

Thanks very much!

---

### Post by coffeecat on 2010-10-02
Here's your problem:

> **Monkihunta said:**
> description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]

I have no experience of SiS chipsets or graphics cards but from what I've read here, it can be an eye-watering experience to get SiS cards working properly. You could search the forums for '771/671', or perhaps someone with SiS experience will post.

Alternatively, what's your budget like? Can you afford a new graphics card? Even a low-end nvidia or ATI can support decent 3d acceleration and would probably detect your monitor accurately. ATI can be hit and miss: some cards work well, but others can be difficult. If you want the least hassle, go for nvidia.

---

### Post by Monkihunta on 2010-10-02
Thanks a lot- Now I have an excuse to buy a new graphics card!

---

### Post by coffeecat on 2010-10-02
> **Monkihunta said:**
> Thanks a lot- Now I have an excuse to buy a new graphics card!

:lol:

Before you do, do a little researching on the forum so you don't get lumbered with a "difficult" one. The chipset is more important than the card manufacturer and model number. Do you want to do gaming, or will be you be happy with a decent resolution and perhaps some compiz effects? Because, if the latter, an nvidia card in the Geforce 6***, 7*** or 8*** ranges should be all you need and they don't cost much. You'll need the proprietary nvidia driver in Lucid and Maverick for gee-whiz compiz effects, but by the time 11.04 is released (Natty Nincompoop or something), 3d acceleration will be supported in the open-source nouveau driver out of the box - or so I understand.

**Edit:** I mentioned that ATI can be a bit of a gamble, but there is one ATI card I can tell you works just fine in both Lucid and Maverick. It's the ATI Radeon HD4350. I've got one in my main desktop machine. The bonus is that I get compiz 3d effects with the default open-source ati driver. I don't need the proprietary driver. But I don't game.

Another bonus is that mine is passively-cooled = totally silent. And it's modestly priced too.

---

### Post by Monkihunta on 2010-10-02
I won't really be using it for games, except maybe really old ones on the windows side. But as for those drivers, will I just be able to install them through synaptic or software manager, or will I have to do it thorough the terminal (sorry, I'm a complete noob)

---

### Post by coffeecat on 2010-10-02
> **Monkihunta said:**
>  But as for those drivers, will I just be able to install them through synaptic or software manager, or will I have to do it thorough the terminal (sorry, I'm a complete noob)

No problem. :)

Ubuntu comes with a comprehensive set of open-source drivers, and when you boot up, the xserver, which is the underpinnings of the GUI, autodetects the graphics chipset and loads the appropriate open-source driver: ati for ATI, nouveau for NVIDIA, intel for Intel and a bag of used straw for SiS. Sorry - just kidding. :wink:

If you don't need 3d or desktop transparency, that's all you need. No extra drivers to install. Simply enjoy. But if you want 3d, etc, things are slightly more complicated, and are a moving field. Things are getting better, except for very old chipsets.

Intel: (this doesn't affect you I guess) - except for older chipsets, the intel driver supports 3d acceleration, but probably not good enough for games.

ATI: where the chipset supports this, you get 3d with most of the more recent cards using the open source ati driver. Older legacy cards should give you 2d, but often limited monitor resolutions. Some very new cards might be problematic. You'll see a lot of threads where people need help installing the proprietary (variously called fglrx or catalyst) driver. As far as I understand the proprietary driver is really only needed by gamers. As I said before, I'm perfectly happy with the 3d on my particular ATI card, but other people's experience of other cards may vary. 

NVIDIA: the so-called 'nouveau' driver will support all except very old nvidia cards, but 3d support is a bit behind the ATI driver. You can enable 3d with some experimental stuff in Lucid and Maverick, but expect further improvements next year. If you want 3d for compiz, much the best option at the moment is to install the proprietary 'nvidia' driver. This is as simple as going to System > Administration > Hardware Drivers (Additional Drivers in Maverick) and OK-ing the proprietary driver it suggests you enable.

---

### Post by formaldehyde_spoon on 2010-10-02
1680x1050 is 16:10, not 16:9...
If you're buying a new graphics card you can get a GeForce GT 260 for about $100.  The 200s are now already 2 generations old - 6000s are now 6 generations old! Ancient!

---

