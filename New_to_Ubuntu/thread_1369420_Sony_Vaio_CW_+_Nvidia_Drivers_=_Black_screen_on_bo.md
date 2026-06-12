---
title: "Sony Vaio CW + Nvidia Drivers = Black screen on boot..."
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Simpsoni28 on 2009-12-31
Hi guys,

I've recently got myself a new laptop, a Sony Vaio CW... I've proceeded to install 64-bit Ubuntu onto it and everything works perfectly, all the components are picked up and work beautifully... Apart from one....

The laptop has a new Nvidia GT230M GPU and when I install the latest nvidia drivers 190.53 (i think) and reboot the white ubuntu logo appears then a black screen. If I plug a VGA cable into the laptop then the correct image appears and everything is fine... However, the laptop screen does not.

I've read on the nvnews forum [G210m Blank Laptop Display - Page 2 - nV News Forums]("http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2") that the problem is to do with ubuntu not reading the EDID correctly so the monitor is not recognised and therefore is not used... What I need is someone with this laptop to download and run softMCCS ([http://www.entechtaiwan.com/files/softmccs.exe](http://www.entechtaiwan.com/files/softmccs.exe)) and save their EDID as a .bin file and post it up here. (softMCCS is a windows program but it crashes on my laptop for some unknown reason...)

If someone could do this for me then that would be great and I would truely appreciate it because i'd hate to have to switch back to windows because of one reason! I would hate to have bought a £700 gaming laptop and not be able to use its 3D capabilities!

Thanks,

---

### Post by bads3ctor on 2010-01-01
Here you go. I had to change the file from .bin to .txt because ubuntuforums doesn't allow uploading of files with a .bin extension so you need to rename it back to sonycw.bin

Good luck with Ubuntu. I had to stay with Win7 :-(

I never got my external LCD to work with any Linux distros on my Sony CW.

---

### Post by Simpsoni28 on 2010-01-01
Thank you very much, I am so very very greatful for this :)

Have a look at the first link in my first post, thats the solution :)

---

### Post by Freebaser on 2010-01-28
Thanks for the link and the file. Worked great!

---

### Post by vainiya on 2010-02-03
Thanks for help and thanks for file; my nvidia 310M in Vaio CW with 9.10 amd64 now is ok.

---

### Post by tgui on 2010-02-03
> **bads3ctor said:**
> Here you go. I had to change the file from .bin to .txt because ubuntuforums doesn't allow uploading of files with a .bin extension so you need to rename it back to sonycw.bin

