---
title: "What a Scare..."
date: 2010-12-20
forum: New to Ubuntu
---

### Post by kaptkan on 2010-12-20
I recently downloaded Ubuntu and created a USB stick with the Ubuntu software on it as instructed. But when I started up the PC, the software was supposed to give me a choice to "try" or "install". I think it started to install... but am not sure... because all of a sudden, it appeared like a DOS menu came up for a second but I could not read it. Then the screen seemed to go blank although the USB was flashing (showing some activity) and I had no indication of what was happening.

I panicked and turned off the PC and pulled out the USB - when I started up, Windows Vista did a recovery. 

I really only want to try this OS first ... not replace my windows until I am sure I find it meets my needs. 

Did I do something wrong using the USB version? There did not seem to be a GUI at the start like the one shown on the Ubuntu installation page.

I may be too naive to be trusted to install this... feel free to tell me so ;)

---

### Post by Hippytaff on 2010-12-20
Hi Welcome and don't panic!

Can you boot into windows? 

Also the install process goes through a number of stages before you actually install it, like choosing to install it over windows or etc etc...you probably (unless you've got some kind of crazy trigger finger) can't install it accidently

---

### Post by unplugged23 on 2010-12-20
If you can still boot into windows just fine, I would say the easiest way to go about trying ubuntu before installing it, would be to download The latest ubuntu cd .iso along side unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))

After you have both of these things, open unetbootin and direct it to your ubuntu.iso, and choose the letter of the usb drive you would like to boot from. Let all of that run through and when it's finished and you've rebooted your computer, provided all of your bios settings are correct and allow the computer to boot from the flash drive, you should be presented with a rather dull looking menu with quite a few options. Make sure you've selected default and continue on and it should take you into the ubuntu live environment, where you can explore the OS before you choose to install it.

Also, there is something called wubi ([http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)). I've never used this before, but I think what it does is allow you to run ubuntu inside of windows, so your not even booting your computer differently than normal.

Best of luck!

---

### Post by amjjawad on 2010-12-20
Problems with Installation and stuff? please check my signature and read the [guide ]("http://ubuntuforums.org/showthread.php?p=10257675")posted there.

Welcome to Ubuntu!

---

### Post by 3rdalbum on 2010-12-20
Ubuntu never "just installs itself". There are always questions that it needs to ask first.

With the normal Ubuntu CD/USB image, it starts up a "live" session of Ubuntu, that runs from the CD/USB. From there, it gives you a window where you can choose to try Ubuntu, or install it. If you click "Install", it asks you a couple of questions first before starting the installation procedure. If you click "Try Ubuntu", it continues starting up the live session.

If you don't click anything, nothing happens.

---

### Post by t0p on 2010-12-20
I think you pulled the plug when the cd was just loading to RAM so you could try it out in a "live" session before making any decision to permanently install.

You really don't need to worry about "accidently" installing Ubuntu when you just want to try it out.  When you install Ubuntu, the installer will ask you questions which you have to answer before installation can begin.  So don't worry about "DOS-like" text and splash screens and stuff.  The live cd takes a few moments before the live session actually starts.  It is *very* unlikely that anything untoward has happened to your current operating sytem.

---

### Post by kaptkan on 2010-12-20
I am not sure, but the USB seems to work away for a while then the monitor just displays a "No Signal" message and I see no activity at all except that the USB flashes for a while... then everything seems to go quiet... and because the HDD is not being used for the boot, there is a very eerie feeling that nothing is happening.

Could there be an issue with Ubuntu and my video card/drivers? I mean, I really should see some sort of indication that something is happening. Eventually even the USB stops blinking.

I downloaded the Ubuntu Desktop ISO file. I then ran the Universal-USB-Installer.

How long should I be waiting for the USB to finally come up with the screen that says "Try Ubuntu"?? I thought after 15 minutes I should at least seem something... other than an indication that the monitor is receiving no signal.

---

### Post by kroq-gar78 on 2010-12-20
Hmm.... I also have the problem of not having a signal. I have 2 monitors, so I decided to turn it off, unplug one, and boot off my flash drive/CD again. When it booted and got to the desktop after saying 'Try Ubuntu', I plugged my 2nd monitor back in and set my desktop to be expanded onto it.

