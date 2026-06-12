---
title: "Cant set resolution- Monitor: Unknown"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Holy bible on 2011-08-26
Hi every volunteer which at least clicked on my thread. Im new to u-forums and  ubuntu too and problem popped up what made me angry because i cant use ubuntu in comfortable way. I want to use ubuntu in compare to windows (its ****) because it got terminal :D. so to the problem- i surfed every thread about resolution, monitors and so one.. but none of them helped.Im sick as mud from all that so i posted here. If anybody know the answer please write. 

Problem is that when i go "System -> Preferences -> Monitors" the biggest resolution i can set is 1024 x 768. and when i install graphic card adapter it get even worse. then the biggest res. is 640 to 480 i think, so i got it uninstalled. if it will be needed to install it i do it but i need any steps what to do. 

Holaa, for ewery answer. thanks volunteers.

---

### Post by Holy bible on 2011-08-26
and i firstly installed ubuntu maybe a 2 months before this thread and it was perfect, so i dont know.

---

### Post by jtarin on 2011-08-26
What where you doing when this problem arose? Installing some software, like a game?
Issue the command ```
lspci
``` in a terminal and post the results here.

---

### Post by realzippy on 2011-08-26
Which ubuntu version?
Which graphics driver did you install ?
Please post output from

```
lspci | grep VGA
```

```
xrandr -q
```

Btw,welcome!

---

### Post by Holy bible on 2011-08-26
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:08.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster


this is "lspci" command output

---

### Post by Holy bible on 2011-08-26
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

"lspci | grep VGA" output

---

### Post by Holy bible on 2011-08-26
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
 
"xrandr -q"  output

---

### Post by Holy bible on 2011-08-26
and now answers for you guys. Problem appeard this way. I got problem on cooler of my graph. card, but my father didnt believed me so he took pc into repair :D. repairer give some 64mbit g.card into computer but i didnt used ubuntu while this card. when my father bring back card, he realised that i was true :D so i put the card back into computer, started ubuntu (i got 10.10) but nothing happened... suddenly black screen appeard and some commands started coming up. It looked like ms-dos :) and it started some upgrading or idk what. after 3,5 hours of that screen i wrote y ffor some question and what happened. 11.04 installed into mine computer. grub was new, some old versions of linux were available and 11.04 too. and now the problem started. In grub i gone to old versions ( i hate 11.04 from that time :D) and tried to start old ubuntu version 10.10. but nothing, i couldnt choose it. when i pushed enter nothing happened. WTF?. i tried reinstall to 10.10.... and from that time i got fu*ked ubuntu. now i got 10.04 .

---

### Post by realzippy on 2011-08-26
Did installing nvidia-driver work,besides the resolutions available got worse ?

---

### Post by Holy bible on 2011-08-26
this way. When i install nvidia driver the resolution go worse. i cant set even 1024x 768, only 640 x 480 i think. so i got it uninstalled but if you wanna to try something if you got clue for that :D i can install it

---

### Post by realzippy on 2011-08-26
Tell me which monitor model you use.(vendor/type)
Then install the nvidia-driver,reboot,post.

---

### Post by Holy bible on 2011-08-26
what is vendor :D sorry but Im lame in hardware . i only know that i got Prestigio monitor and in ubuntu idk how to get system information. and btw. when i go to monitors to set resolution i got that i have unknown monitor.

---

### Post by realzippy on 2011-08-26
There must be something written on the monitor itself,or on it's back.
I want to search for data about your monitor,so we can edit a file (xorg.conf) to get all resolutions it supports...

---

### Post by madjr on 2011-08-26
GeForce FX 5500 ?

i think nvidia dropped support for that card (5xxx), probably why the "official" drivers may not work.

the open source driver may be working better.

---

### Post by realzippy on 2011-08-26
> **madjr said:**
> GeForce FX 5500 ?

i think nvidia dropped support for that card (5xxx), probably why the "official" drivers may not work.
173.14.31 supports it and should work in 10.04

---

### Post by Holy bible on 2011-08-26
so ill write everything whats on back of mine monitor :D 

17" TFT Monitor
Prestigio P179

and there are some P/N and S/N codes but they are big so idk if they will help you. and above you got type and name of monitor

