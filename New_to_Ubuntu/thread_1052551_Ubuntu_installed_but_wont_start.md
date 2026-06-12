---
title: "Ubuntu installed but wont start"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Island King on 2009-01-27
I have just installed Ubuntu 8.10 on my laptop, with the intention of dual booting Ubuntu and a pre-existing windows vista 64bit installation. The laptop is a gateway FX laptop.
Ubuntu booted from the disk and installed without any issues, I used the guided mode available on top giving ubuntu 50gb. It finished, and grub started up when the computer restarted giving me the options of
Ubuntu
Ubuntu recovery mode
Ubuntu memtest
Windows (recovery)
Windows

when I start Ubuntu the loading screen appears and goes through loading, then afterwards instead of anything starting a "_" is flashing in the top left corner of the screen and if it does stop the screen goes completely blank and then nothing happens.
what can I do to fix this?

---

### Post by kspncr on 2009-01-27
You could try recovery mode and see if that helps at all.

I think the easy way out (and maybe not the best if you want to learn more) would be to simply try reinstalling Ubuntu. It shouldn't hurt anything, since you haven't been able to boot into it anyway, right?

---

### Post by klein de usa on 2009-01-27
hi 
did you use the 64bit live cd? 
and if you did, did the live cd boot into the desk top?

---

### Post by valus on 2009-01-27
Hi,
I had the same problem when I installed Ubuntu for a friend of mine. It is an Ubuntu 64bit installation side by side with XP 32bit installation. 
Everything was just fine in the beginning but when I talk with my friend after 1 week he told me about this issue. I have no idea what it is. What I can tell you is that after 5-10 minutes of this cursor blinking Ubuntu will start (at least it started on that machine). And something else, not at every boot it happens this.

---

### Post by Island King on 2009-01-27
the Ubuntu install is 64bit as well, and when booting from the CD things worked fine, or at least appeared to. Recovery mode started, a lot to text went by very quickly, then everything stopped again, I waited a bit and then the screen went completely blank. 
How would I go about reinstalling? Do I need to uninstall first?
And if so how would I uninstall while being unable to start ubuntu?

---

### Post by bumanie on 2009-01-27
Possibly a graphics driver issue. You could try pushing Ctrl-Alt-F1 together. This brings you to a console screen, enter username and password and then type > sudo apt-get install ubuntu-desktop then hit enter. When it's finished downloading > sudo shutdown -r nowThis will reboot the computer and hopefully the desktop will be installed correctly. Alternatively, boot in recovery mode (second choice in grub menu) and try to install the graphics driver via System --> Administration --> Hardware Drivers.

---

### Post by kspncr on 2009-01-27
> **Island King said:**
> the Ubuntu install is 64bit as well, and when booting from the CD things worked fine, or at least appeared to. Recovery mode started, a lot to text went by very quickly, then everything stopped again, I waited a bit and then the screen went completely blank. 
How would I go about reinstalling? Do I need to uninstall first?
And if so how would I uninstall while being unable to start ubuntu?

You do not need to uninstall to reinstall first. To reinstall, you could just follow the exact same procedure you used the first time. However, I would try bumanie's suggestion first.

---

### Post by Island King on 2009-01-29
Thank You for your advice and information so far, but the damn thing still doesn't want to work.
Recovery mode encounters the same problem of not actually starting. Ubuntu started once, and only once, said something about my graphics driver, I had to turn off, and when I tried to start Ubuntu again is once again didn't work.
My Graphics card is a "NVIDIA GeForce 9800M GTS 1GB"
I tried to reinstall, but the guided installer tried to take another chunk out of Vista, and did not give the option to reinstall over the area that the Ubuntu install was in.

---

### Post by avtolle on 2009-01-29
To do an install over an existing installation, you would need to use the manual partitioner, and find the partition where your current Ubuntu installation is; give it a mount point of / and have it formatted as ext 3.

---

### Post by eragon100 on 2009-01-29
That card is supported :confused:

Download the latest 64-bit linux drivers from [www.nvidia.com](www.nvidia.com) (be sure to get the package that's called pkg2.run at the end, the largest download, because that one includes libraries for running 32 bit programs.

Then install these drivers from the text console. (start the system text-only mode, I believe you can select this if you start up safe mode.

then cd to the directory you had that driver put in, and then type:

chmod +x <driver name>

without the <>

and then:

sudo ./Nvidia-Linux-whatever-it's-called-exactly

Follow the very easy on screen instructions, select yes if it askw wether or not to install 32 bit opengl compatibility libraries, and if it asks wether or not to modify your xorg.conf.

Restart the computer and everything should work. Good luck! :wink:

---

