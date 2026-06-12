---
title: "Help, 10.04 Lucid Lynx, everything slow, HELP..."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by x3jose on 2010-05-01
Hi I just installed Lucid and now every thing is for the most part sooo slow. Im a newb to linux but had 8.04 before. So I did a complete partition and reinstalled twice yet still same slowness, as if this computer had 100mb of ram and No available virtual memory every process is soo slow. I would hate to go back to XP since i think that Lucid Lynx is just soo dam sexy. ;P So if you can help I would be very apreciative.

---

### Post by nixclusive on 2010-05-01
Please post your hardware configuration. :)

---

### Post by Paul T. on 2010-05-01
You can try looking at system monitor to see what's going on:
System>Administration>System Monitor

---

### Post by TechRomeo on 2010-05-01
I have the same problems. After upgrading to Lynx from 9.1 all is sluggish. Did id a disaster for me. 
 There is no Ubuntu Welcome screen and sound anymore. After that there is a scrambled screen before showing the desktop 
Some people say you can fix this with CLUTTER_VBLANK+none.
I have not a clue how to do that.

---

### Post by quinnten83 on 2010-05-01
> **TechRomeo said:**
> I have the same problems. After upgrading to Lynx from 9.1 all is sluggish. Did id a disaster for me. 
 There is no Ubuntu Welcome screen and sound anymore. After that there is a scrambled screen before showing the desktop 
Some people say you can fix this with CLUTTER_VBLANK+none.
I have not a clue how to do that.


Backup your home-drive to an external drive and reinstall. Create a separate home partition so if 10.04 does not work for you, you can easily install 9.10 or another Linux distro.

---

### Post by jvc26 on 2010-05-01
+1 for the separate home partition - really useful for just wiping the OS and restarting. If you could give us some more details on the hardware involved we may be able to help futher, Lynx is pretty snappy for me.

J

---

### Post by TechRomeo on 2010-05-01
The same problem here.  All is sluggish. No Ubuntu Welcome screen anymore.  I was using Compiz too.
Silly of me not to ghost the OS partition

