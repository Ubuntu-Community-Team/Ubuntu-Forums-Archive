---
title: "Two problems."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-07
I installed Ubuntu on a dual boot with Vista day before yesterday.

1. When I go on AmaroK, and I try to play music, I can't. Like, I click on an artist, then double click a song for it to play, and it just goes through all the songs on all of the albums really fast and doesn't play them.

2. No sound. I went on Youtube and it isn't playing the sound. I don't know if it's always no sound on everything. Yes, my volume is up.

---

### Post by easybake on 2009-06-07
It seems as if you don't have the mp3 codecs installed. 

Edit: do you hear the login noise when you boot into Ubuntu?

---

### Post by Sedative on 2009-06-07
Well how do you install those?

EDIT: There is no login noise.

---

### Post by ad_267 on 2009-06-07
How did you install the adobe flash player? 

Try installing the ubuntu-restricted-extras and kubuntu-restricted-extras packages from System - Administration - Synaptic Package Manager. That will install the flash player and codecs for mp3 for Amarok as well as many other useful things that can't be included with Ubuntu by default for legal reasons.

---

### Post by easybake on 2009-06-07
You need to run ```
sudo apt-get install ubuntu-restricted-extras
```

[read more here if you want]("https://help.ubuntu.com/community/RestrictedFormats/")

Edit: [This may fix your sound issue]("http://onlyubuntu.blogspot.com/2008/11/fix-for-no-sound-issue-in-ubuntu-810.html")

---

### Post by Sedative on 2009-06-07
For the Ubuntu restricted extras it affects other programs. Do I still do it?

---

### Post by ad_267 on 2009-06-07
> **Sedative said:**
> For the Ubuntu restricted extras it affects other programs. Do I still do it?

What do you mean by effects other programs? It will install other packages it depends on, but it shouldn't make you remove any existing packages.

---

### Post by Sedative on 2009-06-07
I did the sound commands and now every time I try to play a Youtube video it stops after 3 seconds.


EDIT: It's making me uninstall other packages. libavcodec52 and libavutil49

---

### Post by Don1500 on 2009-06-07
> **Sedative said:**
> I installed Ubuntu on a dual boot with Vista day before yesterday.

1. When I go on AmaroK, and I try to play music, I can't. Like, I click on an artist, then double click a song for it to play, and it just goes through all the songs on all of the albums really fast and doesn't play them.

2. No sound. I went on Youtube and it isn't playing the sound. I don't know if it's always no sound on everything. Yes, my volume is up.

Go here, do what the man says. You will have music, and record it, too.

I have done this many times, and every time, it works. 

[URL="http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html"]
Click here for link[/URL]

---

### Post by Johan-Steyn on 2009-06-07
Hi,

If you have installed w32codecs or libdvdcss2 individually before, you need to use Synaptic to install the Ubuntu restricted extras, in order to resolve the dependencies.

Regards,

JS

---

### Post by 3rdalbum on 2009-06-07
> **Sedative said:**
> EDIT: It's making me uninstall other packages. libavcodec52 and libavutil49

Correct. It will install "libavcodec-unstripped-52" which has support for proprietary/patented codecs. That's what "unstripped" means - it hasn't been stripped of non-Free support.

After installing, do a search in Synaptic for "libavcodec". Install all the "unstripped" equivalents for maximum codec support.

---

### Post by Sedative on 2009-06-07
I installed ubuntu-restricted-extras and kubuntu-restricted-extras and I still have no sound on Youtube. Also, when I try to play song in AmaroK, it plays the song instead of going through all the songs really fast, but there is no sound. (Hey, we're getting there)

---

### Post by halitech on 2009-06-07
what sound card do you have? Can you post the output of the following commands in a terminal
```
lspci
```
```
sudo lshw -C sound
```
and
```
aplay -l
```

---

### Post by Sedative on 2009-06-07
```
lspci
```

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```

```
sudo lshw -C sound
```

```
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by halitech on 2009-06-07
everything looks okay there. I know this may sound like a stupid question but have you checked to make sure the speakers are plugged in properly?

---

### Post by Sedative on 2009-06-07
Yeah, I'm on a laptop, so the speakers are built in, and the volume is up.

---

### Post by halitech on 2009-06-07
Do you have a set of headphones you can try in the headphone jack? I'm wondering if it is directing sound to the headphone jack instead of the laptop speakers

---

### Post by Sedative on 2009-06-07
Kay, I tried plugging my headphones in. No sound.

---

### Post by Johan-Steyn on 2009-06-07
Hi,

Check out the **comprehensive sound guide** on this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Webbca01 suggested that, if you have an intel8x0 module, you can get AC'97 working by  	Code:
 	sudo nano /etc/modprobe.d/alsa-base 
 and adding this as the last line:  	Code:
 	"options snd-intel8x0 ac97_quirk=3" 
Regards,

JS

---

### Post by Sedative on 2009-06-07
I don't know what intel8x0 module or AC'97 is. :(

---

### Post by Johan-Steyn on 2009-06-07
Ok,

We know you have a laptop with an Intel chipset.

Your audio is an Intel Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03).

Use gedit or nano to edit the alsa-base.conf file

**sudo gedit /etc/modprobe.d/alsa-base.conf**
 
or

**sudo nano /etc/modprobe.d/alsa-base **

add this at the end of the file and save:

options snd-intel8x0 ac97_quirk=3
options snd-hda-intel model=hp-m4 enable_msi=1

I hope it helps.

Regards,

JS

---

### Post by Sedative on 2009-06-07
After I put gedit or nano in the terminal, then what do I do?

---

### Post by Johan-Steyn on 2009-06-07
Hi,

Open the terminal and type or copy & paste the code:

[B]sudo gedit /etc/modprobe.d/alsa-base.conf
[/B]
Enter your login password and wait for the file to open.

Scroll down to the bottom and add the codes:

options snd-intel8x0 ac97_quirk=3
options snd-hda-intel model=hp-m4 enable_msi=1

at the end of the file. Save and exit.

Log in & out and check if it works.

Regards,

JS

---

### Post by Sedative on 2009-06-07
I did it. No sound still.

---

### Post by Johan-Steyn on 2009-06-07
Hi,

What make / model of laptop do you have?

Also, try one last thing for me. Also add the following two lines at the end of the **/etc/modprobe.d/alsa-base.conf** file:  

options snd-hda-intel model=3stack-dig
options snd-hda-intel single_cmd=1 			 		

And restart.

Thanks 

JS

---

### Post by Sedative on 2009-06-07
I have a HP Pavilion Entertainment PC

And

```
bash: /etc/modprobe.d/alsa-base.conf: Permission denied
```

---

### Post by Johan-Steyn on 2009-06-07
Hi,

This is a common problem with the HP Pavilion.

Sorry I forgot to mention, you have to put sudo in front, i.e:

**sudo gedit /etc/modprobe.d/alsa-base.conf** 

Regards,

JS

---

### Post by Sedative on 2009-06-07
It worked. I put the rest on the end and I'm going to restart now.


EDIT: OMG THE MUSIC WORKS!!! I thank you oh so very very much!

EDIT 2: Except the music is pretty quiet and all my settings are at 100% volume. :(

---

### Post by Johan-Steyn on 2009-06-07
My pleasure!

Regards,

JS

---

