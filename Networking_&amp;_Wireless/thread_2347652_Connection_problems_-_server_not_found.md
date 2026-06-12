---
title: "Connection problems - server not found"
date: 2016-12-27
forum: Networking &amp; Wireless
---

### Post by adna95 on 2016-12-27
Hello! 
So I have been using this laptop for a couple of days now and I have encountered a few problems. I'm new to this and I have no idea how to solve it on my own. I don't know if these problems are in any way connected. 
First problem was that my screen froze. System was already booted, but I didn't use it in couple of hours. I solved it by shutting it down with button. After that everything was normal.
Second problem happened this morning after I tried booting my system. Black screen appeared and it said something about built in shell and initramfs, I don't remeber it clearly. 
So I found a solution on internet that somebody said it helped.
When initramfs appeared, I typed exit and it did some kind of checking. And then it said:
/dev/sda1 : UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck exited with status code 4.
The root filesystem on /dev/sda1 requires a manual fsck.

After that I typed fsck /dev/sda1, again it did some kind of checking and when it finished, I typed reboot.
It started booting as usual, but before login screen, black screen appeared and it said:
[ 16.686242] snd_hda_intel 0000:00:1b.0: control 2:0:0:PCM Playback Volume:0 is already present

I logged in after that, connected to Wi Fi, but when I opened Firefox and tried to open a page, it said Server Not Found. I even tried logging on steam, it still said there was no connection.
I really don't know what to do now, I hope I gave you enough information to solve this problem.
Thank you in advance.

---

### Post by SeijiSensei on 2016-12-27
I suggest you start over and reinstall Ubuntu.

First you cannot run fsck once Ubuntu is running without using sudo, i.e., "sudo fsck /dev/sda1," but more importantly you cannot run fsck on a mounted filesystem.  You can only run it from "recovery mode" that you can select from the boot menu.  You can then choose "root shell" from the menu and run "fsck /dev/sda1" from there.  You don't need sudo in that case because the recovery shell is running with root privileges already.

However I strongly suggest you reinstall if you're starting from scratch anyway.

Also never turn the power off on the machine without first running "shutdown" either from the program menu or manually from the terminal.  From the terminal, I usually just run "sudo reboot" then turn off the machine when the BIOS is booting up.  Turning off the power without shutting down gracefully can leave errors on the main filesystem.  When that happens, you'll get the "fsck" message you reported.

The problem you report probably means that name resolution, the process that translates "www.ubuntuforums.org" to its IP address, 91.189.94.12, is not working properly.  Reinstallation should fix that, too.

---

### Post by adna95 on 2016-12-27
I hope I don't sound stupid, but I have never used this kind of system before, how do I reinstall Ubuntu?

---

### Post by SeijiSensei on 2016-12-27
Hardly any machines come with Ubuntu pre-installed, so I assumed you had installed it yourself.  If the machine has a DVD drive, you can download an disk image and burn it to disc then install from that.  You'll need another working computer to do this, of course.  If it has no optical drive, you'd need to create a bootable image on a USB thumbdrive and boot from that.  I suggest starting by reading this document: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation).

Here are the disk images for Ubuntu 16.04.  You'll need to know whether your machine has a 32-bit or a 64-bit processor.  You can install the 32-bit image on either type, but if you try to install the 64-bit version on a 32-bit machine, it will report an error, and you'll need to download the other version.

32-bit: [http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-i386.iso](http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-i386.iso)
64-bit: [http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/xenial/daily-live/current/xenial-desktop-amd64.iso)

---

### Post by adna95 on 2016-12-27
Okay, I'll try that. And thank you for your time.

---

### Post by victoriano1979 on 2016-12-29
Hi @adana95 , in case you need further information here you have some good tutorials:
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
[http://www.alphr.com/operating-systems/1000061/how-to-install-ubuntu-run-linux-on-your-laptop-or-pc](http://www.alphr.com/operating-systems/1000061/how-to-install-ubuntu-run-linux-on-your-laptop-or-pc)

Hope it helps

---

