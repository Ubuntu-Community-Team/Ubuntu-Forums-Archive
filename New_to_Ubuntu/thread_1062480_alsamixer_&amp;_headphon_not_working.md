---
title: "alsamixer &amp; headphon not working"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by crowhill on 2009-02-06
hi there

i have a fresh ubuntu 8.10 install running on my dell xps m1330. unfortunately, i'm not able to get my audio properly working. this shows up when i want to make a call with skype. i checked this forum but the solutions assume that alsamixer is properly working. however, it seems to me that this is where my problem is. namely, i only get to see a hand full of switches and no microphone switch in particular. please, see the attached screenshots of what i can play with in alsamixer. what is wrong here?

some advice and help would be very much appreciated.

cheers,
crowhill.

---

### Post by kostkon on 2009-02-06
Your *alsamixer* is working alright, these are just the *PulseAudio* volumes. I assume that you want to access the volumes of your hardware. To do it, run *alsamixer* like this:
```
alsamixer -Dhw
```

---

### Post by kostkon on 2009-02-06
As fas as *Skype* is concerned, you need to go to its audio preferences and set the *Sound Out* and *Ringing* options to the *pulse* device.

---

### Post by crowhill on 2009-02-06
> **kostkon said:**
> Your *alsamixer* is working alright, these are just the *PulseAudio* volumes. I assume that you want to access the volumes of your hardware. To do it, run *alsamixer* like this:
```
alsamixer -Dhw
```

great, thx a lot for that. one step further. now the problem is that the solution suggested in [http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16) doesn't work as my mic switch cannot be increased. see the attachments for that. what do i have to change here? i don't really know what that stuff in alsamixer is for.

thx in advance,
cheers,
crowhill.

---

### Post by crowhill on 2009-02-06
> **kostkon said:**
> As fas as *Skype* is concerned, you need to go to its audio preferences and set the *Sound Out* and *Ringing* options to the *pulse* device.


thx for that too :)

i tried it but it's not working. i can't hear myself. i guess, this i because the mic is on 0 (see the pictures above.

---

### Post by kostkon on 2009-02-06
> **crowhill said:**
> great, thx a lot for that. one step further. now the problem is that the solution suggested in [http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16) doesn't work as my mic switch cannot be increased. see the attachments for that. what do i have to change here? i don't really know what that stuff in alsamixer is for.

thx in advance,
cheers,
crowhill.
First of all, this how-to is too general since every audio hardware device has different volumes and with different names.

I can see that your volume levels are fine and I can see that in playback view you have set your mic volume to 0. That's just fine. You'll now not hear yourself from the speakers.

> **crowhill said:**
> thx for that too :)

i tried it but it's not working. i can't hear myself. i guess, this i because the mic is on 0 (see the pictures above.
No, you made a mistake. You need to set the *Sound In* option to your sound card/microphone and not *pulse*.

Or leave it like this and then install the *PulseAudio Device Chooser* and set your soundcard that has the microphone input as the default input device.

I recommend you, for the moment, to do the first option, just set *Sound In* to your soundcard.

Also, to be sure, make sure that in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) you have your sound playbacks set to *Autodetect* and your sound inputs to your soundcard's microphone.

---

### Post by crowhill on 2009-02-07
here is what **lspci** gives me

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


which is my soundcard?

using the skype settings indicated in the above screenshot (3 times pulse) i can hear myself now in skype. in alsamixer, i mutet the mic (where it said zero) and changed digital to digital, rather than analog (see the screenshot). i can also hear myself changing the in device to HDA Intel (hw:Intel,0) in skype. 

however, in each case, the volume is extremely low. it is also very low if i watch movies. under windows, i used to be able to get much higher volumes. it seems, i can't push the L-R-capture switch higher than to 43% (see the same screenshot).

puzzled!

i had ubuntu 8.04 running it skype worked better in regard of the volume (i have no idea how i got skype running under 8.04). movies worked better to.

i think, i have a good soundcard (soundblaster?) but ubuntu might not be able to see/detect it?

---

### Post by kostkon on 2009-02-07
> **crowhill said:**
> here is what **lspci** gives me



which is my soundcard?

using the skype settings indicated in the above screenshot (3 times pulse) i can hear myself now in skype. in alsamixer, i mutet the mic (where it said zero) and changed digital to digital, rather than analog (see the screenshot). i can also hear myself changing the in device to HDA Intel (hw:Intel,0) in skype. 

however, in each case, the volume is extremely low. it is also very low if i watch movies. under windows, i used to be able to get much higher volumes. it seems, i can't push the L-R-capture switch higher than to 43% (see the same screenshot).

puzzled!
*Skype*'s working, that's good. As fas as the volume being low, check again every volume level in *alsamixer* (don't forget to press F4 to see the rest). You can do it from a GUI if you want (if you find it more straightforward), just right click on the speaker icon in your system tray and select *Open Volume Control...*

From there you will more or less have the same volume levels available. If not, to add more, just *select Edit &#8594; Preferences*.
> **crowhill said:**
> i had ubuntu 8.04 running it skype worked better in regard of the volume (i have no idea how i got skype running under 8.04). movies worked better to.
Eh, yeah, sound in 8.04 works a little differently. In 8.04 *ALSA* sounds don't pass through *PulseAudio* whereas in 8.10 they do.
> **crowhill said:**
> i think, i have a good soundcard (soundblaster?) but ubuntu might not be able to see/detect it?
It will work fine, I think. You will be able to easily set it as the default card using the *PulseAudio Device Chooser* utility.

Which model is it?

---

### Post by crowhill on 2009-02-07
thx a lot 4 your help. this is extremely much appreciated.

i played a bit with the switches in the gui for alsamixer. basically, i have all of them on maximum. the volume though is still very low.

my sound card: sound blaster audigy advanced mb creative

---

### Post by kostkon on 2009-02-07
> **crowhill said:**
> thx a lot 4 your help. this is extremely much appreciated.

i played a bit with the switches in the gui for alsamixer. basically, i have all of them on maximum. the volume though is still very low.

my sound card: sound blaster audigy advanced mb creative
That's unfortunate. But the audigy should work out of the box, if you decide to use it.

Could you elaborate a little more on this:
> **crowhill said:**
>  and changed digital to digital, rather than analog
Also, have you found any other switches that you can set on/off? Did you tried them?

---

### Post by crowhill on 2009-02-07
regarding the "digital":
please, see the screenshots. i changed the yellow term above "digital" from "analog" to "digital".

regarding the sound card:
as i already mentioned, my sound worked better when using ubuntu 8.04. however, even there i thought that with windows things were better as i could get higher volumes. don't i need some special, additional driver for a sound card like that? do you think a reinstall would do the trick? i wouldn't mind doing it if the sound works afterwards.

regarding the switches:
i played with all of them a little bit, not systematically though as it is a bit annoying. see the sreenshot for the things that belong to the "recording" group. if i click on the little microphone i can turn them off or on.

---

