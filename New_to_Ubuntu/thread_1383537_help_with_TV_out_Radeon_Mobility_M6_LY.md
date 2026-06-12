---
title: "help with TV out Radeon Mobility M6 LY"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by zsazsa on 2010-01-17
Hi,
I want to use my TV out on my Compaq evo n600c.
I use Ubuntu studio 9.10
Could somenone please help me out?

What I've done uptill now:
check card:
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

tried to install ATI driver with Envyng -t
 +---------------------------------------------------------------------------+
 | Number | Candidate Version | Installed Version | Compatible | Recommended |
 |---------------------------------------------------------------------------|
 | 0      | 8.660-0ubuntu4    | 8.660-0ubuntu4    | -          | -           |
 +---------------------------------------------------------------------------+

It wants to install the same driver as already is installed.

I can find a suitable driver at the ATI/AMD site.


I added the medibuntu repostory
installed atitvout and various for ATI support
it doesn raact to many commands, what it does do is:
~$ sudo atitvout vbe
VBE Version: 2.0
VBE OEM Identification: ATI MOBILITY RADEON
:~$ sudo atitvout detect
CRT is attached.
~$ sudo atitvout standard
Can set on the fly:
 ntsc
 pal
 palm
Current standard is PAL.

I don't understand why it says CRT is attached. I did this with nothing attached and with TV attached, it both said CRT is attached.
The commands to set the output give 'VBE call failed'error


I installed ATI ccc, it gives me the message:
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

tried to start aticonfig:
~$ aticonfig
aticonfig: No supported adapters detected


xorg.conf contains:
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "dri"
    Load    "GLcore"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "vesa"
EndSection


I hope somebody can help me out.

---

### Post by halitech on 2010-01-17
Looking at your xorg.conf file, its using the vesa driver right now which is why you are getting the message of no supported adapters detected. Also, based on what I can find out about this laptop, I *think* its old enough that 9.10 is not going to work with whatever driver is currently available from ATI. I think you may need to drop back to 8.04 in order to get a driver to work with that age of machine.

---

### Post by zsazsa on 2010-01-19
thanks,

that's defininetly a solution I don't want to hear ;-)
i'll try tinkering around.

---