Good luck with Ubuntu. I had to stay with Win7 :-(

I never got my external LCD to work with any Linux distros on my Sony CW.

I have almost the same machine and have both HDMI and VGA working just fine. Here is how.

[http://ubuntuforums.org/showpost.php?p=8748678&postcount=16](http://ubuntuforums.org/showpost.php?p=8748678&postcount=16)

---

### Post by shayan72 on 2010-03-09
when i try to start bzflag to see it's installed or not i got this error :

Could not set Video Mode: Couldn't find matching GLX visual.

and some times I see hang of ubuntu !!

vaio F111FX 

thanks .

---

### Post by davoudi on 2010-03-20
I followed the procedure but it tells me that the driver not found! Any help?

---

### Post by eduardo.lago.aguilar on 2010-03-28
Wow! This file is the final solution! Thanks! I think it could work for many other VAIO + NVIDIA combinations.

---

### Post by rampage355 on 2010-04-16
I don't have a Vaio but the same problem. How do you install drivers if your screen is turned off, it goes off before grub. I cant get to ttyl or anything. Fairly new to doing this kind of stuff.

Thanks

---

### Post by linusr on 2010-05-03
> **rampage355 said:**
> I don't have a Vaio but the same problem. How do you install drivers if your screen is turned off, it goes off before grub. I cant get to ttyl or anything. Fairly new to doing this kind of stuff.

Thanks

Is it fixed in lucid?

I'm planning to buy this laptop but now worried

---

### Post by stnzz on 2010-05-04
No

---

### Post by bloom_20 on 2010-05-04
Hi

I just installed 9.04 on my colleagues Vaio VPCCW1S1E and then upgraded to 9.10 and today to latest 10.04. X86
Got the Nvidia Driver 195.36.15 installed.
The Graphics Card is a Geforce GT 230M and it works with a external monitor connected but i cant get anything on the laptop screen, its pitch black.
Read in forums and followed different steps but i seem to mess it up all the time....
The Xorg.conf look like this:

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

What are your suggestions?
Seen that Nvidia has released a new driver195.36.24 but i cant install this since when i shutdown X its just black and i cant do a s**t...

Thanks in advance! 
(i just started to use Ubuntu this year so i would call myself a amatuer)

---

### Post by bloom_20 on 2010-05-04
> **bloom_20 said:**
> Hi

I just installed 9.04 on my colleagues Vaio VPCCW1S1E and then upgraded to 9.10 and today to latest 10.04. X86
Got the Nvidia Driver 195.36.15 installed.
The Graphics Card is a Geforce GT 230M and it works with a external monitor connected but i cant get anything on the laptop screen, its pitch black.
Read in forums and followed different steps but i seem to mess it up all the time....
The Xorg.conf look like this:

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

What are your suggestions?
Seen that Nvidia has released a new driver195.36.24 but i cant install this since when i shutdown X its just black and i cant do a s**t...

Thanks in advance! 
(i just started to use Ubuntu this year so i would call myself a amatuer)

have now got the laptops screen to work, but now the external doesnt work through the vga.

i put a edid file for Vaio CW into /etc/X11 and changed the following in the xorg.conf file.

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
[COLOR=Red]Option "ConnectedMonitor"  "DFP-0"
Option "CustomEDID"         "DFP-0:/etc/X11/_*THE-EDID-FILE.bin*_[/COLOR]
EndSection
[SIZE=2]
Must say this is quite interesting, will try to explain what i feel by translating a Swedish saying....."well, [/SIZE][SIZE=2]if its not the one thing its the other said the girl who bled from her nose....[/SIZE]"

---

### Post by bloom_20 on 2010-05-04
Solved it with following in xorg.conf file

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
Option "ConnectedMonitor"  "DFP-0,DFP-1,CRT"
Option "CustomEDID"         "DFP-0:/etc/X11/THE-EDID-FILE.bin
EndSection

HDMI, VGA & Internal Monitor now works for me in Ubuntu 10.04 together with Nvidia 195.36.15!

I must say im impressed that i managed to solve it on my own like this!  :D

---

### Post by linusr on 2010-05-04
> **bloom_20 said:**
> Solved it with following in xorg.conf file

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
Option "ConnectedMonitor"  "DFP-0,DFP-1,CRT"
Option "CustomEDID"         "DFP-0:/etc/X11/THE-EDID-FILE.bin
EndSection

HDMI, VGA & Internal Monitor now works for me in Ubuntu 10.04 together with Nvidia 195.36.15!

I must say im impressed that i managed to solve it on my own like this!  :D

Congratz.. will fresh install of 10.04 with nouveau driver work?

---

### Post by bloom_20 on 2010-05-05
> **linusr said:**
> Congratz.. will fresh install of 10.04 with nouveau driver work?

No experience with the Noveau driver, but [COLOR=Purple]_*[this]("http://www.nvidia.co.uk/object/linux_display_ia32_195.36.15_uk.html")*_[/COLOR] Nvidia driver worked for me together with the edid file that is uploaded by bads3ctor in this tread, and now it works like a charm.

---

### Post by ref_de_leyendas on 2010-06-07
> **bloom_20 said:**
> Solved it with following in xorg.conf file

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
Option "ConnectedMonitor"  "DFP-0,DFP-1,CRT"
Option "CustomEDID"         "DFP-0:/etc/X11/THE-EDID-FILE.bin
EndSection

HDMI, VGA & Internal Monitor now works for me in Ubuntu 10.04 together with Nvidia 195.36.15!

I must say im impressed that i managed to solve it on my own like this!  :D
I am very new to Linux ... I have installed kubuntu 9.10. a vaio CW. I have the same problem - black screen when trying to use the nvidia drivers plate-310m

I have two questions:

1 - where you installed the file edid.bin? Did you have to be modified?
2 - how did you do to configure xorg?

sorry if my questions are very basic, but it is the first time I install ubuntu and really want to use

---

### Post by GLIA on 2010-06-12
I have a Sony Vaio VPCCW13FD and I'm running U-9.10:

I activated NVIDIA visa the System>Admin>Hardware Drivers route. Upon reboot, my screen was completely down. I haven't found a way to solve the problem, but I have found a few codes which successfully reversed it. Here are the steps:

1) Restart: ctrl+alt+del  OR complete shut-down and then restart
2) Access GRUB: press ESC immediately after the computer restarts
3) Choose emergency reboot: scroll down the options given 
4) Choose root directory in the terminal
5) Type (after entering your user-name and password): 

