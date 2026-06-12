---
title: "[SOLVED] installing new hardware."
date: 2009-01-04
forum: New to Ubuntu
---

### Post by MickAld on 2009-01-04
Hi again, I am really enjoying learning all I can about Ubuntu and have been trying out various bits and pieces over the last week or so. However today I decided to upgrade my computer with some new hardware hoping that because it was pci based it would be automatically detected. One was a sound card and the other was a pci-usb card. Unfortunately I can not make head nor tail of the driver requirements even though the box for the sound card says it is linux supported. This is an xwave-7000 5.1 channel Audio card. Anyone know what i am supposed to do please? Pretty Please.:confused:

PS, When I plug devices into the usb card (eg a flash drive) it (the flash drive) indicates power is there but the computer sits there totally unconcerned.

---

### Post by kestrel1 on 2009-01-04
post the result from 
```
lsusb
```

---

### Post by MickAld on 2009-01-04
Hi Kestrell, it took me a minute or two to work out what you meant, I hope this is it.

mick@mick-desktop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 03f0:0b0c Hewlett-Packard 
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
mick@mick-desktop:~$

---

### Post by MickAld on 2009-01-04
Actually I decided it might be better if I resubmitted this with devices plugged in to all the ones I know work. These were the original usb connectors that came with the computer.

mick@mick-desktop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 03f0:0b0c Hewlett-Packard 
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 017: ID 1307:0165 Transcend Information, Inc. 
Bus 004 Device 016: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
mick@mick-desktop:~$

---

### Post by ranch hand on 2009-01-04
Have you disabled the intigrated sound manager in BIOS?  I recently installed an Audigy 5.1 card.  Works great but only if BIOS is trying to use it.

---

### Post by MickAld on 2009-01-05
Still not having much success but what I found somewhere was an instruction to do this line in Terminal.

mick@mick-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

All very good but what does it tell me? BTW thx for all previous replies. Ranch Hand what does it mean when my BIOS tells me that under audio it is set to auto?

---

### Post by theozzlives on 2009-01-05
If you have a sound card on the motherboard, disable it... it's conflicting with your new card. Try on of your built in USB ports and see if Ubuntu mounts your flash drive.

---

### Post by kestrel1 on 2009-01-05
If the sound is set to auto in the BIOS it should disable itself if it detects a sound card, I suspect this is not happening, so you need to turn it off or disable it.
What is the output from:
```
lspci
```
Type the above in a terminal.

---

### Post by MickAld on 2009-01-05
This is the output Kestrel. Does this help? 

mick@mick-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 USB Controller: NEC Corporation USB (rev 43)
00:08.1 USB Controller: NEC Corporation USB (rev 43)
00:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

---

### Post by MickAld on 2009-01-05
I also went into the bios and set audio under 'Integrated Peripherals' to disabled. Unfortunately nothing happened from the sound card. Usually I get a boot sound both when the log-in screen appears and when I get to the desktop. Nothing!

---

### Post by MickAld on 2009-01-05
PS to lspci, the 1.1 USB card is an old one I plugged in to see if it was recognised, it will be out of the machine before I finish upgrading. Thing is when I plug a flash card in there it works, ie recognises the device and the files stored. Very frustrating innit?

---

### Post by kestrel1 on 2009-01-05
So is the new USB card plugged in when you run the lspci command?
I was assuming that the 1.1 was the onboard & that the NEC was the card, guess I was wrong. I am now assuming that the NEC is the onboard.
It looks like you have two sound cards installed, did you run lspci before disabling the onboard in the BIOS?
If so can you run it again with the onboard disabled.
I know this sounds silly, but are you sure that the speaker cable is plugged in the new card correctly?
One more thing you could try is to run the live CD & see if the sound card & USB card work correctly.

---

### Post by ranch hand on 2009-01-05
In my BIOS I have a listing for an onboard sound manager with three options:
Off
Auto
On

On means that the intigrated card will be used no matter what.
Auto is supposed to mean that it will use another card if it is pressent.  It would not.
Off turns off the intigrated crap (sounded like a 60s transistor radio).

What you have done sounds like it should have fixxed it.

Have you right clicked on the volumn applet and opened the controls and checked what switchs are set.  That may be the seat of your problems.  Make sure, if you have one, that the didgetal output jack is OFF.  On my audigy card that makes for really irritating noise.  have no idea why it is even there.

