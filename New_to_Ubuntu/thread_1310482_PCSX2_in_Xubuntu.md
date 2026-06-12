---
title: "PCSX2 in Xubuntu?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by ProDigit on 2009-11-01
I wanted to run PCX2 in xubuntu.
I found very little info on how to install it.
I downloaded and unpacked the folder on my desktop, and the folder seems to have an executable; no help or readmes to read...

I execute the program, and get following error:
> 
"Could Not Load GS Plugin '/home/*****/Desktop/pcsx2/plugins/': /home/*****/Desktop/pcsx2/plugins/: cannot read file data: Is a directory"

with "*****" as the login name.

Then a window appears (see pcsx2.png in attachment).

I see I don't have any display driver (OR GRAPHICS SUBMENU)to choose from.

I have a Laptop running the latest Xubuntu 9.10 with latest updates, with an Intel® Graphics Media Accelerator 950 Chipset: Intel® 945GM GPU.

What's missing?
Do I need to install a display driver?
Do I need to install OpenGl?

The website notes:
> You need the following installed: gtk2, opengl, libbz2, libjpeg, glew-dev, libxxf86vm-dev, x11proto-xf86vidmodeautomake and autoconf (version >= 1.9) Nvidia Cg-Toolkit, libasound-dev, joystick.

Plugins available for Linux are: ZeroGS OpenGL, ZeroSPU2, PeopsSPU2, ZeroPad, EFP Iso, EFP Polling and Linuz Iso

Can I install all of them easily on a 4GB USB stick (with still 800MB of free space left)?

And if I can, how can I do this, since many of the dependencies and programs I can not find in Synaptic.

Thanks!

---

### Post by jefri_of_azure_sea on 2009-11-01
I think you dont need to install the VGA driver, because your VGA already detected by the system

Actually to play the emulator you need to download some plugin for the emulator by yourself
-sorry if my English is really bad-

---

### Post by ProDigit on 2009-11-01
it seems like [this site]("https://help.ubuntu.com/community/CompilingSoftware") is telling me how to compile.

Then [This link]("http://ubuntuforums.org/showthread.php?t=1114229") is telling me the commands for the required dependencies.

It sure would be nice for the noob to either have the dependencies and packages automatically installed with a 'PCSX2 package' in synaptic, or at least write a simple user manual...
I just hope the emulator will be as playable in Xubuntu as it is in Ubuntu... (which is nearly unplayable slow)

---

