---
title: "Xorg heavy cpu load"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by donny.davis on 2011-06-08
chk out the attached screenshot 
the xorg uses almost full cpu when i try to run a video or firefox
i hv a low graphics card : 64MB
RAM : 512 + 256 MB
Cpu : intel pentium 4
this is the reason why i shifted from ubuntu to xubuntu

thankx

---

### Post by Toz on 2011-06-08
Can you provide us with more detailed system information?
- What kind (make/model) of video card?
- Which drivers are you using? 
- If you are running Xubuntu, is there anything listed when you go to System->Additional Drivers? If so, have you activated them?
- A copy of /var/log/Xorg.0.log

---

### Post by mastablasta on 2011-06-08
also if your card is actually a chip that uses the CPU than that would make sense if you have some effects enabled. Try switching to pure "XFCE session" at the start instead of Xubuntu.
 
And yes Toz is right you need to provide that data to help troubleshoot.

---

### Post by donny.davis on 2011-06-08
Here is my system info:

OS : xubuntu 11.04 (natty)
Kernel : 2.6.38-8-generic
CPU : Intel(R) Pentium(R) 4 CPU 2.40GHz
RAM : 512 + 256 MiB
HardDisk : 160GB
Motherboard : Advik motherboard 845 GL (intel chipset based) 
BIOS : AwardBios
Display : Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (VGA Controller) 64MB

and there is nothing listed in Additional drivers.
xorg.O.log is attached with this reply

---

### Post by donny.davis on 2011-06-08
> **mastablasta said:**
> . Try switching to pure "XFCE session" at the start instead of Xubuntu.


i tried xfce session at startup...but of no use
the videos are still tearing...and xorg utilizing max cpu

---

### Post by Toz on 2011-06-08
> **donny.davis said:**
> Here is my system info:

OS : xubuntu 11.04 (natty)
Kernel : 2.6.38-8-generic
CPU : Intel(R) Pentium(R) 4 CPU 2.40GHz
RAM : 512 + 256 MiB
HardDisk : 160GB
Motherboard : Advik motherboard 845 GL (intel chipset based) 
BIOS : AwardBios
Display : Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (VGA Controller) 64MB

and there is nothing listed in Additional drivers.
xorg.O.log is attached with this reply

You seem to be using the VESA driver for your intel card. I would try the intel driver to see if it fixes the problem. From: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus") it suggests creating an /etc/X11/xorg.conf file with the following contents:```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

and restarting. 

Note: if for some reason you get no graphic screen on reboot, simply Ctrl-Alt-F1, login and type:```
sudo rm /etc/X11/xorg.conf
``` to remove the file and reboot.

---

### Post by donny.davis on 2011-06-10
hey Toz it didnt work...

i made a xorg.conf file with only the above mentioned text
and saved it in the location u specified
was tht enough or should i include some more codes inside it...

---

### Post by Toz on 2011-06-10
1. What happened when you rebooted with the file? 

2. Can you post a copy of the contents of the file?

3. Can you post a copy of /var/log/Xorg.0.log when you try to use that file?

---

### Post by donny.davis on 2011-06-10
when i rebooted with that file 
no GUI was provided 

i tried to search startup log files for u but in vain

the booting up commands were shown in text like...
fsck ......... [ok]
pulse-audio.....[ok]

then after some more commands finished..... 
i had to press ctrl + alt + F1 to remove the file and reboot

pls chk attached file

---

### Post by Toz on 2011-06-10
Try temporarily booting with modeset. Have a look at: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2"), specifically the section labelled "Editing the GRUB 2 Menu During Boot". After the word "splash" add "i915.modeset=1" so it looks like "<all_the_stuff_before> splash i915.modeset=1"

Boot the kernel and see if it works. Post back the contents of /var/log/Xorg.0.log again.

---

### Post by donny.davis on 2011-06-11
i did what u said
here is the xorg.O.log file

but i did not understand y i did tht....what is the use of i915.modeset=1

also i tried to run a video(fullscreen)
but still xorg is 60% and vlc is 28%
is this normal in all computers
and can't we find a driver for my intel chipset

hey toz pls dont get angry from my silly questions....

---

### Post by donny.davis on 2011-06-11
Below are few links i got when i googled about the intel 845G/GL integrated graphics chipset....i think this could help us...

