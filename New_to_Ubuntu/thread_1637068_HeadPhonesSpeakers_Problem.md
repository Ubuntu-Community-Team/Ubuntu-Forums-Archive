---
title: "HeadPhones/Speakers Problem"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by anweshdbest on 2010-12-04
[FONT=Book Antiqua][SIZE=2]Hey everyone!

I know this problem has been posted several times before but i really need you to help me.

My laptop (Lenovo G560) has Ubuntu 10.10 installed.

The problem is that the sound only comes out from the laptop speakers and continues from there even if i insert the headphone or my Altec Lansing Speakers.

On writing alsamixer in the Terminal,

I get - 

Card - HDA Intel

Chip - Intel IbexPeak HDMI

I have tried editing that file in which we enter 

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```and have tried putting in 

```
options snd-hda-intel model=lenovo position_fix=1 enable = yes 
```Also, my output for lspic in the Terminal is :

```


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```for [/SIZE][/FONT][FONT=Book Antiqua][SIZE=2]cat /proc/asound/version


It returned - "No such file or directory"

[/SIZE][/FONT][FONT=Book Antiqua][SIZE=2]And for cat /proc/asound/cards

```


0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8400000 irq 46

```cat /proc/asound/modules

```


0 snd_hda_intel


```

Can someone please help me out as to what i can do? Step by step procedure PLEASE!

Thank you :)
[/SIZE][/FONT]

---

### Post by anweshdbest on 2010-12-04
Please help!

---

### Post by Penguin=) on 2010-12-04
ok, tell me how to do the code: thingy and i will tell you what you have to do!

---

### Post by anweshdbest on 2010-12-04
To get the code thingy working, just type CODE in rectangular brackets at the start of your text and then type /CODE in rectangular brackets [ ] at the end of it!


Example :-

```
 This is a Code 
```

---

### Post by anweshdbest on 2010-12-05
Really need help! Please....

---

### Post by jmisasa on 2010-12-05
Same here. Any solution?

Thanks.

---

### Post by Penguin=) on 2010-12-05
Have you both downloaded ALL of the alsamixer components from the Ubuntu Software Center OR Synaptic?

---

### Post by LinuxCharms on 2010-12-05
I know on my laptop I have to switch to headphone mode when I plug them in.

You can go to the following to do that:
system>prefs>sound>output>headphones

You'll have to change back and forth when you want speakers and when you want headphones.

---

### Post by Penguin=) on 2010-12-05
You beat me again LinuxCharms, good one!

---

### Post by jmisasa on 2010-12-05
> **LinuxCharms said:**
> I know on my laptop I have to switch to headphone mode when I plug them in.

You can go to the following to do that:
system>prefs>sound>output>headphones

You'll have to change back and forth when you want speakers and when you want headphones.

Nothing. Actually, when I plug my headphones and I have "analog headphones" selected, I can't hear anything on them. Only when I switch to "analog output" I hear the audio in both the laptop speaker and the headphones.

Thank you anyway.

---

### Post by Calais225 on 2010-12-05
Here is a thread with some solutions.

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

There are links from there to other possibilities as well.

and might be some help here:

[http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic](http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic)

---

### Post by jmisasa on 2010-12-05
> **Calais225 said:**
> Here is a thread with some solutions.

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

There are links from there to other possibilities as well.

and might be some help here:

[http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic](http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic)

Thanks. I'll check that out.

---