---

### Post by kaptkan on 2010-12-20
Yeah... I only have one monitor. My PC is an HP Slimline ... so the built-in video card may be an issue. Odd tho... because a basic video driver should work.

---

### Post by kaptkan on 2010-12-20
I was able to recover and reboot. I tried the USB again... but again it simply seems to get so far and then the monitor goes blank (indicating No Signal). The USB flashes a couple of times and then stops. As the monitor seems to be shut off, I have no way of knowing if it is doing anything. I just eventually (after 15 minutes) push the power switch and shut the PC off and restart it using Windows to come back into this forum.

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> I was able to recover and reboot. I tried the USB again... but again it simply seems to get so far and then the monitor goes blank (indicating No Signal). The USB flashes a couple of times and then stops. As the monitor seems to be shut off, I have no way of knowing if it is doing anything. I just eventually (after 15 minutes) push the power switch and shut the PC off and restart it using Windows to come back into this forum.

Did you check MD5SUM for the downloaded iso file? step1 in my signature should show you how to do that.

What tools you used to create the LiveUSB?

When you boot up from your LiveUSB, do you see any purple screen with a tiny picture for a man and a keyboard? if yes, press any key, select your language and then "try ubuntu".

---

### Post by kaptkan on 2010-12-21
OK thank you for your input... however, I may be a luddite when it comes operating systems. I know my end products (office tools) but am at a loss as soon as I look under the hood. Please bare with me...

I visited your "Step 1" page...
For the md5sum matter I was about to raise a litany of problems but now realize that reading the whole page, it is important to "read the manual"! I tried executing the Linux instructions... Ooops!

So, once I read and tried the Windows version of the guide on md5sum I got a confirmation that my CheckSums are the same.

**I did notice one interesting thing: **I notice that there is an ISO for AMD64. I downloaded an ISO for i386 ... should I have downloaded and AMD64 ISO??? Oh my - someone take the steering wheel out of my hands before I drive this bus off the road! **Of course... step 1 of your Step1 file tells us to read the manual... **I suppose you are now figuring out that indeed ... I did not. So, allow me to start again... and apologize to all for wasting your time.

I will likely be back... but let's see if using the AMD64 ISO makes a difference?

KaptKan (slightly chagrined)

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> OK thank you for your input... however, I may be a luddite when it comes operating systems. I know my end products (office tools) but am at a loss as soon as I look under the hood. Please bare with me...

I visited your "Step 1" page...
For the md5sum matter I was about to raise a litany of problems but now realize that reading the whole page, it is important to "read the manual"! I tried executing the Linux instructions... Ooops!

So, once I read and tried the Windows version of the guide on md5sum I got a confirmation that my CheckSums are the same.

**I did notice one interesting thing: **I notice that there is an ISO for AMD64. I downloaded an ISO for i386 ... should I have downloaded and AMD64 ISO??? Oh my - someone take the steering wheel out of my hands before I drive this bus off the road! **Of course... step 1 of your Step1 file tells us to read the manual... **I suppose you are now figuring out that indeed ... I did not. So, allow me to start again... and apologize to all for wasting your time.

I will likely be back... but let's see if using the AMD64 ISO makes a difference?

KaptKan (slightly chagrined)

Take a deep breathe and read the whole thing.
I'm here, almost 24/7 so you're not wasting my time, I'm enjoying helping others ;)

What CPU do you have?

---

### Post by kaptkan on 2010-12-21
My CPU - AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 2.00 GHz
RAM - 1.00 GB
System Type: 32-bit Operating System

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> My CPU - AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 2.00 GHz
RAM - 1.00 GB
System Type: 32-bit Operating System

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

My apology if this is indirect answer to your question but I've learned a simple thing ... I don't answer a question unless I'm 100% sure of the answer or at least I have tired it before.
I have never had a 64-bit OS or CPU. Thus, all what I could do is to provide the link above.

---

### Post by kaptkan on 2010-12-21
Now I am confused again... 

The system is not a 64-bit OS... it is a 32-bit OS.

Is it your contention that I should **not be able to install** the Ubuntu OS??

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> Now I am confused again... 

