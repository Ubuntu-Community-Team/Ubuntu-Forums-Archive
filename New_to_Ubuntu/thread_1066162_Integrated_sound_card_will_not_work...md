---
title: "Integrated sound card will not work.."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by kingchipo on 2009-02-10
ive got no sound on my intergrated sound card i really need help and im pretty new to linux

Does anyone have any help on the subject?


running ubuntu 8.10

---

### Post by adam_kimber on 2009-02-10
Wheeee. Soundcards. Right then. Excuse me if I am a little condescending, I am not sure of your level of Ubuntu knowledge. 

First off. What type of machine is it, laptop or desktop? Shouldn't make much difference but there is more chance of a proprietary sound card which is more difficult to setup in a laptop than a desktop.

I have assumed desktop for now. 

Secondly, we need to know whether your soundcard is USB or PCI based. This will allow us to select the appropriate driver:

These things are easier to do in a terminal.  (hope this is not too scary ;) )

Can you open a terminal (Accessories --> Terminal) and type the following 

```
lspci
``` 

This should list all your PCI devices (ls means list, literally list PCI!)

Below is the results for mine (I have filtered my results using GREP and PIPE which I can explain if you want) 

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

Next the USB devices.......

```
lsusb
``` 

Same syntax as before.....Heres mine..

```
lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 006: ID 045e:0719 Microsoft Corp. 
Bus 004 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

From this information we should be able to get your card working.

---

### Post by kingchipo on 2009-02-10
Thank you so much my results from the terminal

```
00:00.0 Host bridge: Intel Corporation 440GX - 82443GX Host bridge
00:01.0 PCI bridge: Intel Corporation 440GX - 82443GX AGP bridge
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)
```

Thats for the first command 

And for the second

```
Bus 001 Device 003: ID 04b3:310c IBM Corp. 
Bus 001 Device 002: ID 04b3:3025 IBM Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by kingchipo on 2009-02-10
oh and i forgot to mention i have a very wierd sound card its not pci the plug is longer than a pci but my intergrated soundcard will not work either so far i cannot get niether of them to be detected

Oh and yes its an older model dell made in about 2000

---

### Post by adam_kimber on 2009-02-10
The next question might sound weird. Are you sure you have a sound card. It is not listed here........

---

### Post by kingchipo on 2009-02-10
Well This external sound card i got is awfully wierd 

But yes im sure i have intergrated sound card that isnt displayed i see speaker jacks i/o on the back of the motherboard. 
I would rather just get the intergrated soundcard to work because the external isnt neccesary

---

### Post by adam_kimber on 2009-02-10
Correct me if I am wrong you have two sound devices in your machine? One plugs into the long slot (which I assume is ISA - wow I have never used ISA under Linux :D) and two the onboard. 

I would say that most likely they are clashing. Whichever you want to get working do the following.

1) For the ISA card - disable the onboard in the BIOS and then run those above commands again!

2) Pull out the ISA card. Reboot and run those above commands again!

---

### Post by kingchipo on 2009-02-10
Ill go with the onboard sound card im pulling out the "isa" and rebooting now give me one second:)

---

### Post by kingchipo on 2009-02-10
OK instead of going with my gut i turned the onboard off in the bios and went with the isa sound card which still isnt showing...

Im going to now try to remove the isa and turn the onboard back on..

one sec!

---

### Post by kingchipo on 2009-02-10
Ran the command and still cant find anything...

my output was 

```
00:00.0 Host bridge: Intel Corporation 440GX - 82443GX Host bridge
00:01.0 PCI bridge: Intel Corporation 440GX - 82443GX AGP bridge
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)
```


i dont understand....

---

### Post by kingchipo on 2009-02-11
anyone have any ideas?

---

### Post by adam_kimber on 2009-02-11
Do you know the make and model of your motherboard. From that we can find out what the onboard sound chip is and try a different approach.

I still think there might be a conflict of hardware as by all rights it should show up in lspci or lsusb unless the onboard sound is configured as an ISA card. Then method one is the only way to find out what it is........

---

### Post by kingchipo on 2009-02-11
Alright i found a problem

i am getting a plug and play configuration error message at boot up with the onboard sound card enabled i disabled it and put my isa card back in..

---

### Post by cjv8888 on 2009-02-11
Please post the following to see if it can give you some more ideas:

