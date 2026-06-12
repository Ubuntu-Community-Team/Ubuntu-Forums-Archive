---
title: "Monitor will go to 1024*768 but max available 800*600"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by SundayStrummer on 2010-05-20
Hi. I'm an IT Professional with a limited experience of unix command prompt on AIX. I've recently installed Ubuntu 10.04 on an old Dell Optiplex GX240 with the aim of teaching myself Ubuntu, Unix, PHP and MySQL. The GX240 comes with an E151FP monitor which on Windows XP ran at 1024*768. However, the maximum resolution Ubuntu offers me is 800*600. Is there any way I can get it to run at the higher resolution?

**xrandr**
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
**lspci | grep VGA**
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

Thanks in anticipation.

Graham

---

### Post by halitech on 2010-05-20
See my post here: [http://ubuntuforums.org/showpost.php?p=9312054&postcount=5](http://ubuntuforums.org/showpost.php?p=9312054&postcount=5)

change the commands where it says mousepad to gedit

---

### Post by ronjr49423 on 2010-05-20
Maybe you could help me too. My monitor goes to 1280 x 1024 but ubuntu limits me to 1024 x 768. Here is my info:
home@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:0b.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller
home@ubuntu:~$

---

### Post by halitech on 2010-05-20
> **ronjr49423 said:**
> Maybe you could help me too. My monitor goes to 1280 x 1024 but ubuntu limits me to 1024 x 768. Here is my info:
home@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:0b.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller
home@ubuntu:~$

follow the same steps but add "1280x1024" to the modes line

---

### Post by ronjr49423 on 2010-05-20
Followed the first step and here is what I get:
home@ubuntu:~$ sudo touch /ext/X11/xorg.conf
[sudo] password for home: 
touch: cannot touch `/ext/X11/xorg.conf': No such file or directory
home@ubuntu:~$

---

### Post by SundayStrummer on 2010-05-20
Hi halitech. Thanks for your response.

Unfortunately nothing seems to have changed and I'm still stuck with 800*600 as my max resolution.

I had to create the **ext** directory and **X11** subdirectory before the touch command would work.  Does this sound right?

Thanks again.

Graham

---

### Post by SundayStrummer on 2010-05-20
Yeah, that's what I got too.[U] 
[/U][]("http://ubuntuforums.org/member.php?u=1078027")

---

### Post by halitech on 2010-05-20
sorry guys, just remembered I messed up and didn't correct the spelling. I've corrected it now. the proper path is supposed to be 

/etc/X11/xorg.conf

---

### Post by SundayStrummer on 2010-05-20
OK, I got it now.  The path to the file is **/etc/X11** not /ext/X11 or /etx/X11 as in the instructions.

I created the file there as instructed and rebooted.  Then I went to System - Preferences - Monitors and I could select 1024*768.

Thanks again for your help.

Graham

---

### Post by halitech on 2010-05-20
sorry for the confusion, I should have corrected it. Glad its working for you.

---

### Post by ronjr49423 on 2010-05-20
I'm still hoping but here is what I still get:
home@ubuntu:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: No such file or directory
home@ubuntu:~$

---

### Post by halitech on 2010-05-20
you need to run
```
sudo touch /etc/X11/xorg.conf
```
then
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by ronjr49423 on 2010-05-20
Well I have 1280x960 now and thats good for me..thanks for your help.

---

### Post by ronjr49423 on 2010-05-29
My monitor setting reverted back to 1024x768 here is my info again...ans by the way I went thru your process but it did not give me a better resolution option:
home@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:0b.0 Ethernet controller: Intel Corporation 82541EI Gigabit Ethernet Controller
home@ubuntu:~$ 

Any suggestions?

---

### Post by halitech on 2010-05-29
can you post your xorg.conf file? open a terminal and run
```
cat /etc/X11/xorg.conf
```

---

### Post by ronjr49423 on 2010-05-29
thanks for your quick reply. Here it is:
home@ubuntu:~$ cat /etc/X11/xorg.conf
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS" "true"
	HorizSync	30.0-60.0
	VertRefresh	50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
			Depth		24
			Modes		"1280x1024" "800x600"
	EndSubSection

EndSection
home@ubuntu:~$

---

### Post by ronjr49423 on 2010-05-29
Unfortunately my highest available resolution is 1024x768:confused:

---

