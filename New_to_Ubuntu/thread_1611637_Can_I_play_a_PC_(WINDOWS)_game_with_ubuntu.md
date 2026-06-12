---
title: "Can I play a PC (WINDOWS) game with ubuntu?"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by scorpian81 on 2010-11-02
Hi, I am just wondering if it will be possible to play a pc game with ubuntu ok and finding my computer specs.

I would love to play GTA IV and I'm not spending £300 on a ps3 just for that. It says on the box games for windows and looking at minimum requirements for the game I know my cpu is ok but I cant work out my video card properties using lshw in terminal. I have plenty of free hard disk space.

I'm just a bit lost as I,ve never played a game on a pc before other than solitaire and ubuntu's brilliant sudoku.

Many thanks in advance.
Ian.

---

### Post by julio_cortez on 2010-11-02
Before trying to get the specs of the video card, you'd better see if the game runs in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14723&iTestingId=44672](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14723&iTestingId=44672)

It looks like the game itself didn't work a year ago, and there are no newer tests.. So I'm not even sure you could play it (even if the video card is OK)..
__

---

### Post by Verbeck on 2010-11-02
sadly, the wine appdb doesn't show good results
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8757](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8757)

if you don't want to buy a ps3, a dual boot is the best option

---

### Post by julio_cortez on 2010-11-02
> **Verbeck said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=8757](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8757)Touché. I assumed he was talking about the retail version (as he didn't mention updates of any kind) but this page is way more useful than the one I posted :D

---

### Post by scorpian81 on 2010-11-02
Thanks for the replies guys. That's a shame, but we can't have everything in life:P

when you say dual boot, do you mean haviung ubuntu and windows on the same computer/hard drive?

If yes, then that is what I have. Windows needed registering as genuine within 30 days and I thought no I'm trying ubuntu. So my only option is to find keycode hack type thing for xp?

---

### Post by julio_cortez on 2010-11-02
> **scorpian81 said:**
> So my only option is to find keycode hack type thing for xp?I'm not sure it can be discussed here, really..
But ultimately yes, you need to activate Windows for it to work completely.
And of course it would require a valid key and (if I don't remember bad) you can activate XP only N times (with N being quite a fair amount) with the same key.

---

### Post by scorpian81 on 2010-11-02
ok, sorry i did think i shouldn't say too much about the dreaded windows.
Thanks, I will continue my search for a solution to the problem at hand. and hopefully get somewhere!:)

---

### Post by Verbeck on 2010-11-02
if you think you can finish the game in 30 days, then there's no need to buy a ms windows licence :P

else, you need to activate the copy

[]("http://ubuntuforums.org/member.php?u=1069263")

---

### Post by jroa on 2010-11-02
I wonder if reseting your BIOS clock would trick it?  Probably not, but you could try.  You could also delete your Windows partition and  reinstall it, if you have the installation disk.  That would give you another 30 days.  Or just install it on a virtual machine inside of Linux.

---

### Post by julio_cortez on 2010-11-02
> **scorpian81 said:**
> ok, sorry i did think i shouldn't say too much about the dreaded windows.No wait, it must be fine to talk about Windows to a certain extent (even if you maybe won't find excellent support here of course).. But it's your referral to a *keycode hack type thing for xp* that can get you in trouble with mods.

---

### Post by Grenage on 2010-11-02
> **scorpian81 said:**
> Hi, I am just wondering if it will be possible to play a pc game with ubuntu ok and finding my computer specs.

I would love to play GTA IV and I'm not spending £300 on a ps3 just for that. It says on the box games for windows and looking at minimum requirements for the game I know my cpu is ok but I cant work out my video card properties using lshw in terminal. I have plenty of free hard disk space.

I'm just a bit lost as I,ve never played a game on a pc before other than solitaire and ubuntu's brilliant sudoku.

Many thanks in advance.
Ian.

If you're using on-board graphics, you can probably forgot about trying to play GTA IV.  Double check what card you have before you spend time dual booting the PC.

```
lspci | grep VGA
```

---

### Post by cascade9 on 2010-11-02
> **julio_cortez said:**
> But it's your referral to a *keycode hack type thing for xp* that can get you in trouble with mods.

Really? Provided that its not a malicious command, there shouldn't be any issues with posting hacks for XP.  

> **scorpian81 said:**
> I would love to play GTA IV and I'm not spending £300 on a ps3 just for that. It says on the box games for windows and looking at minimum requirements for the game I know my cpu is ok but I cant work out my video card properties using lshw in terminal. I have plenty of free hard disk space.

You dont get much in the way of video card properties in lshw, but it does at least give you the basics- 

```
*-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb01ffff

```

Should be enough to tell you if you need a video card upgrade to play GTAIV.

---

### Post by julio_cortez on 2010-11-02
> **cascade9 said:**
> Really? Provided that its not a malicious command, there shouldn't be any issues with posting hacks for XP.
I misunderstood maybe. I thought that he would like to ***actually hack*** the activation procedure in order to, well, use a non-activated copy for more than 30 days.
I might have made a mistake :D

---

### Post by Mark Phelps on 2010-11-02
> **scorpian81 said:**
> T Windows needed registering as genuine within 30 days and I thought no I'm trying ubuntu. So my only option is to find keycode hack type thing for xp?

This kind of "hacking" is ILLEGAL as it is specifically violating licensing agreements with Microsoft products.

And providing support for this is FORBIDDEN in this forum ... as mentioned specifically in the Forum Code of Conduct, Introduction, paragraph #5 as follows:

> Material that suggests illegal activity or contains illegal content is also forbidden.


---

### Post by s.fox on 2010-11-02
This forum does not support illegal activities. Thread Closed.

---