The system is not a 64-bit OS... it is a 32-bit OS.

Is it your contention that I should **not be able to install** the Ubuntu OS??

If your CPU is 64bit then download the 64bit version.
If your CPU is 32bit then download the 32bit version.

Edit: [http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit](http://en.wikipedia.org/wiki/64-bit#32-_vs_64-bit)


> In [x86-64]("http://en.wikipedia.org/wiki/X86-64")  architecture (AMD64), the majority of the 32-bit operating systems and  applications are able to run smoothly on the 64-bit hardware.

---

### Post by kaptkan on 2010-12-21
OK - here i go again exposing my luddite-ness... does the 64 X2 dignify a 64-bit CPU? or is the fact that the existing OS a 32-bit OS what I should be concerned with. :) Thank you for your patience.

---

### Post by kaptkan on 2010-12-21
Oh well, I am reaching my threshold for understanding this process. I truly appreciate those who understand the OS world... it seems above my skill level.

AMJJAWAD provided some interested reading and the allegory of the Lego set brought me home to reality:

> A parallel situation that can emphasize the problems is Lego. Picture the following:

[LIST]
[*]  New: *I wanted a new toy car, and everybody's raving about how great Lego cars can be. So I bought some Lego, but when I got home, I just had a load of bricks and cogs and stuff in the box. Where's my car??*
[*]  Old: *You have to build the car out of the bricks. That's the whole point of Lego.*
[*]  New: *What?? I don't know how to build a car. I'm not a mechanic. How am I supposed to know how to put it all together??*
[*]  Old: *There's a leaflet that came in the box. It tells you exactly how to put the bricks together to get a toy car. You don't need to know how, you just need to follow the instructions.*
[*]  New: *Okay, I found the instructions. It's going to take me hours! Why can't they just sell it as a toy car, instead of making you have to build it??*
[*]  Old: *Because not everybody wants to make a toy car with Lego. It can be made into anything we like. That's the whole point.*
[*]  New: *I still don't see why they can't supply it as a car so people who want a car have got one, and other people can take it apart if they want to. Anyway, I finally got it put together, but some bits come off occasionally. What do I do about this? Can I glue it?*
[*]  Old: *It's Lego. It's designed to come apart. That's the whole point.*
[*] New: *But I don't **want** it to come apart. I just want a toy car!*
[*]  Old: ***Then why on Earth did you buy a box of Lego??***
[/LIST]
I figured out that I was using the wrong ISO (i386 v.s. AMD64) and ran the md5sum to confirm that it was a correct and complete download. But when I tried to run it from my USB flash drive it seemed to go through all the motions and then the screen went blank - indicating "No Signal". There was no purple screen with a man behind a computer (as previously suggested) and no further GUI dialog prompting me to "try" or "install" Ubuntu.  
I would like to say that I won't give up... but I fear that I lack the necessary geek creds to pursue this quest.

;)

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> OK - here i go again exposing my luddite-ness... does the 64 X2 dignify a 64-bit CPU? or is the fact that the existing OS a 32-bit OS what I should be concerned with. :) Thank you for your patience.

Isn't that your CPU?

