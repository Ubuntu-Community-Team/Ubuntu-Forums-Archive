---
title: "Zsnes Help! Unable to install!"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by AzureBlade on 2009-07-12
I am very new to Linux, I just installed Ubuntu 9.04 on my 32 bit (I think) computer. My XP was messing up, and so I formatted the hard drive and reinstalled XP... but I didn't have the activation code. So now my computer is 100% Linux.

I am trying to install ZSNES from their site ([http://www.zsnes.com](http://www.zsnes.com)) and when I ran ./configure everything went okay, but when I ran make here was the result:

g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=athlon-xp -O3 -fomit-frame-pointer -s -fno-rtti -o tools/depbuild tools/depbuild.cpp tools/fileutil.o tools/strutil.o
tools/depbuild.cpp: In function ‘void dependency_calculate_asm(const char*)’:
tools/depbuild.cpp:133: error: ‘system’ was not declared in this scope
tools/depbuild.cpp: At global scope:
tools/depbuild.cpp:186: error: first argument of ‘int main(size_t, const char* const*)’ should be ‘int’
make: *** [tools/depbuild] Error 1

I understand "error: first argument of ‘int main(size_t, const char* const*)’ should be ‘int’", and I have fixed that, but I still got this:

tools/depbuild.cpp:133: error: ‘system’ was not declared in this scope
make: *** [tools/depbuild] Error 1

Please help!

---

### Post by cronos on 2009-07-13
I installed Zsnes v1.51 using the Synaptic Package Manager.  Good luck. :)

---

### Post by AzureBlade on 2009-07-13
I tried installing ZSNES 1.51 through APT, (sudo apt-get install zsnes), but now it doesn't work. When I run it, nothing happens. Thats why I tried compiling it from the source package. Thanks anyway, cronos!

Anybody know what's wrong?

---

### Post by DaGrimReefah on 2009-07-13
I'm not sure as you didn't provide much information, but you may be missing some dependencies.

---

### Post by jerome1232 on 2009-07-13
> **AzureBlade said:**
> I tried installing ZSNES 1.51 through APT, (sudo apt-get install zsnes), but now it doesn't work. When I run it, nothing happens. Thats why I tried compiling it from the source package. Thanks anyway, cronos!

Anybody know what's wrong?

What error's do you get if you run zsnes from a terminal?

---

### Post by DaGrimReefah on 2009-07-13
> **jerome1232 said:**
> What error's do you get if you run zsnes from a terminal?
Yes, install zsnes from Synaptic again, run it through terminal, and post the output on here. That would be helpful.

---

### Post by AzureBlade on 2009-07-13
I am very new to Linux... and so typically the most simple solution is probably the correct one: Run it in Terminal, which, honestly, I wouldn't of thought of. I am a bad troubleshooter. Here's the output:

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: HID 04d9:048e
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device
 
There's a lot of things wrong here: Unable to poll SIX files, two mice detected (mouse 0?), and, apparently, no available video device.

Now I'm really confused.

---

### Post by AzureBlade on 2009-07-13
I just ran it as root, and that fixes the permission problems, but I still get this:

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: HID 04d9:048e
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device

---

### Post by DaGrimReefah on 2009-07-13
Looks like you are missing some video drivers. What kind of video card/device do you have?

---

### Post by jimsheep on 2009-07-13
> **AzureBlade said:**
> I just ran it as root, and that fixes the permission problems, but I still get this:

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: HID 04d9:048e
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device
i had a similar problem, but i solved it by editing the configuration file to change the output mode to 600x800 windowed (mode 8, i think).  it ran like a dream.

you should find the configuration file in ~/.zsnes or one of its subfolders.

---

### Post by AzureBlade on 2009-07-13
How do I figure that out?

---

### Post by jerome1232 on 2009-07-13
pretty sure the unable to poll /dev/input# errors are fine, the detecting two mice are fine as well, it the video error, I've seen posts refering to removing libsdl and compiling the latest version solving it.

The thread I found was here
[http://board.zsnes.com/phpBB2/viewtopic.php?t=12973&sid=44da06c82c688fdf590c63ee014314ea](http://board.zsnes.com/phpBB2/viewtopic.php?t=12973&sid=44da06c82c688fdf590c63ee014314ea)

That's just the first result I got on google with these keywords 'zsnes Could not set 512x448 video mode: No available video device', perhaps a more in-depth search will pull up more.

---

