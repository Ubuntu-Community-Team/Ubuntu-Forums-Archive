---
title: "Adding Software w/o Internet"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by kampion998 on 2010-02-23
I would like to add a lot of software to my Ubuntu vm, but i do not have an Internet connection to my desktop.  This has thus far kept me using XP, since it is simple to thow software on a SD or usb stick, and install from that.  

Some software I'd use would be Softmaker Office, plus video and graphics editting software.

Any tips for this linux n00b?:P

---

### Post by edwardLS on 2010-02-23
I am not sitting at my Ubuntu PC now, but I think I can remember enough to get you headed in the right direction.

In Ubuntu using Synaptic Package Manager you can select the packages that you want, and then instead of downloading and installing, you go under the "File" (I believe) menu and select something along the line of writing a script file for getting thos packages onto a Flash Drive.  Take the script file to an internet system and using "wget" you can get those packages.  Then take the Flash Drive with the packages to your Ubuntu machine.  Under "File" you can install from those packages.  

Sorry I don't have better detail at my fingers.  I used to do this with a Hi-Speed connection at work, and Dial Up at home.  It did the trick for me.

Good Luck

---

### Post by marshmallow1304 on 2010-02-23
Also see [Keryx]("http://keryxproject.org/").

---

### Post by jmszr on 2010-02-23
kampion998,

In addition to Keryx (as above), APTonCD might be what you are looking for: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) .

According to Ji Ruo in this thread: [http://ubuntuforums.org/showthread.php?t=1238179](http://ubuntuforums.org/showthread.php?t=1238179)

"You don't need to burn the ISO file created by AptonCD. It will save it to the hard drive, and then give you the option to burn it. Choose no and exit the program. Go into your file manager and navigate to the directory you saved it in, then copy and paste it to your USB drive. Reverse the process on the other computer and run AptonCD again to unpack it."

Edit: Further information.

---

### Post by mac9416 on 2010-02-23
Hey, kampion998,

Here is a description of the differences between Keryx and APTOnCD: [http://keryxproject.org/wiki/index.php?title=Keryx_vs_APTonCD](http://keryxproject.org/wiki/index.php?title=Keryx_vs_APTonCD)

also, here is someone's guide to using Keryx and APTOnCD together: [http://keryxproject.org/forums/index.php?topic=19&limit=1#p60](http://keryxproject.org/forums/index.php?topic=19&limit=1#p60)

---