---

### Post by realzippy on 2011-08-26
That's enough,thanks.
Now reinstall the driver,reboot,post when done ..I'll search meanwhile.

---

### Post by Holy bible on 2011-08-26
ok so i go "System -> Administration -> Hardware Drivers" 
and i got there two drivers 1. NVIDIA Accelerated graphics driver (version 173) [RECOMMENDED]
2. NVIDIA Accelerated graphics driver (version 96)

ill instal 173... post when installed. bye for a while :D

---

### Post by Holy bible on 2011-08-26
so i got fresh graphic driver :( ... biggest resolution 640 x 480 and when i do "System -> preferences -> Monitors" this window pop-ups
It appears that your graphic driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead? YES / NO

when i go No Monitor preferences are shown 
When i go YEs . NVIDIA X Server Settings will pop up...

---

### Post by realzippy on 2011-08-26
Yes,I expected this.Means your driver is running,we will fix the resolution now.
...show your xorg.conf file:

```
gedit /etc/X11/xorg.conf
```

post output

---

### Post by Holy bible on 2011-08-26
i was experimenting with xorg so i got it fu*ked more then it was. 

OUTPUT


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection



OUTPUT

---

### Post by realzippy on 2011-08-26
Run
```
sudo nvidia-xconfig
```
to create a new xorg.conf
then post the new one please..

---

### Post by Holy bible on 2011-08-26
new one: 

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Sun Nov  8 21:50:38 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by realzippy on 2011-08-26
Now run

```
gksudo gedit /etc/X11/xorg.conf
```

and change in  "Section Monitor" the Hsync/Vrefresh values to:

HorizSync 30.0 - 80.0
VertRefresh 56.0 - 75.0

be careful not to change anything else by accident.
Close file saving changes.
Also run:
```
rm ~/.config/monitors.xml
```

Then reboot or restart the Xserver..

After reboot your resolution (1280x1024) might be set already,if not
do not open the System =>Preferences =>Monitors tool again,
use the nvidia-settings tool to set resolution.
Then hit "apply",then hit "Save-to-X-Configuration-File".
Now your machine should reboot in correct resolution.

---

### Post by Holy bible on 2011-08-26
problem.

i cannot run code : 
mosquito@mosquito-desktop:~$ rm ~/.config/monitors.xml
rm: cannot remove `/home/mosquito/.config/monitors.xml': No such file or directory
mosquito@mosquito-desktop:~$ 



how to continue?
rm ~/.config/monitors.xml

---

### Post by realzippy on 2011-08-26
Thats no problem.Command should delete the file if it exists.
rm means "remove"....
 Because it did not exist,it cannot delete it.
All good,ignore it.Go on...

---

### Post by Holy bible on 2011-08-26
dont know how to restart X server but if i run it. nothing changed. btw. if i click anywhere on X server window it move to left corner and when i click it again it move back :D lol

---

### Post by realzippy on 2011-08-26
You can reboot instead of restarting Xserver.

---

### Post by Holy bible on 2011-08-26
maaaaan i love you :D

---

### Post by realzippy on 2011-08-26
Nah,just basic stuff.
**Please set thread as solved.**
Also suggest to stay with 10.04,since your card (nearly EOL) might not work in 
11.04.
10.04 is longer supported than 10.10,since it is a LTS version.
Have fun...

---

### Post by Apprentice Rand on 2011-09-09
Same problem, only in Jaunty Jackalope and my NVIDIA card is a 7950 GX2 and my "monitor" is a Sanyo DP19640 using the HDMI input. Same solution?

p.s.: Last download was the 280.13 (NVIDIA'srecommendation for my card).

---

### Post by madjr on 2011-09-10
> **Apprentice Rand said:**
> Same problem, only in Jaunty Jackalope and my NVIDIA card is a 7950 GX2 and my "monitor" is a Sanyo DP19640 using the HDMI input. Same solution?

p.s.: Last download was the 280.13 (NVIDIA'srecommendation for my card).

hm i dont even remember what version was jaunty.. , why not try a newer release?

anyway i dont see a problem with you trying the same methods

---

### Post by realzippy on 2011-09-10
> **Apprentice Rand said:**
> Same problem, only in Jaunty Jackalope and my NVIDIA card is a 7950 GX2 and my "monitor" is a Sanyo DP19640 using the HDMI input. Same solution?

p.s.: Last download was the 280.13 (NVIDIA'srecommendation for my card).


You should open an own thread if you cannot solve your resolution problem
with the infos here.Send me a pm then...

---

### Post by Apprentice Rand on 2011-09-10
Why can't I run gedit? It looks like I am going to have to start a new thread. Before closing this (or in a p.m.), please let me know what info I should start with on the new thread. My screen real estate issue is going to present challenges--can't see or access buttons on the bottom of window/panel.  Oh, and BTW: Jaunty Jackalope is 9.04.

---

### Post by madjr on 2011-09-10
> **Apprentice Rand said:**
> Why can't I run gedit? It looks like I am going to have to start a new thread. Before closing this (or in a p.m.), please let me know what info I should start with on the new thread. My screen real estate issue is going to present challenges--can't see or access buttons on the bottom of window/panel.  Oh, and BTW: Jaunty Jackalope is 9.04.


do newer releases have the same issue?

test a live-cd and see.

9.04 is not even supported anymore, but if you want to go ahead and try to fix it, i believe is better you should open a new thread.

---

### Post by Apprentice Rand on 2011-09-10
I have 2 Ubuntu machines: the minimalist one may be able to download and burn an .iso. The one I'm trying to get visually-usable didn't want to complete downloading the .iso--I think, but I couldn't access the bottom of the screen to check.

Going to try to burn the last LTS version.  Wish me luck.

---

### Post by Apprentice Rand on 2011-09-11
Update and good-bye to this thread: somewhat newer machine with Gx2 card is going server 10.04.3-still having issues with the display exceeding the actual screen, but with more command-line linux experience in my past, it's less intimidating.  [Win7 laptop is en route this week, so I can continue my server research from that device.]
    My ancient desktop-distro machine has an AGP graphics card (an 8 MB NVIDIA Vanta-currently ignoring the "x86-71.86.15-pkg1.run"), so new thread addressing that will follow.

---

### Post by realzippy on 2011-09-11
> **Apprentice Rand said:**
> ...let me know what info I should start with on the new thread. 

..perfect info for a graphics related issue would be:

1.Ubuntu version
2.Output from
```
lspci |grep VGA
```
3.Output from
```
xrandr -q
```
4.Content of
/var/log/Xorg.0.log
file (attached,it is too long)

---

### Post by Apprentice Rand on 2011-09-11
ver: 9.04

(grep VGA): 01:00.0 VGA Compatible controller: nVIDIA Corporation NV6 [Vanta/Vanta LT] (rev 15)

(xrandr): Can't open display

log: can't do anything but 800x600, 640x480, 400x300, and 320x240.
(still relearning the file mgmt stuff in terminal, sorry--it's been 10 years, but I did learn it once).

---

### Post by Apprentice Rand on 2011-09-11
Here goes with the log output (attached as Open Office document).

---

### Post by realzippy on 2011-09-11
1.Which monitor model do you use?
2.show xorg.conf

```
gedit /etc/X11/xorg.conf
```

---

### Post by Apprentice Rand on 2011-09-11
[LIST=1]
[*]Sanyo DP 19640. TV with VGA, HDMI inputs--my old system is using the VGA.
[*]gedit:3349): Gtk-WARNING **: Cannot open display:
[*]using vi: (see attached)
[/LIST]

---

### Post by realzippy on 2011-09-12
Try to edit your xorg.conf with Hsync/vrefresh data:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync 30-50
        VertRefresh 58-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by bapoumba on 2011-09-17
> **realzippy said:**
> 
**Please set thread as solved.**


Done :KS

---

### Post by Apprentice Rand on 2011-09-25
A corrective P.S.:  Managed to update to 10.04.3 LTS Lucid Lynx. It's a side-by-side of 64-bit server and 32-bit desktop-going to try to fix desktop then address the overscan issue in server.  Guess I will use this thread and start a new thread after I have results from my efforts.  Thanks for everything, "bean-ers(?)".

ERandall/Apprentice Rand

---

