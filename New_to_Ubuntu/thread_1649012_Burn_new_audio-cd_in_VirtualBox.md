---
title: "Burn new audio-cd in VirtualBox"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by MrQuincle on 2010-12-19
Dear all,

First, there are many solutions for **mounting** .iso files, from mount, to furiusisomount, to gCDEmu. What I am searching for however is something that emulates a CD/DVD **writer**.

This would enable me to start VirtualBox with a blank CD/DVD in the drive. It would enable me subsequently to start Windows Media Player and burn DRM protected WMA files of my girlfriend's lost MP3 player to this simulated medium, give her her music back and make her day, or even month.

The cdemu people say they emulate burning, but on my system there is no option to actually create an empty medium. Something like brasero, or other burning software is of course not any solution either. 

Thanks in advance!

---

### Post by PhantmKllr on 2010-12-19
I'm not sure that this is possible. However, you could try to burn directly to your physical DVD/CD drive from VirtualBox.

---

### Post by Chesamo on 2010-12-19
Check the box next to "Passthrough" in the Storage Device settings, and you can burn to a real blank disc.

I don't think there's anything that can create, mount and burn a fake blank disc.

You can also use a system called FairUse4WM to strip the DRM off the WMA files, which I won't link here (but a guide that uses is can be found [here](http://www.instructables.com/id/Convert-DRMed-WMA-files-to-Usable-MP3s/)). This seems the more elegant solution.

---

### Post by Joeb454 on 2010-12-19
Enabling passthrough still won't work from what I've seen. See the attached image from the VirtualBox settings dialog (paying particular attention to the bottom of the window)

---

### Post by MrQuincle on 2010-12-20
Thanks all for the answers, but burning to a real CD is what I wanted to avoid...

---

### Post by Joeb454 on 2010-12-20
Ah, I seem to have misread your question, so what you want is to burn an audio disc to a file, essentially? Which could then (in theory) be burnt to a real disc if needs be?

---

### Post by MrQuincle on 2010-12-25
> **Joeb454 said:**
> Ah, I seem to have misread your question, so what you want is to burn an audio disc to a file, essentially? Which could then (in theory) be burnt to a real disc if needs be?

The thing is that it's easy to get the songs from an audio disc, be it real or virtual, in mp3 format. So, I can give her her music back. I strongly disagree with illegal practices surrounding music downloading, ripping, etc. This is however her own music, she paid for it, and she should be able to listen to her backupped files I would say... 

So, this is the envisioned trajectory:

Ubuntu -> Create Empty CD (something like gCDEmu) -> VirtualBox (Oracle) -> Get files (shared folder) -> Windows Media Player -> Mount virtual audio CD -> Burn audio CD -> Store ISO (shared folder) -> Rip in usual way.

I can't find a program that emulates **writing** CDs. So the second steps fails, all the others will work...


================

Steps 1-3 are in a Windows 7 VM.

[1] My approach right now - and it kind of works - is to use a Windows cd-writer emulator. I installed Daemon Tools, PowerISO, NoteBurner, and some others, they do not work, and can only emulate reading. With a shock I realized again that (a) such shareware programs on Windows might be spyware, (b) their source code is not available, so if they are not spyware you have to believe it on face value, (c) they are hard to deinstall, (d) need all administrator rights and a full reboot. I'm lucky that I'm in a VM. Anyway, I came across "**Phantom Burner**", which is able to actual emulate writing. By default it gives you the ability to create an empty audio disk of 50 MB, which amounts to 5 minutes of music. Good enough to test the approach.

[2] In "Phantom Burner" go to the tab "Operations" and choose "Create". You are now allowed to create a "virtual disk image" (VDD file). As said before, this is only good for 5 minutes of music, you have to buy the full version to do more. The program automatically mounts this new created virtual disk in the emulated drive, "G:\" on my system.

[3] You start Windows Media Player and at the burn tab page, you will now be able to go to options and select the right CD drive, you will see that the previously created disk is mounted indeed and will be able to burn in a few seconds. My girlfriend downloaded her music (legally!) with Napster (it still exists) so you will need to install a plugin for that to tell WMP that it indeed concerns properly obtained files. Integration of WMP and Napster sucks, so be prepared to spend a few hours on that.

[4] Now you have a written VDD file and back in Ubuntu you mount it using something like gCDEmu. I'm not aware of the exact differences between ISO and VDD, but gCDEmu is able to open the .cue file that is created alongside the .vdd file. Something like bchunk might help you out in creating ISOs.


Take home message: For DRM related stuff, look at Windows programs. 

Linux people are probably more careful with buying rights alongside their music, and do not need to write emulators to get back what is rightfully theirs.


PS: To make music work in Windows 7 in Oracle VirtualBox, you will need to install the Realtek AC '97 drivers in Windows itself.

---