Another thing may be that you are using the same speakers as went with the intigrateted manager.  You probably need powered speakers.

---

### Post by MickAld on 2009-01-05
Trying to deal with one thing at a time now, I have removed the 'new' usb2 card, I moved the sound card to that PCI slot and put the usb1.1 card in where the sound card was. I know it sounds daft but when I tried to get the new usb card out it was a half height thing and I couldn't get at it. So I had to remove the other cards so that I could remove it without damaging it and other hardware close by. The way I have it arranged now my new video card (not yet, lol, I am having enough trouble with the usb and audio) situated in its oown slot, then I have the sound card in the PCI slot next to that, then the 1.1 usb card. Now I hope that I can easily swap the usb cards without having to keep disturbing the other cards. Anyway, remember I have onboard usb 2.0 slots, plus this 1.1 card in pci and this is my lspci result below

mick@mick-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

There seems to be no reference to the NEC USB now. Perhaps that is the new one (now removed). That being the case, I presume that the card is recognised by the system but things don't automatically mount. Is this likely and if so, how do I fix that?

Again many thanks for all your suggestions. I really do appreciate your time and effort.

---

### Post by MickAld on 2009-01-05
PS, I also just noticed in the new listing that it shows two sound devices, the c-media one (that is the new one but I presume that is a generic name cos the box it came in was xwave) and the other one is the VIA technologies one that came with the computer. Now I think we are close to resolution if I can de-activate the onboard one and activate the new one. Whhhoooooo!

---

### Post by kestrel1 on 2009-01-05
What make & model is the new sound card?
From what I can see there are two entries for audio controllers:
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

Are you sure that the onboard audio is disabled?

---

### Post by MickAld on 2009-01-05
I have now removed the 1.1 usb card and replaced it with the new 2.0 card and this is the result after lspci

mick@mick-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 USB Controller: NEC Corporation USB (rev 43)
00:09.1 USB Controller: NEC Corporation USB (rev 43)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
mick@mick-desktop:~$ 

Hello hello hello? Why is the 1.1 usb still there? Could it be that the onboard is 1.1 only?

---

### Post by kestrel1 on 2009-01-05
I would suspect that to be the case as it is a VIA tech, as is the mobo chipset. Although there is reference to a VIA tech USB 2.0 as well.
What make Model is your mobo?
Have you disabled the onboard audio yet?

---

### Post by MickAld on 2009-01-05
I have just figured out this quick reply business lol. New websites are a minefield until you get used to it. Right, I do appear to have two audio cards and at the moment I have not disabled the original because I tried it earlier and got no sound at all, so I reverted to auto. The bios only allows me two choices, auto or disabled. 

The new sound card is an xwave-7000 and on the box it says it is dos, windows and linux supported. Unfortunately there is only a brief handout on installing windows drivers. Chipset is c-media cmi-8738/pci-6hc with 16 bit codec.

---

### Post by MickAld on 2009-01-05
Well now I have plugged in my flash drive to the usb 2.0 card and it registers (mounts) automatically.I got quite brave then and plugged in my accessories via a hub and they all mount as well so it seems it might have been resolved. I have an external hard drive, a printer/scanner and a second dvd drive. all work now and I am over the moon. Now I can attend to the audio card.

---

### Post by MickAld on 2009-01-05
I have disabled the onboard sound system and as you advised I have added an external powered speaker system rather than the ones in my monitor. Thanks again for your advice and help. I am somewhat relieved and delighted that it has all been resolved through the forum.

---

### Post by MickAld on 2009-01-05
It would seem that all of these issues have now been resolved. Many thanks once again to all those who contributed with different ideas and I very much appreciate all of this assistance. Hopefully one day I will be able to provide assistance to other newbies (but not yet eh?) 

The sound issue has been resolved by the use of an external (powered) speaker system. 

The USB 2.0 card now works not only with individual devices but multiples through a hub. Chuffed? Youbetcha!!!

---

### Post by kestrel1 on 2009-01-06
I think the only way to resolve the audio card problem will be to disable the onboard until the new one is sorted.
I am assuming that you are plugging the speaker cable in to the correct port on the new card? I know that sounds silly, but you should see the things I have in the past.

---

### Post by ranch hand on 2009-01-07
I hope you mark this thread as solved.  Just go to the thread tools at the top of the page.

That way this may help someone else.

It feels good to get the stuff working for sure, that's great.

---

