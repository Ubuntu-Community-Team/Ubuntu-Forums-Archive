---
title: "Running NVIDIA X Settings."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ^aDaM on 2009-01-06
Hi,

New to unbuntu 8.10. Problem is when I go to run the, "NVIDIA X Server Settings". It comes up with this msg: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I dont have a clue what to do :( as I'm very new to this type of OS, "Linux". I've only ever used MS Windows all my life!!

I have all the updates, all 216 of them. Installed the 177ver nVidia drivers.

I was told I need to setup root and sudu an things like that :)


Anyone out there that can help me out with my drivers and setup?




Regards,
^aDaM aka codingmonkey.

---

### Post by PmDematagoda on 2009-01-06
How did you install the Nvidia driver in the first place?
 
And who told you to setup root and sudo? Usually the default setup should be more than enough(it is for a lot of people).

---

### Post by lazyart on 2009-01-06
I wouldn't worry about running nvidia-settings unless something is wrong with your screen resolutions, or if you were trying to set up dual monitors.

nvidia-settings is part of the driver package.  To do what is it asking, hit Alt-F2 and type```
gksudo nvidia-settings
```It will ask for your password, then launch the app.  Most of the stuff there will be confusing at first.  If your display is doing what you want it to do then really, don't bother with it.

---

### Post by fooman on 2009-01-06
to run a command with temporary root priviledges...just put a "sudo" in front of it.

so, for the "nvidia-xconfig" command....open a terminal and type or copy/paste the following into it:

```
sudo nvidia-xconfig
```press enter and you wil be prompted for your password...type it in (it will not show in the terminal as you type it,  so get it right and press enter afterward).  when you are done log out (easiest/fastest way is to press alt-ctrl-backspace), and back in again....see if that helps.

---

### Post by ^aDaM on 2009-01-06
Hi, nice an fast reply :o

Well what I did is, installed ubuntu... updated with 216 updates, rebooted.

System > Administrator > Hardware Drivers > Installed Versions 177 of the NVIDIA Drivers [Recommended]. Rebooted, then went to go onto, "NVIDIA X Server Settings". Then that msg came up saying about edit my X Server.


Right ok, i just went to go on to the NVIDIA X Server Settings to comfirm the MSG what comes up, and it seems of to fixed it self?? comes up with my sys info and all the other settings.

To be honest I'm confused lol... aw well thanks mate! :)
so no need to restart my X Server? i know its Ctrl > Alt > Backspace.




Regards,
^aDaM aka codingmonkey.

---

### Post by ^aDaM on 2009-01-06
> **fooman said:**
> to run a command with temporary root priviledges...just put a "sudo" in front of it.

so, for the "nvidia-xconfig" command....open a terminal and type or copy/paste the following into it:

```
sudo nvidia-xconfig
```press enter and you wil be prompted for your password...type it in (it will not show in the terminal as you type it,  so get it right and press enter afterward).  when you are done log out (easiest/fastest way is to press alt-ctrl-backspace), and back in again....see if that helps.

bash: sudu: command not found
codingmonkey@ubuntu:~$ 

^^ That comes up?? take it i'm not setup to use sudu yet :/ password i used was for my username of the OS.


[EDITED] Ahh noob It's SUDO not sudu omg, my bad!! :)



Regards,
^aDaM aka codingmonkey.

---

### Post by fooman on 2009-01-06
it should be sud[COLOR=Red]o[/COLOR] ....*not* sud[COLOR=Red]u

[COLOR=Black]but if the nvidia-settings are already working....no need to bother with that.[/COLOR]
[/COLOR]

---

### Post by sadaruwan12 on 2009-01-06
> **^aDaM said:**
> Hi,

New to unbuntu 8.10. Problem is when I go to run the, "NVIDIA X Server Settings". It comes up with this msg: You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I dont have a clue what to do :( as I'm very new to this type of OS, "Linux". I've only ever used MS Windows all my life!!

I have all the updates, all 216 of them. Installed the 177ver nVidia drivers.

I was told I need to setup root and sudu an things like that :)


Anyone out there that can help me out with my drivers and setup?



Thanks,
-Regards^aDaM-