[http://www.amd.com/us/products/desktop/processors/athlon-x2/Pages/amd-athlon-x2-dual-core-processors-desktop.aspx](http://www.amd.com/us/products/desktop/processors/athlon-x2/Pages/amd-athlon-x2-dual-core-processors-desktop.aspx)

I have never ever used AMD in my whole life, period. However, I know how to find out what I don't really know. Plain and simple, I use google.

From what I posted so far, I guess using 32-bit OS is not a bad idea.
You need to use google, mate. Try to find out more about your hardware as it's your hardware :)

---

### Post by msandoy on 2010-12-21
You have a 64bit CPU. It can run both 32bit and 64bit OS. But with only 1GB RAM, I would go for the 32bt (i386).
If you tried Ubuntu 10.10, please try with 10.04, since that is a LTS, hence supposed to be a bit more stable.
When you boot your computer with the USB drive, you are supposed to get a screen with some choises. If that screen does not come up, there is something fishy with your USB install. Do you have the posibility to try with a CD?
Just to ask a dumb question, you did download the desktop version, and not the alternate install?

---

### Post by kaptkan on 2010-12-21
I did install the Desktop version and not the alternate. I get a plain screen with choices and it defaults to running Ubuntu from the USB... but after all the script seems to run through... the screen goes blank... and appears not to be communicating with the computer anymore.

---

### Post by kaptkan on 2010-12-21
amjjawad - thanks... you are very correct pointing out that it is "my hardware" ... I admit that I have very little knowledge - but thank you for your advice and patience.

---

### Post by bubba_169 on 2010-12-21
Do you know what make you graphics card is? I had a similar issue with an onboard nVidia 8200 but never found a friendly solution.

---

### Post by amjjawad on 2010-12-21
> **kaptkan said:**
> amjjawad - thanks... you are very correct pointing out that it is "my hardware" ... I admit that I have very little knowledge - but thank you for your advice and patience.

Please do not be offended. If I were you, the first thing I would do is "read" as much as I can in order to understand what's going on.
I was just like you when I started with Linux. I've been using Windows for 10 years and then, out of sudden, I moved to Linux. Too much of a different world. I did lots of mistakes and that's why exactly I have learned from my mistake.

I'm so much willing to help you step by step but after all, you're sitting there with your machine. Our job is to offer some suggestions, advices and steps to follow but it's you who will do it :)
Believe in yourself and don't lose hope.

My finial suggestions if you don't mind:
Keep reading and use the 32-bit Desktop version for 10.04 or 10.10. Check the MD5SUM and try to create the liveCD as explained in Ubuntu download page ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)).

If that did not work, try the alternate CD. Perhaps it's your Graphics Card.

All the best and I'm here if you need anything!

---

### Post by msandoy on 2010-12-21
I would still suggest that you try starting from a live CD, if you have that posibility. But it might be a hardware incompatibility as bubba_169 mentioned.

Please be warned, the alternate cd does not give you the choice of trying Ubuntu, it is meant to install in text mode.

---

### Post by bubba_169 on 2010-12-21
A bit of background on my problem: Ubuntu was trying to use the open source nVidia driver when it didn't support my hardware. I had to switch to a virtual console and edit config files to make it use vesa before I could see an X screen. Not sure if this will help at all?

---

### Post by Hippytaff on 2010-12-21
A work around for some graphics issues (especially Nvidia) is to drop into the grub menu by highlighting ubuntu *when given a choice of OS's/Kernels, by pressing e. Delet 'quiet splash' and type 'nomodeset' and press CTRL+X to boot.
 
Obviously this will not work unless you can get to the grub menu in the first place.
 
Edit -> and then I would install the recommened proprietery driver from System -> Administration -> Alternative Drivers
(something like that, can't check at the moment)

---

### Post by amjjawad on 2010-12-21
Okay, this is my last post for now because I have to go.

1) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

2) From: Download Ubuntu Desktop Edition > Download Ubuntu 10.10 OR 10.04.

3) Choose 32-bit and then click "Start".

4) Once done, check MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The above link explains in details what do you need to do.

5) Compare your MD5SUM with:

 59d15a16ce90c8ee97fa7c211b7673a8 
    ubuntu-10.10-desktop-i386.iso 



or


9a95ed6f6ec38fb58c446dba1add6a08 
    ubuntu-10.04.1-desktop-i386.iso


6) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) >  #2 (Burn your CD or create a USB drive).
I guess it's very clear and explains in details what do you need and how.


7) If you already have tired all the above and failed, then you may want to try the alternate CD but keep in mind the installation will be a bit harder as it's text-based installation. Beside, there is no LiveCD.


8 )  If you're sure you have AMD64 then you could try the 64-bit version. BUT I'M NOT SURE ABOUT THIS 100% - CHECK with someone who knows about 64-bit version.


9) Make sure your BIOS settings are set correctly so that you could boot up from CD and USB.


10) If you can't boot up from USB, try CD or [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)




At the moment, that's all what I could offer ... sorry, have to run.


Good luck :)

---

### Post by msandoy on 2010-12-21
I'm not totally clear if you get the proper startup screen or not. When the computer boots from USB, do you get to a screen asking you for the language to use, then you should be able to press F6, and choose no acpi, this sometimes help to solve startup issues.

---

