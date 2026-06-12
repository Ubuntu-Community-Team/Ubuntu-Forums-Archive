---
title: "Gnome power management issue"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by ozmann54 on 2010-11-30
i have a Dell that is giving me the following message:

he configuration defaults for 
GNOME Power Manager have not
been installed correctly.
Please contact your computer
administrator.

I am totally new to this system and need step by step help to resolve this...
thanks

---

### Post by cariboo on 2010-11-30
I would suggest you go to System->Administration->Synaptic Package Manager, search for gnome-power-manager and mark it for re-installation.

---

### Post by terobin on 2011-03-03
I'm getting the error on my netbook, and it's not letting me log in to fix it.

Is there a way I can force my way in to try and fix it? Otherwise I guess I'll just have to reinstall, which is an inconvenience.

---

### Post by lz1dsb on 2011-03-03
What kind of error are you getting? Could you share some outputs with us?

---

### Post by terobin on 2011-03-03
When I turn it on there's an error message in the top right hand corner of the log in screen. It says,

"Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator."

When I try and log in in any of the modes, they all just send me back to the login page with the same message.

I'd be quite happy to reinstall Ubuntu, I downloaded it and followed the instructions to put it on a USB device, and went into BIOS to set it to boot from that device, but it keeps ignoring it.

---

### Post by lz1dsb on 2011-03-04
Do you try to run Ubuntu from live USB? In order for this to work, you need to start your machine with the USB stick plugged in and select it as a preferred device from the BIOS menu. Otherwise it won't work. 
For the other problem. Did you try to reinstall the Gnome-power-manager package?

Cheers, 
Boyan

---

### Post by terobin on 2011-03-04
The BIOS is set to boot from the USB stick, I selected it by name. It's just ignoring it though.

As for reinstalling the Gnome-power-manager package, is there a way to do that without logging in? Whenever I put in my password, no matter how I try to start up (Netbook edition, Desktop edition, etc for all the options), it just returns me to the login page and displays the error message again.

EDIT:
I went back into BIOS and disabled all the other boot devices, so the only option was to boot from the USB stick. The following message comes up:

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

Pressing a key repeats the message.

I think that my USB stick isn't suitable for booting from, maybe. It's actually a USB stick/MP3 player thing, so I'll try it with a different USB stick as soon as I can get access to one.

EDIT 2:
I've set up another USB device as the ubuntu-netbook boot disc, but my netbook wont boot from that either. It's just showing me the same

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

message.

EDIT 3:
OK, after considerable dicking around I've managed to get a terminal open.

Now all I need is a command to fix GNOME Power Manager, I think...

EDIT 4:
I used sudo apt-get purge gnome-power-manager and then sudo apt-get install gnome-power-manager to remove and reinstall it, but the netbook still wouldn't let me log in.

I then went back to the terminal and used sudo apt-get purge compiz* because that was the last thing I'd installed before it stopped working.

After compiz had been purged, the netbook started working fine. I assume it's because compiz is too demanding on my very, very underpowered netbook.

Anyway, I think that's done. Cheers!

---

### Post by lz1dsb on 2011-03-05
Wow. It looks like you've gone through a lot of problems! It's great that you didn't give up though. That's important. 
I've heard about problelms with USBs used for booting. And I think I've read somewhere that some USB flash drives aren't suitable for such applications anyway. I think that you've stumbled upon exactly on such issue.
Anyway, the important thing is, that you've solved the issue.

Cheers,
Boyan

---