i) $ sudo jockey-text --list (to check which driver you have; it's likely to be 185) 
ii) $ sudo jockey-text -d xorg:nvidia-185 (96/173 depending on the driver type; this deactivates the driver)
iii) $ sudo shutdown -r 0 (this reboots your system; be patient here because the screen will go black for 10-15 seconds, but it's not the "screen of death")

I was very relieved to get back my desktop and to continue searching for the final solution. Hope it works for some of you also. My thanks to "[COLOR=Red]jimflood[/COLOR]" who posted these codes on another thread ([COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1307653[/COLOR]).

---

### Post by ref_de_leyendas on 2010-06-17
succeed in securing the 3D acceleration on my vaio CW with this procedure ...
but now I do not recognize the HDMI output.
I have installed the drivers 185.18.36. . .

will solve the problem by updating the drivers?
If I upgrade, I have to reconfigure xorg?

On the other hand, I'm on kubuntu 9.10, if I upgrade to 10.04, I lose the graphics settings?


thanks!

---

### Post by sanju_bd on 2010-06-22
I am running similar problem on my Sony Vaio cw series (VPC-CW29GS). My graphics is G310M GPU and I am running Kubuntu 10.04 Lucid Lynx 64 Bit on my machine. After a lot of research (using custom EDID file found in ubuntu forum, Edited xorg.conf) I was able to install the latest driver (NVIDIA-Linux-x86_64-195.36.31-pkg2.run) from nvidia support(It failed on first two occasions bcoz I didnt have kernel source and binutils package updated). 

But still there is no display. Did anybody else experiencing something like that? and also could it be directly related to "nouveau" messing up with the current display setting? I read the new Kernel source mess up with nvidia setting so it has to be blacklisted. But I installed the driver after i did the upgrade and also have blacklisted the as suggested but no luck.

Could somebody with the same laptop [NVIDIA® GeForce® G310M GPU -256MB VRAM 14" VAIO Display (1366x768 )] put up the EDID file (I am not sure if using another CW series sony vaio edid file would work or not). I have removed windows from the machine :(

Please let me know if somebody has a better suggestion. Thanks anyway.

---

### Post by Aloon on 2010-06-27
Here's all the info you need to get the 310M going. Let me know if you have any questions.

Step 1:

[http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")

Step 2:

[http://idyllictux.wordpress.com/2010...ricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")
 		                   		  		  		  		  		  	   	 		 
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] []("http://ubuntuforums.org/editpost.php?do=editpost&p=9516264")I just got everything going and it feels so great !

Good luck.

---

### Post by mrphy on 2010-08-29
> **Aloon said:**
> Here's all the info you need to get the 310M going. Let me know if you have any questions.

Step 1:

[http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")

Step 2:

[http://idyllictux.wordpress.com/2010...ricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")
                                                                                                   
                                              [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] I just got everything going and it feels so great !

Good luck.
 Hi guys
I have Sony laptop(VPCCW2 JGX),and i can't install driver of graphic card ,wireless and brightness   .
I tested very way for installing ... .
It's possible that you write stages of installing step by step.i am very tired :icon_frown:
Please help me.
detail of my laptop: 
Model =VPCCW2 JGX
Graphic card=NVIDIA 310m GEFORCE
i install ubuntu 10.04.

thanks

---

### Post by simar.mohar on 2010-09-04
> Here's all the info you need to get the 310M going. Let me know if you have any questions.

Step 1:

[http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")

Step 2:

[http://idyllictux.wordpress.com/2010...ricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")
 		                   		  		  		  		  		  	   	 		 
	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] I just got everything going and it feels so great !

Good luck.

Is the tty2 and tty1 also working 
Try Ctrl+Alt+F2 IN Gnome or Kde
what do you ovserve

To return back
Ctrl+Alt+F7

---

### Post by waqar.hameed08 on 2010-09-19
> **bloom_20 said:**
> Solved it with following in xorg.conf file

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
Option "ConnectedMonitor"  "DFP-0,DFP-1,CRT"
Option "CustomEDID"         "DFP-0:/etc/X11/THE-EDID-FILE.bin
EndSection

HDMI, VGA & Internal Monitor now works for me in Ubuntu 10.04 together with Nvidia 195.36.15!

I must say im impressed that i managed to solve it on my own like this!  :D

Thanks! I was able to run my Nvidia Geforce 310M on my Vaio VPCS116FA! Thanks to you (Y)

---

### Post by forevertheuni on 2010-10-26
Hi. In the latest series of 153.xx the EDID config was not longer necessary. If I install the latest 153.xx it works great with no configuration(if I install nvidia-bl-dkms the brightness works with options nvidia_bl max_level=0x1ffff in a modprobe.d/xxx.conf)

It seems that the 160 series do a black screen issue(I though specifying wouldn't work either...because I tried and I had blackscreen...maybe I made a mistake) anyways the stable version works...it's a pain that a problem that was solved comes back in a higher version :s.....

---

### Post by flyav on 2010-10-28
> **forevertheuni said:**
> Hi. In the latest series of 153.xx the EDID config was not longer necessary. If I install the latest 153.xx it works great with no configuration(if I install nvidia-bl-dkms the brightness works with options nvidia_bl max_level=0x1ffff in a modprobe.d/xxx.conf)

It seems that the 160 series do a black screen issue(I though specifying wouldn't work either...because I tried and I had blackscreen...maybe I made a mistake) anyways the stable version works...it's a pain that a problem that was solved comes back in a higher version :s.....

Can you tell me which version should i use? I have a GT230m which makes my driver version starts with 2xx, has the latest driver solved the problem? I have been stuck with this black screen issue since yesterday and it's driving me crazy because none of the solutions i found seem to work...

---

### Post by flyav on 2010-11-09
Anyone? any help would be appreciated.

---

### Post by NitrousUK on 2010-11-12
I'm having the same problem too. Fresh installed 10.10, let it do some updates, then it asked to install the nvidia drivers, so I "activated" them. Upon reboot I get a blank screen. However I've modified my xorg.conf to contain the lines regarding the screens and EDID file provided on this thread, but with no change. Could it be I need a different EDID from the one provided in this thread?

My laptop: Sony Vaio CW, P7450, 14" 1366x768, Nvidia GT 230M

---

### Post by porolycapa on 2010-12-12
Hey Everybody,

So, here is what I have: 
Sony Vaio VPCF1 series, Nvidia card
64-bit Ubuntu 10.10 (Fresh install)
Kernel 2.6.35.23-generic (fixed the no-touchpad issue, Yaaay)
Black-screen problem after adding the Addition Driver stuff.
I also tried to install the new Nvidia 260.19.21, same result.

What to do:

Get the 256.53 driver from the Nvidia website. (Use recovery mode and FailsafeX to do so. Google for this specific driver.  If you have encrypted home directory, you want to save it somewhere outside from your home directory, so it is accessible later. 
```
sudo cp ~/Downloads/NVIDIA-Linux-x86_64-256.53.run /etc/X11
sudo reboot
```

Get into recovery mode from grub.

Get into runlevel 3 (after you login into the root console, last option.) ```
telinit 3
```

Uninstall everything related to nvidia 
```
apt-get --purge remove nvidia-*
```

Install the new driver
```
cd /etc/X11
chmod 733 NVIDIA-Linux-x86_64-256.53.run
./NVIDIA-Linux-x86_64-256.53.run
```

Enjoy...

I assume that you have the appropriate dependencies, build-essential, linux-header etc.

**Note:** I tried the EDID workaround for 2 days, it just didn't worked. If you have problems implementing the CustomEDID, **try to revert to the 256.53 driver**, as that does not require messing with xorg.conf.
Anybody else can confirm that Kernel 2.6.35-23 & Nvidia 260.19.21 is not good combo?

---

### Post by codegrinder on 2011-02-12
I have the same problem with Ubuntu 10.10 x86_64 and Sony Vaio VPCS11V9R. Managed to make it work with nv &#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088; and EDID solution, still no nvidia drivers for 310M from official nvidia website managed to work. System / Administration / Additional drivers didn't work either. Could anyone help?

---

