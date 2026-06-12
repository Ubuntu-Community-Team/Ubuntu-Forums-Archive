---
title: "What graphics card do i have? Compiz not working"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Crazyatvspaz on 2010-06-25
Ok iam running 10.04 using wubi with win 7. I wanted to make sure everything woked before ditching 7. I have an ACER aspire one 12" netbook. I was hoping to get compiz to work but when i switch to extra visual effects a screen appears "searching for drivers" screen flashes several times then a box appears saying "coud not enabe extra effects".  I ran this code sudo lspci |more and got this: 
netbook@ubuntu:~$ sudo lspci |more
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 
07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH 
Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD A
udio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Ex
press Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Ex
press Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) US
B UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) US
B UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) US
B UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) US
B EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Br
idge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE
 Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E P
CI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
netbook@ubuntu:~$ 

So what graphics card do i have? i was hoping to install drivers to make this work.Id appreciate the help.

---

### Post by warfacegod on 2010-06-25
> 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH
Poulsbo) Graphics Controller (rev 07)

This would be it.

---

### Post by mk1w86 on 2010-06-25
It looks like you have onboard Intel graphics.  What model is your netbook?

---

### Post by Crazyatvspaz on 2010-06-25
The bottom on the netbook says Model: some Chinese then ZA3 its an Aspire one. Is there any drivers i can install? Thanks!

---

### Post by mk1w86 on 2010-06-26
It appears the Aspire One ZA3 is a re branded Aspire One 751h so this may be of help:

[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

More specifically here:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/) 

It looks like you have to manually install a binary driver for your onboard graphics chipset which from the looking at the links appears to be an Intel GMA500.

---

### Post by nhasian on 2010-06-26
this terminal command will tell you what graphics adapter you have:

```
lshw -C display
```

---

### Post by Crazyatvspaz on 2010-06-27
Well my battery indicator now works and i now have a better screen resolution but still no Compiz. Iam wrong when i say that 10.04 and my gma 500 video hardware just wont run Compiz? Thanks for the help iam very surprised as to how much the forums have been a help as this is my first post:0

---

### Post by Dustin2128 on 2010-06-27
it is, of course, possible that a netbook can't run compiz. However, I agree with an above poster that manually installing the official binary driver would probably solve it; my old desktop ran compiz excellently with 128Mb of video RAM and most netbooks have about that if I recall correctly. Also intel drivers sometimes don't integrate very well with linux (Trust me, I have one on my laptop) and you might just use a driver utility to modify your default open driver.

---

### Post by sandyd on 2010-06-27
> **Dustin2128 said:**
> it is, of course, possible that a netbook can't run compiz. However, I agree with an above poster that manually installing the official binary driver would probably solve it; my old desktop ran compiz excellently with 128Mb of video RAM and most netbooks have about that if I recall correctly. Also intel drivers sometimes don't integrate very well with linux (Trust me, I have one on my laptop) and you might just use a driver utility to modify your default open driver.
One of the problems with the netbooks is that some of them restrict the video memory to 8mb, especially with the GMA 500. They restrict it to 8MB-10MB, and it is not changable unless you hack the bios, which im not going to cover here.

@OP, can you go into the bios, and see how much video memory you have?

---

### Post by mikewhatever on 2010-06-27
Gma500 is unsupported hardware. Manual installation of the old unsupported driver is required, but even then, compiz in 10.04 wouldn't work. Quite frankly, I wouldn't recommend running Linux at all on gma500. Save yourself the trouble and get supported hardware.

---

### Post by Crazyatvspaz on 2010-06-27
Thank for all of your help. I think ill forget compiz on this net book. I have everything else working fine.

---