Bro, I also had your kind of problem when I was newbie to linux. What most windows migrates do when they come to Ubuntu they try to install drivers just like they did on the windows system. What you guys have to know that you don't need to install any drivers in the first place when you install Ubuntu 'cos they come with all the needed drivers. But some times Linux needs drivers that comes from vendor in your case from Nvidia so what you do download the driver from there page and install it. Well thats big mistake what you've to remember when you're on Ubuntu you don't have to down load any drivers from any vendor web and that include software packages too. Why I say this is that ubuntu poses the worlds largest software repository what you need is there (most of the times ... :D).

Know lets see just do this remove what ever driver you've installed and go to System -> Administration -> Hardware Drivers when this window lords it'll ask for a password give your login password that you used to log in to Ubuntu then wait for the window then you'll see your hardware driver name and in front of that name there is a check box and in front of that you'll a red dot followed by the text disabled. Click on the check box and it'll give a massage with two buttons click on enable then drivers will get downloaded from the repository to your PC and get installed the synaptic will ask for a system reboot so after the reboot that it your VGA drivers are installed and configured.

---

### Post by lazyart on 2009-01-06
Note that when you are running a graphical application, you should use GKSUDO instead of SUDO.

---

### Post by ^aDaM on 2009-01-12
Got it all sorted thanks guy's! ;)



Regards,
^aDaM aka codingmonkey.

---

### Post by ^aDaM on 2009-01-12
Well up to now I've gotten this far;

Installed .177 nVidia Drivers,
Installed Wine,
Installed Steam Client,
Installed OpenArena,
Installed Nexuiz/Nezuix (Pro Mode),
Installed Xchat IRC,
Installed Pidgin IM,
Installed VLC Media Player,
Installed Compiz,
Installed Ktorrent.

Next task is Quake 4, not bad for a week of using Ubuntu Linux?

Some gnome-screenies;
[IMG]http://i42.tinypic.com/23j00wh.jpg[/IMG]
[IMG]http://i39.tinypic.com/2dik679.jpg[/IMG]

[IMG]http://i39.tinypic.com/2cct1c6.jpg[/IMG]
[IMG]http://s5.tinypic.com/iy1mcm.jpg[/IMG]
[IMG]http://i43.tinypic.com/spd8g5.jpg[/IMG]

[IMG]http://i40.tinypic.com/28iyszt.jpg[/IMG]

```
cat /proc/cpuinfo

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 6
cpu MHz		: 1600.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3733.60
clflush size	: 64
```

```
Current Desktop Rig; 
Manufacturer:Intel,Gigabyte,GeiL,Gainward,Antec,Seagate,Creative,Thermaltake
Motherboard: Gigabyte GA-965P-DS3 Rev C2 Intel P965/G965
Processor: Intel Core 2 Duo E6300 @ 1.87GHz/1866MHz
Memory: GeiL Ultra DDR2 PC6400 3GB @ 400MHz
Disc Drives: Seagate 80GB @ 57.2GB Free Space / CD-RW/DVD±RW Drive 52x SATA
Videocard: Gainward Bliss 8800GT 512MB, GDDR3 PCI-E XHD @ 600MHz/900MHz/1500MHz Fanspeed 9765RPM
Monitors: Samtron 72v 17" @ 1024x768/75Hz / Samsung Series 3 26" @ 1280x720/60Hz
Soundcard: Creative Soundblaster Audigy 5.1 SE
Headphones/Speakers: Logitech USB Headset/B&W DM602 S3 Bookshelfs + Denon PMA-255UK Amplifier
Keyboards: Z-Board + All Keysets / Saitek Eclipse (Bluelight Keys)
Mouse: Logitech MX518 @ 1600DPI
Mousemat: Icemat (White) / Raptor Gaming + Spray/ QcK Steel non-slip Clothpad
Tower: Thermaltake Soprano + Clean Sidepanel / White Neon 
Powersuply: Antec HE Neo 550w
Operating System: Unbuntu 8.10 Intrepid Ibex (i386) Linux Distribution

```


All help from UbuntuForums and #ubuntu-uk channel <-- Download mIRC and connect @ irc.freenode.net#ubuntu-uk - Channel URL: irc://irc.freenode.net/ubuntu-uk

Thanks to;
popey
brobostigon
thumbnail
gord
webpigeon
CShadowRun
Chris`
JGJones
madmartian



Regards,
^aDaM aka codingmonkey.

---