Since I am new to Ubuntu. What do I actually need to do to fix this.
I red this site, but it is too Spanish for me to find a way to fix my system.
[http://live.gnome.org/GnomeShell/SwatList](http://live.gnome.org/GnomeShell/SwatList)

---

### Post by TechRomeo on 2010-05-01
Not sure if this is a bug or just me.

Silly of me not to ghost the OS partition

Since I am new to Ubuntu. What do I actually need to do to fix this.


I red this site, but it is too Spanish for me to find a way to fix my system.
[http://live.gnome.org/GnomeShell/SwatList](http://live.gnome.org/GnomeShell/SwatList)

I probably will reinstall 9.1. I was quite happy with it.

---

### Post by TechRomeo on 2010-05-01
I guess wipe the drive and reinstall 9.1.  No harm done sine I don't use it for data. I use this old PC as Net TV Video Player.
Next time I will Ghost the partition before upgrading.

---

### Post by vuthailinh on 2010-05-01
after upgrade to lucid my computer become slow and slow....

then type password : more than 30s to desktop. in karmic it is 0s - immediate
open ntfs disk needn't password (at the first open)
...
i think i will reinstall karmic

---

### Post by x3jose on 2010-05-01
> **jvc26 said:**
> +1 for the separate home partition - really useful for just wiping the OS and restarting. If you could give us some more details on the hardware involved we may be able to help futher, Lynx is pretty snappy for me.

J
Well, I dont know if this is what you mean but for all i know Im using a 4 year old notebook with 512mb ram and 250 gb hd

---

### Post by nathan726 on 2010-05-02
Go to System > Preferences > Startup Applications

Disable anything you know you wont need - for example, I disabled: Bluetooth Manager, Evolution Alarm Notifier, Gnome Login Sound, Network Manager, Remote Desktop, Ubuntu One, Visual Assistance (I don't need or use any of these services).

After doing this (and restarting my computer) I noticed I had about 500Mb more ram. I'm not sure which one of the above startup applications was hogging all the ram, but you could try and experiment and see what works best for you.

---

### Post by utnubuuser on 2010-05-02
Have you guys tried disabling ACPI?
I was reading another thread in which slowness was an issue, though it was in Virtual setups, and the solution was to disable ACPI.

**I'm only pointing this out, -- I know nothing about ACPI.**

---

### Post by Pakia on 2010-05-02
I am running the server version and it to is extremely sluggish. I checked the partitions and noticed that there is no swap. I did the upgrade from 9.10. Besides being sluggish all works fine. System monitor shows very low resources being used. Any advice welcome and thanks in advance

---

### Post by la1234uk on 2010-05-13
:confused::confused:

I have very similar problems... with 9.10 I had a pretty fast life on ubuntu, gorgeous compiz running with emerald at over 100 frames/sec, could work jumping through desktops with many applications open without noticeable slow downs. (see pics below for my hw specs)

Updating about 10 days ago to 10.4, boot got slightly faster, but after logging in and waiting few minutes (even doing nothing at all), compiz starts to suck all cpu, frame rate drops below 20 in idle, and below 10 doing things... strangely enough I didn't notice this problem the first days, only few days ago.

Tried to google forums, but find nothing that heals it. I use ubuntu for work and would be very happy to come back to higher frame rates... ! What the heck could be the problem ? Is there a bug somewhere in lucid lynx ??

Any suggestions will be tested and reported here, thanks a lot in advance !

GR

[IMG]http://ruggero.sci.yokohama-cu.ac.jp/img/rep1.jpg[/IMG]

[IMG]http://ruggero.sci.yokohama-cu.ac.jp/img/rep2.jpg[/IMG]

---

### Post by Zisland on 2010-05-18
Don't know if this helps.  I have an old Toshiba Satellite and had the same problem.  I followed another thread ( [http://ubuntuforums.org/showthread.php?t=1468876](http://ubuntuforums.org/showthread.php?t=1468876)) and followed the instructions on resetting the swappiness per the instructions on post #40, then followed all the instructions on the Swap FAQ ( [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ).  My Lucid Lynx system is now lightning fast.  Hope this helps.

---

### Post by Salomonis on 2010-07-14
Sorry for the story format, but the history may help.  I recently upgraded to Lynx and didn't have any problems until I had downloaded and used Celestia(Gnome) and or KDEStars.  These programs required Open GL rendering(so I used restricted drivers NVIDA I have Nvidia 6800 Ultra).

---

### Post by Salomonis on 2010-07-14
(Sorry for double post)  continuing, btw I was using Stellarium with no problems before that.  So I decided to remove my restricted hardware and delete Celestia and Stars and that worked perfectly unfortunately  Stellarium would only run at .300 fps.  I went to NVidia drivers page and downloaded the specific driver needed 256.35  it was a .run file so I had to purge nvidia and add thing to the blacklist(sorry I don't have link to that forum)  Now everything is slow whether I uninstall the driver or not.  I noticed in the memory that swap and mem never reaches 300MB even though I have a GB. Processor goes up to 100% and things go grey like they are about to FORCE QUIT.  Any suggestions?

---

### Post by Salomonis on 2010-07-14
Well I don't know what's hapenning, but apparently after a day of shut down I haven't had laggy problems.  Before that it was running for 4 str8 days, but this is linux.  That shouldn't be a problem.  Maybe some of the hardware is over heating.

---

### Post by nedsowt on 2010-12-06
> **nathan726 said:**
> Go to System > Preferences > Startup Applications

Disable anything you know you wont need - for example, I disabled: Bluetooth Manager, Evolution Alarm Notifier, Gnome Login Sound, Network Manager, Remote Desktop, Ubuntu One, Visual Assistance (I don't need or use any of these services).

After doing this (and restarting my computer) I noticed I had about 500Mb more ram. I'm not sure which one of the above startup applications was hogging all the ram, but you could try and experiment and see what works best for you.
This worked for me, good advice.

---

