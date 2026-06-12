---
title: "no gui booting from CD"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by paeppi.p on 2011-04-04
I am trying to boot Maverick from CD. 
After a while the following error message appears: 
"[  67.730462] shpchp 0000:00:01.0: Cannot reserve MMIO region". 
Then a welcome message and the prompt "ubuntu@ubuntu: ~$" 
appear in console mode.

Any suggestions?

---

### Post by seawolf167 on 2011-04-05
Looks like its just a [warning message]("http://ubuntuforums.org/showthread.php?p=10435677").

Is the CD the server version or the regular version? If its the server version there will not be a GUI, only a terminal.

---

### Post by Dutch70 on 2011-04-05
When you get to ...ubuntu@ubuntu: ~$

Try entering...
```
sudo startx
```

---

### Post by paeppi.p on 2011-04-06
> **seawolf167 said:**
> Looks like its just a [warning message]("http://ubuntuforums.org/showthread.php?p=10435677").

Is the CD the server version or the regular version? If its the server version there will not be a GUI, only a terminal.

The CD is the regular version.

---

### Post by paeppi.p on 2011-04-06
> **Dutch70 said:**
> When you get to ...ubuntu@ubuntu: ~$

Try entering...
```
sudo startx
```

I tried this. Only the tail of the output is visible on the screen. I copy some text from the output, which may be helpful:

    (==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 6 09:48:48 2011
    (==) Using system config directory "/usr/share/X11/xorg.conf.d"
    (EE) [drm] failed to open device
    (EE) open /dev/fb0: No such file or directory
    (EE) VESA(0): No valid modes
    (EE) Screen(s) found, but none have a usable configuration.
    Fatal server error: no screens found

I am now skipping some output lines. The output then ends:

    giving up.
    xinit: No such file or directory (errno 2): unable to connect to X server
    xinit: No such process (errno 3): Server error.

---

### Post by Dutch70 on 2011-04-06
Check the md5sum of your downloaded .iso, and check the cd for defects. Did you burn it at the slowest speed possible?

[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by paeppi.p on 2011-04-07
> **Dutch70 said:**
> Check the md5sum of your downloaded .iso, and check the cd for defects. Did you burn it at the slowest speed possible?

[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

The CD was burned by a friend of mine, not by myself, meanwhile he has deleted the downloaded .iso.

However, booting from this same CD works fine, if I use my laptop. It is just my somewhat older desktop pc, where I get the problems.

---

### Post by cobolt01 on 2011-04-07
> **paeppi.p said:**
> The CD was burned by a friend of mine, not by myself, meanwhile he has deleted the downloaded .iso.

However, booting from this same CD works fine, if I use my laptop. It is just my somewhat older desktop pc, where I get the problems.

How old are we talking here? Specs?

---

### Post by Dutch70 on 2011-04-07
It could be your memory causing issues. Have you added or changed the original RAM that came with the computer? If so, try going back to what you had originally until you install, then put your RAM back in. 

Also, you may want to run memtest to check your memory, but it has to run for a minimum of 8 hours, overnight is better. That's why I suggested going back to original RAM to give it a try.

---

### Post by 1991sudarshan on 2011-04-07
Press **ctrl+Alt+F7** to get the graphical mode

---

### Post by paeppi.p on 2011-04-09
sorry for double message

---

### Post by paeppi.p on 2011-04-09
> **cobolt01 said:**
> How old are we talking here? Specs?

Currently the PC runs under Ubuntu 8.04 (Hardy),
memory: 512 MB,
monitor: Samsung SyncMaster 940MW 1440 x 900

> cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 4
model name	: AMD Athlon(tm) processor
stepping	: 2
cpu MHz		: 1196.698
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips	: 2395.70
clflush size	: 32

> lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 USB Controller: NEC Corporation USB (rev 43)
00:09.1 USB Controller: NEC Corporation USB (rev 43)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by paeppi.p on 2011-04-09
> **Dutch70 said:**
> It could be your memory causing issues. Have you added or changed the original RAM that came with the computer? If so, try going back to what you had originally until you install, then put your RAM back in. 

Also, you may want to run memtest to check your memory, but it has to run for a minimum of 8 hours, overnight is better. That's why I suggested going back to original RAM to give it a try.

No, I did not change the original RAM.
memtest has been running for 3 hours without detecting any problems, I will try a longer run as you suggest.

---

### Post by paeppi.p on 2011-04-09
> **1991sudarshan said:**
> Press **ctrl+Alt+F7** to get the graphical mode

I tried this. Result was a lot of screen output ending as follows:

    * Enabling additional executable binary formats binfmt-support [OK]
    * Checking battery state...                                    [OK]

and then it hangs.

---

### Post by paeppi.p on 2011-04-12
I burned a new CD with Ubuntu 11.04 beta, and everything works fine.
Seems it was a problem with the maverick CD.

Thank you all for your help.

---