[http://ubuntuforums.org/showthread.php?t=324379](http://ubuntuforums.org/showthread.php?t=324379)

[http://www.intel.com/support/chipsets/sb/cs-009236.htm](http://www.intel.com/support/chipsets/sb/cs-009236.htm)

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82845G+Graphics+Controller](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Desktop+graphics+controllers&ProductProduct=Intel%C2%AE+82845G+Graphics+Controller)

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by donny.davis on 2011-06-11
here are few more links about Xorg

[http://ubuntuforums.org/showthread.php?t=1530752](http://ubuntuforums.org/showthread.php?t=1530752)

[http://ubuntuforums.org/showthread.php?t=316924&page=2](http://ubuntuforums.org/showthread.php?t=316924&page=2)

---

### Post by Toz on 2011-06-11
> **donny.davis said:**
> i did what u said
here is the xorg.O.log file

but i did not understand y i did tht....what is the use of i915.modeset=1

also i tried to run a video(fullscreen)
but still xorg is 60% and vlc is 28%
is this normal in all computers
and can't we find a driver for my intel chipset

hey toz pls dont get angry from my silly questions....

Okay, after you booted with i915.modeset=1, Xorg still used the VESA driver. We're want it to use the intel driver (please note that the intel driver for this card is very buggy, but lets see what you can get out of it). 

Put back the /etc/X11/xorg.conf file from post #6, boot again with the i915.nomodeset=1 kernel parameter, and lets see what happens.

Also post back Xorg.0.log file and this time also /var/log/dmesg.

And don't worry, there is nothing to be angry about here.

---

### Post by donny.davis on 2011-06-11
it didnt work

---

### Post by Toz on 2011-06-11
Okay - doesn't look like the modeset kernel parameter is working, so lets forget about it.

Delete any existing /etc/X11/xorg.conf file that you might have.

Lets create another video specific file:```
sudo gedit /usr/share/X11/xorg.conf.d/20-i845g.conf
```with this contents:```

Section "Device"
        Option      "Shadow"  "False"  
        Option      "DRI" "False"     
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "82845G/GL"
        BusID       "PCI:0:2:0"
EndSection

```

Reboot (no extra kernel parameters). Post Xorg.0.log file again.

---

### Post by donny.davis on 2011-06-12
nope didnt work

---

### Post by donny.davis on 2011-06-12
hey chk this out

[http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)
especially the 5.4.3.1 section

---

### Post by Toz on 2011-06-12
FreeBSD is a different type of unix than Linux - don't think this applies here. Have a look at:[http://ubuntuforums.org/showpost.php?p=10180242&postcount=4]("http://ubuntuforums.org/showpost.php?p=10180242&postcount=4"). It suggests booting in rescue mode, running **Xorg -configure** and copying the resulting file to /etc/X11/xorg.conf.

Remember to delete the /usr/share/X11/xorg.conf.d/20-i845g.conf file.

EDIT: Another link - [http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there]("http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there")

EDIT2: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg884481.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg884481.html")- Also try with creating file /etc/modprobe.d/i915-kms.conf with contents:```
options i915 modeset=1
```

---

### Post by Toz on 2011-06-12
What does:```
lspci | grep VGA
```return?

---

### Post by donny.davis on 2011-06-12
> **Toz said:**
> What does:```
lspci | grep VGA
```return?

here is this output

---

### Post by Toz on 2011-06-12
Thanks. I came across some info about that graphics card that said that Revs 01 & 02 were buggy and that Intel fixed it in Rev 03. Doesn't help you though.

Have you tried the suggestions in post #19?

---

### Post by donny.davis on 2011-06-12
> **Toz said:**
> FreeBSD is a different type of unix than Linux - don't think this applies here. Have a look at:[http://ubuntuforums.org/showpost.php?p=10180242&postcount=4]("http://ubuntuforums.org/showpost.php?p=10180242&postcount=4"). It suggests booting in rescue mode, running **Xorg -configure** and copying the resulting file to /etc/X11/xorg.conf.


while creating the file few messages were displayed 
[warning]=error inserting i2c_algo_bit <path>no devices found
[warning]=error inserting drm....<path> no devices found
[warning]=error inserting drm_kms_helpers.....<path> no devices found 
[Fatal]= error inserting i915 <path> no devices found
No.of created drivers does not match no.of detected devices
configuration failed
closed log file

but the file was created when i rebooted
i have attached the Xorg.0.log and also the xorg.conf
but it still uses vesa... i suppose im right
can u suggest me modifications to the xorg.conf

---

### Post by donny.davis on 2011-06-12
and u know the xorg is now using approx 20% less cpu while running a fullscreen video

---

### Post by Toz on 2011-06-12
Your xorg.conf file has 3 device entries, one for intel, one for fbdev and one vesa. Guess that's why its using vesa.

Try deleting the Device sections for fbdev and vesa.

Change the intel section to read:```
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        Option     "AccelMethod" "XAA"        	# [<str>]
        Option     "DRI" "False"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        Option     "Shadow" "False"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection
```

Post back Xorg.0.log.

---

### Post by donny.davis on 2011-06-13
no didnt work
seems like i have to adjust with vesa driver

thank god tht before editing the xorg.conf i had created a copy of it...tht helped me to get the screen back...

---

### Post by donny.davis on 2011-06-13
hey i cant change my screen resolution....its now 800X600
i tried editing xorg.conf as:

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes	"1024x768" "800x600"
	EndSubSection 

but it didnt work
and also the PC doesnt shutdown properly
when i give the shutdown command... it shows me the xubuntu logo and the system is halted... the fan is still working, the LED lights on the cpu is glowing
i had this problem from the very start, also posted it in my previous threads... but no result came out from it
i have to manually switch off the power supply... to shutdown the machine

---

### Post by Toz on 2011-06-13
Ok. A few more things to try then I've exhausted my options. Can you try with the same xorg.conf file as in post #25 but this time, once with kernel parameter **nomodeset**, once with kernel parameter **i915.modeset=1** and once with the kernel parameter **i915.modeset=0**

If this doesn't work, then I don't know what else to try.

---

### Post by Toz on 2011-06-13
> **donny.davis said:**
> hey i cant change my screen resolution....its now 800X600
i tried editing xorg.conf as:

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes	"1024x768" "800x600"
	EndSubSection 

but it didnt work
and also the PC doesnt shutdown properly
when i give the shutdown command... it shows me the xubuntu logo and the system is halted... the fan is still working, the LED lights on the cpu is glowing
i had this problem from the very start, also posted it in my previous threads... but no result came out from it
i have to manually switch off the power supply... to shutdown the machine

You can always delete the /etc/X11/xorg.conf file and this will put things back they way they were.

---

### Post by donny.davis on 2011-06-13
> **Toz said:**
> Ok. A few more things to try then I've exhausted my options. Can you try with the same xorg.conf file as in post #25 but this time, once with kernel parameter **nomodeset**, once with kernel parameter **i915.modeset=1** and once with the kernel parameter **i915.modeset=0**

If this doesn't work, then I don't know what else to try.

oh my dear Toz... kernel parameters didnt work..
just one more help
should i try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and what about fluxbox

---

### Post by Toz on 2011-06-13
> should i try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Sure, you can give it a try. See what happens.

You can also try fluxbox, but I think you may find you have the same issue. The problem is the video driver, not the DE.

---

### Post by donny.davis on 2011-06-13
will lubuntu reduces the load.... since it supports old systems

---

### Post by donny.davis on 2011-06-13
nothing happened with 
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Toz on 2011-06-13
> will lubuntu reduces the load.... since it supports old systemsPerhaps you can download the Live CD - it will most probably use the VESA driver also, and give it a try and see.

---

### Post by Toz on 2011-06-13
> **donny.davis said:**
> nothing happened with 
sudo dpkg-reconfigure -phigh xserver-xorg

Yes, I figured that would happen.

---

### Post by JohnBonne on 2011-06-13
I would back everything up and be ready with the LiveCD when you have exhausted your options. From experience with ubuntu, Download Xorg from Xorg.com. That should give you a recover point in the boot installer.

---

### Post by donny.davis on 2011-06-13
anyways thankx toz for ur support
atleast i go to know something about Xorg, intel, vesa and log files

---

### Post by Alan McNea on 2012-03-24
Hello,

I recently got a dell optiplex with the same or similar graphics card with similar problems.  I couldn't find a solution online, so, I just started playing with the module options.  Anyways, it has been running for over a week now with no problems.

Here is my card:
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I put the following in /etc/modprobe.d/i915.conf
options i915 reset=Y
options i915 modeset=1
options i915 fbpercrtc=1
options i915 panel_ignore_lid=1
options i915 powersave=0
options i915 semaphores=1
options i915 i915_enable_rc6=0
options i915 i915_enable_fbc=1
options i915 lvds_downclock=0
options i915 lvds_use_ssc=1

If you already have an options file of a different name for your i915 module, put the contents in that file instead.  Remember to back up what you have first.

Anyways, I think it is the rc6 option which fixed it.  It apparently has something to do with power saving?

options i915 i915_enable_rc6=0

---