```
aplay -l
```

```
lspci -v
```

---

### Post by kingchipo on 2009-02-11
> **cjv8888 said:**
> Please post the following to see if it can give you some more ideas:

```
aplay -l
```

```
lspci -v
```

for the first command 

aplay: device_list:215: no soundcards found...


and for the second command i get no sound card on the list

---

### Post by adam_kimber on 2009-02-11
Do you know the name and make of the plug in card? ;)

---

### Post by kingchipo on 2009-02-11
The plugin card is a really old card i forget model make and name 

Ive switched back to the onboard and now have what seems like sound (my headphones have a loud background noise now) but still cant play any sound

I did some googling and figured out this dell desktop has a crystal chipset so i added a command to some module file to load the module on boot and i think im getting somewere

oh and i also here beeps while in the terminal through my speakers now

But my output for aplay -l is still no soundcards

---

### Post by kingchipo on 2009-02-11
aplay -l still shows no sound cards 

But i can hear background noise/static and can hear beeps while in the terminal through my headphones....


any ideas?

---

### Post by adam_kimber on 2009-02-11
Static you say. That sounds like a wrong driver. What does sudo lshw -c multimedia print out?

---

### Post by kingchipo on 2009-02-11
The command prints out

PCI (sysfs)

Also 

dmesg | grep isapnp


says that my chipset is 

cs4236

i run 

sudo modprobe snd-cs4236

And that gives me the static and beep sounds through my headphones also my gnome volume controller has a red x beside it...

---

### Post by adam_kimber on 2009-02-11
Try adding this to /etc/modules and rebooting,,,,,,,,

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

---

### Post by neu2buntu on 2009-02-11
maybe have a look at all the blacklist files in ```
/etc/modprobe.d/*
``` maybe your driver is automatically blacklisted?

---

### Post by t_k_majumdar on 2009-03-30
> **adam_kimber said:**
> Try adding this to /etc/modules and rebooting,,,,,,,,

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

Hi adam_kimber -

I installed ubuntu 8.10 on my old but still wonderfully working Dell Optiplex GX1 computer and facing the same problem of getting no sound after instalation from the onboard sound card cs4236B. After a Google search, I came across the same solution as you suggested here. Implementing this gave me some beeps if I try some unpermissible action (e.g. pressing the Right arrow in terminal).How to proceed further? Or, Should I wait for the release of ubuntu 9.04 due on April,23,2009?

Few relevant points : I can't configure my wireless modem in ubuntu so I can connect to the net through other os only. My experience in ubuntu is 3 days only.

---

### Post by adam_kimber on 2009-03-30
Unfortunately as I have not got a Dell Optiplex we will have to do some remote diagnosing. 

1) First up are the beeps coming from your internal speaker or plugged in external speakers? 

2) Please go to System--> Administration --> System Log, it might ask for your password. Then click on messages. This is just a GUI to the log files. Messages is very useful for diagnosing problems. Copy from a line like the one below down to the end put in a text file and attach. It will be LONG. :) This will ahve copied all the boot messages. 

```
Mar 29 21:26:51 zia kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
```

3) Please go to System--> Administration --> System Log, it might ask for your password. Then click on Xorg.0.log.  The xorg log is useful for working out whether sound / video is working properly in the x-windowed environment that Gnome/KDE uses. 

What I will be doing for 3) is looking for (EE) and (WW) flags. I.e. errors and warnings.

---

### Post by t_k_majumdar on 2009-03-31
Dear adam_kimber -

Thank you for your helping gesture. It also raised hope of solving this problem. 

1) Sounds are coming from the external plygged-in speakers.

2) I have created files of messages and xorg files but failed to attach them as their sizes exceed the permissible limits. I am trying to overcome this difficulty, but please give me some time.
Can I paste them in pastebin or nopaste.com?

3) I found that: on search "Messages" file showed "cs4236" in several areas while xorg file did not showed it, or "sound" or "snd" in any area.

t_k_majumdar

---

### Post by bobpur on 2009-03-31
I'm not poking fun or trying to insult anyones intelligence but a volume icon with an "X" means it's muted isn't it?

Also, check your volume controls and mixer. Just a thought.

---

