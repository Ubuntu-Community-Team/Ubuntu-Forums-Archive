---
title: "video card"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by soffer on 2009-11-09
i'm trying to install Sparkle Geforce 9400 gt (pci version) and my ubuntu 9.04 is getting stuck...
Please help
any ideas?

---

### Post by realzippy on 2009-11-09
How did you try?what happened?
Tried system/administration/restricted drivers?

---

### Post by soffer on 2009-11-09
I cant even get there. with the onboard video the systems great - but when i plug in the pci card - it simply gets stuck and doesn't load. I;m trying now to install 9.10.
maybe it can handle it?

---

### Post by realzippy on 2009-11-09
Can you disable onboard graphics in BIOS?

---

### Post by soffer on 2009-11-09
you think it might do the trick? trying right now and updating

Thanks!

---

### Post by soffer on 2009-11-09
the priority is set to pci/agp/onboard - so that's fine.
and even with 9.10 - it just gets stuck on the opening logo.


oooooooppppppphhh!

---

### Post by realzippy on 2009-11-09
So you cannot even run the live-CD?
Try starting in recovery mode;if that would lead to terminal,we could go on...

---

### Post by soffer on 2009-11-09
hang in there for me man, I'm trying now.

---

### Post by soffer on 2009-11-09
How do I get into recovery?

---

### Post by realzippy on 2009-11-09
press *escape* when:

grub loading stage 1.5 at bootup

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by soffer on 2009-11-09
ok im in - now what?

---

### Post by realzippy on 2009-11-09
** nvidia-xconfig**

---

### Post by soffer on 2009-11-09
something's off here, this is what i get:
even before loading it gives me a menu to choose from. one of them says "(recovery)"
and "c for command".
I used the "c" and get "sh:grub>" which then says "unknown command 'sudo'

---

### Post by realzippy on 2009-11-09
??Again,while "grub loading stage 1.5" press "escape",select actual kernel (recovery mode),what should lead to a (blue) window.select root shell,
something like "drop to root shell promt" (no 9.04 around,this is from 9.10)At root shell try:
**nvidia-xconfig**

---

### Post by soffer on 2009-11-09
sorry man, as long as the pci card is plugged in, it wont even let me get to loading grub.
It simply gets to a b/w screen with these options:
1/ ubuntu, linux 2.6.31-14.generic
2/ ubuntu, linux 2.6.31-14.generic (recovery)
3/ memory test (memtest 86+)
4/ memory test (memtest 86, serial console 115200)

choosing 1 gets it to show me those running lines until it gets stuck, choosing 2 gets me to where i wrote before
:-(

---

### Post by realzippy on 2009-11-09
"to where i wrote before" is what I do not understand.You should get to a root shell somehow...and type *nvidia-config*.
(what would not work if no nvidia driver installed for onboard-device,which -so I thought-was also nvidia.My mistake).
So  "dpkg-reconfigure xserver-xorg" in case of non-nvidia onboard graphics..

**but** not booting to recovery mode with plugged pci card  might be a bios problem.

---

### Post by soffer on 2009-11-09
I tried to do what you've written, and only without the pci card installed did I see the white on blue recovery menu. I guess it means somethings wrong with the card? the bios?

---

### Post by anewguy on 2009-11-09
On that boot menu you posted, select option 2 - this should boot you either directly to a command line or at least to a logon, which after you logon will be at the command line.  At that point try the nvidia-xconfig again.  If that doesn't work then try the dpkg-reconfigure xserver-xorg (*if* this is even available in 9.10).

Please post back any results, including failures and error messages.

Dave :)

I'll be gone for about an hour but someone should be able to help you prior to my return - I'll check when I get back.

---

### Post by anewguy on 2009-11-09
> **soffer said:**
> I tried to do what you've written, and only without the pci card installed did I see the white on blue recovery menu. I guess it means somethings wrong with the card? the bios?

Guess you posted back while I was typing - sorry!  However, since removing the PCI card removes the problem, please post back the following:

- the motherboard model

- the onboard graphics model

- the BIOS settings for your default video

Thanks

Dave :)

---

### Post by realzippy on 2009-11-09
> **soffer said:**
> I tried to do what you've written, and only without the pci card installed did I see the white on blue recovery menu. I guess it means somethings wrong with the card? the bios?

