---
title: "Wifi Problem! Connected but cannot use internet"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by Psil0cybin on 2013-09-14
Hey guys I was playing around with samba last night, and Had to uninstall it because after I installed and configured it my internet stopped working on the machine that I installed it on. My wireless internet continued to state that I was connected to the network but just THAT computer could not use the internet.

The internet would start working every couple of minutes, and then stop working, I do not understand how this happend.

how can I diagnose this? The connection works for a few minutes, here and there...but I cannot really browse a bunch of sites because half way in between everything is not reachable and trying to download any file is impossible..
how can i go about fixing this issue?
Thanks in advance

---

### Post by CeejRab on 2013-09-15
Hello Psil0cybin,

Sounds tricky... Can you tell us what kind of computer you are using, what version of Linux you're running, and when exactly did the wireless internet start to fail and work intermittently? 

For now all I can suggest is resetting your IP address and reinstalling the drivers for your wifi card. You can find tutorials for these processes fairly easily in a web search. 

All the best,

-Christian

---

### Post by Psil0cybin on 2013-09-15
I am using Xubuntu 12.04, this happend when i started playing around with samba.
I am using an HP laptop, I forgot what exact model.

the internet was working fine untill i installed samba, and uninstalled it yesterday....
it had no problems at all before now

---

### Post by varunendra on 2013-09-15
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Bucky Ball on 2013-09-15
*Thread moved to **Networking & Wireless**.*

---

### Post by CeejRab on 2013-09-15
On another note, depending on how you removed samba, it may have left files or settings that are udesireable. You could reinstall it by the apt-get command or another method, and then use "Sudo apt-get purge samba" to delete its files, then "Sudo apt-get remove samba" to remove the whole package. This should help remove all of its files. 

I'm not sure how samba could have affected your wireless that badly, its a little puzzling. Have you tried running a live cd and seeing if the wifi works fine from that? If so at least it's not hardware it's a software glitch. A fresh install of the OS can fix that. 

All the best,

-Christian

---

### Post by Psil0cybin on 2013-09-15
Well I want to try to avoid reinstalling the whole OS. I spent hours customizing how I want things.
Like right now after trying again from the night before, I notice that when I booted up the computer, it worked perfectly fine...I am writting this post off the same computer I have been experiencing problems from, so it seems like its on and off, I notice the problem the worst when I try to download anytthing over 500mb off a HTTP Server such as trying to download an Ubuntu.ISO file. 
What I have noticed is that, the connection continues to state I am connected, but I seem to not be getting any packets.
Anyone know what commands I can execute to help me diagnose this problem? So you guys can help me

I am going to try sudo apt-get purge samba, and let you guys know how it went.

---

### Post by varunendra on 2013-09-15
> **Psil0cybin said:**
> Anyone know what commands I can execute to help me diagnose this problem? So you guys can help me

"Appears to be connected, but doesn't work" type problems are mostly driver issues. We need to see what driver, which version of it is in use and on what kernel version. Combined with this the info about other variables associated with a wifi connection and lastly, hints about what may be going wrong during the download. Hints may exist in dmesg and syslog.

Almost all of these factors are covered and diagnosed by the script I suggested. If you are interested in knowing specific commands to scan/diagnose these, just take a look at the script yourself.

Please run it (preferably when the connection appears to be frozen) and post back the report which should give us a comprehensive picture.

---