### Post by dspisak on 2009-03-31
Hello.  I also have the same problem with the on-board sound device.  The MB is an Asus M3A78-T.  I am running 8.10 , kernel 2.6.27-11.  There is no ISA or PCI card installed.  Running several commands returns:

spisaks@djs-pc:~$ sudo lshw -c multimedia
[sudo] password for spisaks: 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: RS780 Azalia controller
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
  *-multimedia UNCLAIMED
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
spisaks@djs-pc:~$ sudo dmesg | grep isapnp
spisaks@djs-pc:~$ sudo dmesg | grep pcipnp
spisaks@djs-pc:~$ sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
spisaks@djs-pc:~$

Also, lspci -v shows that no kernel modules are associated with the audio device.  The driver or kernel module should be snd-hda-intel.  It is found in /lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/.

I've followed the instructions in "Comprehensive Sound Problem Solutions Guide" and "Interpid Sound Solutions" several times and still no sound.  If I boot to kernel 2.6.27-7 I have sound.  Is it possible to re-install module -11? (FWIW, while kernel -7 has sound it will run only in low resolution mode.  Kernel -11 can run at 2048x1152.)

Any help is appreciated.

Here is my system:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.18 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia and/or ATI Technologies Inc SBx00 Azalia (Intel HDA)

4/6/09 edit: The problem is solved.  I followed soundcheck's instructions on the "ALSA Upgrade Script" thread and re-installed ALSA.  I did not have to re-install either ubuntu or the kernel.  The video was not affected.

---

### Post by t_k_majumdar on 2009-04-02
Hi adam_kimber - 

Enclosed please find the system messages and xorg log files (zipped) as requested by you.

Looking for your comments and assistance.
----------------------------------------------------
Well, I don't dislike "Kinetic Kiwi" as the nickname for ubuntu 9.04.However, being from Bengal, I shall be glad to call it "Roaring Tiger".

---

### Post by filmdc on 2010-02-26
Hi,

My sound works alright by default, using the on-board soundcard. The problem I'm having is I cannot hear my inputs, through my output. My input 1, mic 1 and mic 2, all receive the input fine, and I can tell because volume meters show activity, but I can't hear anything through the mixer's output.

My motherboard is m2n-sli deluxe, with the nvidia nforce 570sli chipset. the audio is ad1988b.

I've followed a few different guides, including the comprehensive sound problem solutions.

My problem isn't that I can't hear audio if I play it directly from my OS, it's that I can't listen to inputs, despite clearly having good signal flow, etc. 


I have it set on Analog Stereo duplex, and I've tried all of the other variations with no joy. Can anyone help me out? I'm a newbie to the linux scene, but I'd like to work on getting my onboard sound completely functional, inputs and all.


**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
______________________________

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 81f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


_____________________

I recently ran alsamixer, made sure my volumes were correct, and the started sound recorder. Sound recorder did record the input line! I can't hear it unless I play back a recording of it, but it is definitely there. i want to listen to the input. Thats where I'm at. How do i configure the sound card and software to send the input sound out of the output?

______________________

Hey, I just got this to work!

On a fresh Ubuntu Karmic Koala I installed libao2 (searched alsa in the synaptic package manager) after installing the ALSA Mixer from the software center.

I loaded up the graphical interface Applications>>Sound and Video>>ALSA Mixer

and it showed me pretty much what you can see in the terminal version of the alsa mixer

except over the input sliders, there were two little buttons. i clicked them off, and  suddenly my input came in clear as day. 

did the terminal version of the alsa mixer have these option hidden, or is the graphical version just more prepared?

im not sure if the libao2 has anything to do with anything as of the moment. will get back to this.

---

### Post by UnicornsRock420 on 2010-03-05
Currently running Karmic Koala -
I tried all this [http://ubuntuforums.org/showpost.php?p=8892809](http://ubuntuforums.org/showpost.php?p=8892809) , building the driver/plugins/libs/etc.

```
Prompt: aplay -l
aplay: device_list:223: no soundcards found...
Prompt: sudo cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC1200
Prompt: sudo lshw -class sound
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
Prompt: uname -a
Linux Host 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

There's the slightest faint with the volume cranked sound in amarok and VLC and everything else is dead. The Mixer appears to be working fine, tried installing/uninstalling pulseaudio package, running alsaconf, no change.


I'm out of ideas here...

---

