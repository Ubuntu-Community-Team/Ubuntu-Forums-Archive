---
title: "ubuntu freezes"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by ashhab2010 on 2011-03-28
i have just started using ubuntu(10.10).
my prob is that i cant start ubuntu by normal boot, i have to select recovery mode to make my ubuntu run
in normal boot after i enter my pass, both my mouse and keyboard freeze and i am not able to do anything....
plz help..:(

---

### Post by Nickjpost on 2011-03-28
Have you tried a fresh install of 10.10? And does the mouse/keyboard work when you run the live CD (try ubuntu, I think is the option)

---

### Post by Dutch70 on 2011-03-28
Hi and welcome to UF
Are you running Compiz? 

Please run the following command in a terminal and post the output into your next post.

```
lspci
```

---

### Post by esprit53 on 2011-03-28
> **Dutch70 said:**
> Hi and welcome to UF
Are you running Compiz? 

Please run the following command in a terminal and post the output into your next post.

```
lspci
```

Running Compiz--does this possibly cause the freeze up or prevent it?

I have freezes periodically and don't know what is running.  Your answer will tell me what to check for.

Thanks.

---

### Post by Dutch70 on 2011-03-29
Compiz can cause it to freeze, but there is much more to it than that. 

Please start your own thread with a good title if you want to get help with your particular situation.

Please read this first.
[[COLOR="Red"]http://ubuntuforums.org/forumdisplay.php?f=326[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by ashhab2010 on 2011-03-29
here is the output of lspci

ashhab@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Dutch70 on 2011-03-30
I'm not familiar with that video card. 

If selecting "none" on visual effects doesn't help. Then maybe someone else will have more input on your situation.

Best regards

---

