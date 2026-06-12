---
title: "Why did this happen? nVidia-glx-173/180/185 &quot;Desktop effects could not be enabled&quot;"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by heysean on 2009-08-10
Firstly and foremost, I want to state that, after reading endless counts of forum and blog posts, I finally came across one that worked, however, at the same time I decided to try something and am left wondering which probably did the trick. I'm new to Ubuntu and Linux in general.

I'm using the Jaunty 9.04 with an nVidia Gefore 7950GT.

I had tried all of the following and was left getting the desktop effects could not be enabled problem:


ctrl+alt+f1 to drop to console

sudo /etc/init.d/gdm stop
sh (nvidia driver package).run


It would run through the installation, build a kernel, modify the xorg.conf, then go back to the console, in which I restarted xserver.

Didn't work. Rebooted and that didn't solve the problem.
I tried using apt-get for nvidia-glx-173 and 180 and going through those steps.

Used the Hardware Drivers tool to activate 173 and 180.
Used EnvyNG, all of which had no change.

Finally, I went and redownloaded 185.
I had found a site that tried explaining how to do it really no different than I had previously been trying except for one small command.

The site said to "chmod +x" the file.

I did do this, but when I did, I rebooted into recovery, dropped to a root console, and, after chmodding it, "sh"'d the drivers.

It gave me a warning about trying to install it on runlevel 1, but I figured nothing could hurt it since it already wasn't working. Rebooted and it now works beautifully. I played around with the windows for a good solid 5 minutes. Haha.

Getting to the point of this post:
Was there something special that the chmod did, or was it the fact that I was in runlevel 1 that may have done the trick?

Whichever answer it is, please inform me on why so my 7 long hours of trying to get this to work doesn't just end with "Well... it works now."


Thanks :]

---

### Post by Paqman on 2009-08-12
> **heysean said:**
> 
Getting to the point of this post:
Was there something special that the chmod did, or was it the fact that I was in runlevel 1 that may have done the trick?


chmod +x adds the permission to execute the file, so that's what did the trick. 

Generally I avoid manually installing graphics drivers like the plague. Hardware drivers (or before that Envy) has always sorted me out nicely.

---