Not wrong,old.Maybe there is a newer bios out?
You only have the option *pci/agp/onboard*?
No way to **disable** onboard/agp ?edit: (mainboard jumper?)
The Kernel seems to have a problem.
Try booting a live CD (9.10),there is an option for graphic modes at startup..

---

### Post by soffer on 2009-11-09
Listen you two - 1st of all thanks for being this patient with a clueless noob.
Seriously.

Here are the details:
MB: asrock P4i65GV
the onboard video: Intel® Extreme Graphics 2
bios setting: pci/agp/onboard

---

### Post by anewguy on 2009-11-09
Just downloaded and looked through the user manual for your motherboard.  It appears you have video selection set correctly, so I wonder if it makes any difference if you change the value of "Internal Graphics Mode Select".  Outside of auto, the manual doesn't list what the possible values are - see if it allows a setting of disabled or size of 0 or something along those lines.

The manual also seems to indicate that if the driver for the onboard graphics is installed that it will always use the onboard graphics instead of an add-on card.  I don't know if this is true for Linux or not, but it does make me ask the following:

- did you install with the add-on card in place, or is it an update after the installation (e.g., did things only work for the install with the onboard graphics?)?

Not sure exactly what is going on.  Since an AGP slot is provided and the manual lists the supported boards for that, perhaps it defaults to running the onboard graphics if there is no board in the AGP slot.  So, another question:

- with the add-on card installed, connect your video to the onboard video and try booting, etc..  Do things look okay then?  If so, it may be a matter of the onboard graphics overriding the add-on.

Dave :)

---

### Post by anewguy on 2009-11-09
Another thing I found - if you have your PCI video card in slot 3, the one that shares with the riser slot, you should try moving it to slot 1 or slot 2 and see if that makes any difference.

Dave :)

---

### Post by soffer on 2009-11-10
Hey Dave.

I've installed XP on the machine just to make sure the MB and 9400 can work together, and they do, no problems.

As for you're queries:

I tried to add the card after an Ubuntu installation, and after failing to boot, tried to reinstall fresh. Didn't work as well. Without the card - things work.

To check your next idea, I'll reinstall 9.10 (side by side with windows) and try to connect my video to the onboard video and try booting, etc..  

thanks and will update soon

---

### Post by soffer on 2009-11-10
update: after my system worked fine (win xp, pci video installed), I tried to install Ubuntu side by side.
The installation went past the "extracting files" stage fine ant then asked to restart in order to complete.
Upon restarting I was to choose (win/ubuntu) and chose Ubuntu.
Than it stuck with this last line:

udev[120]: worker [155] unexpectedly returned with status 0xoob


???

---

### Post by anewguy on 2009-11-10
Now I'm confused......:(

I should add that searching the net for the motherboard and adding a video card seems to suggest the only way to truly disable the onboard video is by using an AGP card in the "AGI" slot.  The manual lists those boards that are supported in the "AGI" slot, and apparently it is not just a standard AGP slot - hence why they call it an "AGI" slot.  I would suspect that the onboard video isn't being disabled by a PCI video card even with the video sequence set in the BIOS, and therefore 2 video cards are conflicting.

Dave

---

### Post by soffer on 2009-11-11
> **anewguy said:**
> Now I'm confused......:(

I should add that searching the net for the motherboard and adding a video card seems to suggest the only way to truly disable the onboard video is by using an AGP card in the "AGI" slot.  The manual lists those boards that are supported in the "AGI" slot, and apparently it is not just a standard AGP slot - hence why they call it an "AGI" slot.  I would suspect that the onboard video isn't being disabled by a PCI video card even with the video sequence set in the BIOS, and therefore 2 video cards are conflicting.

Dave

Dave, I suspect that if that was indeed the case then windows would also act all weird on me...


As for now, I've installed xbmc for windows and it works great. I have to say I'm disappointed because I'm extremely curious about Ubuntu and would love to setup my system with this OS.
Now I;m just looking around to find out how to operate my Win/XBMC system with the wiimote, a thing which is fairly easy with Ubuntu but seems different under Win.

I thank you for the help, and if you have any more ideas would appreciate them very much.

:)
Adi

---

