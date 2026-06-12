---
title: "Alsa and subwoofers"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by sparkplug619 on 2010-08-03
Hello. I just finished installing my realtek alc883 sound driver after a long day of searching and troubleshooting.

I finally have sound on my computer. My problem now is I only have one channel working so the only way I can use my subwoofer is through the same channel as my speakers which sounds so crappy.

I want to know if there is anyway to get my subwoofer to work in its own channel? I should have 3 channels. 2 out and 1 in. Im not sure if the 'in' channel is working either but I dont need it anyway.


Btw, I am still learning linux, I believe im a step up from a beginner but still have alot to learn, just to break the ice.

---

### Post by ubunterooster on 2010-08-03
See the[ Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") to properly set up the audio.

---

### Post by sparkplug619 on 2010-08-03
> **ubunterooster said:**
> See the[ Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") to properly set up the audio.


I was able to get the subwoofer to work. The last step is to set it up for low-pass only.

I didnt have much use for the link, but thank you

---

### Post by sparkplug619 on 2010-08-04
> **sparkplug619 said:**
> I was able to get the subwoofer to work. The last step is to set it up for low-pass only.

I didnt have much use for the link, but thank you


Anyone know of a way to get my sub to only play low pass?

Ive been reading for hours with not much luck

---

### Post by sparkplug619 on 2010-08-04
My pulse audio no longer works correctly... im getting so fed up with this

---

### Post by sparkplug619 on 2010-08-04
problem solved... My pulse audio works correctly. My sub has a low pass filter. 

But now, when I play music in Amarok, after every 3 or 4 songs the audio breaks and I have to restart alsa and pulse audio.

---

### Post by sparkplug619 on 2010-08-05
> **sparkplug619 said:**
> problem solved... My pulse audio works correctly. My sub has a low pass filter. 

But now, when I play music in Amarok, after every 3 or 4 songs the audio breaks and I have to restart alsa and pulse audio.


Anyone know why my audio breaks when I change songs?

---

### Post by simosx on 2010-08-05
You need to provide detailed hardware information about your sound card; it's possible that the sound card is not supported well. Another issue is to check that you have the latest BIOS update installed (it's strange, though it can affect sound as well).

Run

wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

When prompted, allow to send the details to [www.alsa-project.org](www.alsa-project.org) and post the resulting URL here. You can read more on this at the Ubuntu Sound Troubleshooting Wiki.

---

### Post by sparkplug619 on 2010-08-05
This is the url I got

[http://www.alsa-project.org/db/?f=32070547587f5bdde954f928099c13fff0907b78](http://www.alsa-project.org/db/?f=32070547587f5bdde954f928099c13fff0907b78)

---

### Post by sparkplug619 on 2010-08-06
I created a /proc/asound/cards file like it said in the troubleshooting guide and added my card as the top priority (0) and now my sound card is not recognized. I deleted the file and rebooted my computer and it still is not recognized. Im back at square one. Im thinking a complete wipe of everything alsa related and a reinstall is necessary about now. Im creating more problems than I am fixing

---

### Post by lidex on 2010-08-06
What is the make model of your PC/Laptop? If you assembled it, what is the motherboard model? Can you post this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by sparkplug619 on 2010-08-06
> **lidex said:**
> What is the make model of your PC/Laptop? If you assembled it, what is the motherboard model? Can you post this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```


I built my computer myself using an Asus M2A.VM (no HDMI) motherboard. 

The onboard audio is Realtek Alc883.

For "sudo dmidecode -t bios":

```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: ASUS M2A-VM ACPI BIOS Revision 2201
    Release Date: 10/22/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x002D, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

```for the last one i get:

```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M2A-VM
    Version: 1.XX    
    Serial Number: 123456789000


```

---

### Post by sparkplug619 on 2010-08-06
THIS IS WHAT I GOT AFTER BIOS UPDATE


first one:

```

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: ASUS M2A-VM ACPI BIOS Revision 5001
    Release Date: 02/04/2010
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x002D, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1


```
second one:

```

# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M2A-VM
    Version: 1.XX    
    Serial Number: 123456789000

```

---

### Post by sparkplug619 on 2010-08-06
I may have found a potential problem. I just uninstalled everything alsa related and when I was reinstalling it, I just used a driver I got from the realtek website and never actually chose my own. I followed a guide on here and installed my correct driver, Im now just waiting for it to finish up to see if it solves most of my problems or not.

---

### Post by sparkplug619 on 2010-08-06
Well I reinstalled alsa with my correct driver but now, like before, im only getting sound out of 1 audio jack. The method I used to get both to work last time didnt work this time

---

### Post by lidex on 2010-08-06
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-6ch 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. On the output tab choose the correct device.

---

### Post by sparkplug619 on 2010-08-06
Oh man your great.. it works perfectly! Thank you so much!

It seems to have combined the front channel with the sub though so the sub is still putting out all audio and not just lowpass.

When I did a speaker test, the sub and the speakers play on front-left and front right and nothing else. maybe an asoundrc file can fix this?

---

### Post by sparkplug619 on 2010-08-07
Ok Im soo close. In 'sound preference' I am able to control the fade and the subwoofer volume all in one. Ive never been able to do this before.

The problem now is that the adjusting the subwoofer knob negatively affects the front speakers. When lowering it, it leaves a very low screechy sound.

My asoundrc file looks like this

```


       pcm.hda-intel {
          type hw
          card 0
       }
       
       ctl.hda-intel {
          type hw
          card 0
       }


pcm.upmix_20to51 {
    type plug
    slave.pcm lowpass_21to21
    slave.channels 3
    ttable {
        0.0     1       # left channel
        1.1     1       # right channel
        0.2     0.5     # mix left and right ...
        1.5     0.5     # ... channel for subwoofer
    }
}

pcm.lowpass_21to21 {
    type ladspa
    slave.pcm upmix_21to51
    path "/usr/lib/ladspa"
    channels 3
    plugins {
        0 {
            id 1098 # Identity (Audio) (1098/identity_audio)
            policy duplicate
            input.bindings.0 "Input";
            output.bindings.0 "Output";
        }
        1 {
            id 1672 # 4 Pole Low-Pass Filter with Resonance (FCRCIA) (1672/lp4pole_fcrcia_oa)
            policy none
            input.bindings.2 "Input";
            output.bindings.2 "Output";
            input {
                controls [ 300 2 ]
            }
        }
    }
}

pcm.upmix_21to51 {
    type plug
    slave.pcm surround51
    slave.channels 6
    ttable {
        0.0     1       # front left
        1.1     1       # front right
        0.2     1       # rear left
        1.3     1       # rear right
        0.4     0.5     # center
        1.4     0.5     # center
        2.5     1       # subwoofer
    }
}


```

---

### Post by lidex on 2010-08-07
Not my area of expertise but maybe you can get some ideas from the System-Wide Equalizer section here:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Asoundrc here:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)

---

### Post by sparkplug619 on 2010-08-08
everytime I restart my computer, the sub stops working

---

