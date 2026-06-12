---
title: "Lucid screwed my Graphics up."
date: 2010-05-25
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-05-25
I recently installed Lucid after using Karmic since February and it hasn't gone well. My machine is running EXTREMELY slow and when I close a window it leaves parts of it on the screen. I can't use any effects or my machine is comatose. I had all the effects with Compiz and Emerald running with no problems before I upgraded. I posted on Installation and upgrades but haven't had any help with this so sorry for posting here as well. I'm a beginner so I don't know how to fix this stuff. oops I forgot, my graphics card is a Sapphire X1650 Pro, I have 2G RAM.

HELP?? ANYONE??

---

### Post by Peter09 on 2010-05-25
Sanity Check first:
 
Have you gone to system->admin->hardware drivers and checked for third party graphics drivers to load.
 
if no success 
 
Try going to recovery mode and selecting the reconfigure graphics drivers option
 
if no success
 
post the output of the terminal command
 
```
lshw -C video
```

---

### Post by Mark Phelps on 2010-05-25
> **ThePinkWitch said:**
>  my graphics card is a Sapphire X1650 Pro, I have 2G RAM.

There are no third-party drivers for this card that will work in recent Ubuntu versions.  Sorry.  This is one of the cards that ATI relegated to "legacy" status.  The only drivers now are the open source drivers -- which are installed by default.

---

### Post by ThePinkWitch on 2010-05-28
> **Peter09 said:**
> Sanity Check first:
 
Have you gone to system->admin->hardware drivers and checked for third party graphics drivers to load.
 
if no success 
 
Try going to recovery mode and selecting the reconfigure graphics drivers option
 
if no success
 
post the output of the terminal command
 
```
lshw -C video
```

Thanks for the replies.This is the results of the code I typed in...

*-display:0             
       description: VGA compatible controller
       product: RV535 [Radeon X1650 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 9e
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:24 memory:c0000000-cfffffff(prefetchable) ioport:9000(size=256) memory:d1000000-d100ffff memory:d0000000-d001ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV535 [Radeon X1650 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 9e
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d1010000-d101ffff
kayte@SuperCow:~$

---

### Post by ThePinkWitch on 2010-05-28
> **Mark Phelps said:**
> There are no third-party drivers for this card that will work in recent Ubuntu versions.  Sorry.  This is one of the cards that ATI relegated to "legacy" status.  The only drivers now are the open source drivers -- which are installed by default.

Hi thanks for the reply..the card worked fine in Karmic. I only have problems since I updated to Lucid.

---

### Post by ThePinkWitch on 2010-05-30
Can anyone help me with this? I tried the suggestions and it isn't working. It was working fine till I "upgraded" to Lucid, had all the cool effects, cube, emerald etc working.  I am seriously thinking of giving up on Ubuntu. I've been trying to get everything working properly since February and I'm not having much luck. I've totally given up on the idea of ditching Windoze entirely.

---

### Post by ThePinkWitch on 2010-06-04
Can someone please help me with this?

 If youre looking at my join date, I joined in 2008 and had Ubuntu for a week then my computer MB died. The computer shop upgraded my machine and put a new version of WinXP on so I didn't put Ubuntu back on. I didn't get Ubuntu again till Feb this year. I now dual boot.

---

### Post by TheMadMan on 2010-06-04
> **ThePinkWitch said:**
> Can someone please help me with this?
 
If youre looking at my join date, I joined in 2008 and had Ubuntu for a week then my computer MB died. The computer shop upgraded my machine and put a new version of WinXP on so I didn't put Ubuntu back on. I didn't get Ubuntu again till Feb this year. I now dual boot.
 
 
Sorry, but is your answer not at post no. 3 above?  He has stated that recent versions of Ubuntu do not have drivers for your graphic card driver.  I know you stated that everything worked well in the previous version of Ubuntu, but when the poster says recent versions maybe he means 10.04.
 
I'm no expert on Linux/Ubuntu (look at my post count!) but it would seem that the issue is your graphics card not being supported with up to date drives for 10.04 and maybe you will have to revert back to the previous version of ubuntu?

---

### Post by ThePinkWitch on 2010-06-04
> **TheMadMan said:**
> Sorry, but is your answer not at post no. 3 above?  He has stated that recent versions of Ubuntu do not have drivers for your graphic card driver.  I know you stated that everything worked well in the previous version of Ubuntu, but when the poster says recent versions maybe he means 10.04.
 
I'm no expert on Linux/Ubuntu (look at my post count!) but it would seem that the issue is your graphics card not being supported with up to date drives for 10.04 and maybe you will have to revert back to the previous version of ubuntu?

Well I guess that must be the answer. Thanks for your reply. I've had it with Ubuntu. I'm tired of bashing my head on the wall. Goodluck to all the other "noobs" youre going to need it.

---

