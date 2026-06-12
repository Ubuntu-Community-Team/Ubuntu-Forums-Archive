---
title: "How to install ubuntu from hard disk?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by hurzilipochtli on 2011-01-03
Hi everyone!

I have a laptop with kubuntu 06.10 and want to install ubuntu 10.10 on it. I have a bunch of problems which will make the experts laugh, I guess:

- The CD-Rom drive is broken, and I don't have an external one, so installation from a Live-CD fails.
- On a different computer with ubuntu 10.10 I made a boot stick, which works fine there but not on the computer in question (it tries for a while, then starts the old system)
- The third boot option according to the BIOS is booting from LAN, but I don't know how to do this

So I tried to follow the ubuntu documentation page for installation from Linux [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I downloaded unetbootin, but I don't know how to start it: 
- typing  ./unetbootin-linux-494 in the bash results in the message "permission denied"
- typing  sudo  ./unetbootin-linux-494 I am asked for the password, then get the message "command not found"

So I tried to follow the steps on the above page manually, which would be: download an iso-image (which I did), create a partition and put it there and boot from that. 
I don't manage to create a partition and booting without doing this didn't work either:
- I don't have gparted. Searching it via synaptic I find it, but installation fails because the package sources are at an invalid address (maybe there are no more edgy eft sources nowadays). Entering other resource addresses would maybe help but I don't know where to get them from.
- I tried to use cfdisk but didn't see any option for creating a new partition.
- I tried to use fdisk: Trying to create a new partition first gave the answer "no free sectors available". I had a big Linux partition from which I boot, a tiny swap partition and a tiny extended partition. This last one might or might not be just large enough to contain my iso-file. Since I didn't dare to delete the partition from which my linux is running, I decided to give it a try and deleted the tiny extended one, then created a new one at the same place. The manual on the above page tells me to set the file system type to ext3, but fdisk has no such option - how do I do this? Also, after having done the above my swap partition has disappeared. Will this cause problems when trying to reboot?

Exiting from the fdisk shell I got the message that the new partition table will only be valid after rebooting. Now I am afraid to reboot, because given my previous problems I might never be able to reboot again. Any suggestions (after you stopped laughing :-))?

Thanks!

---

### Post by khelben1979 on 2011-01-03
Have you considered taking out the cd-rom drive and used some ethanol on the lens inside it? It's not difficult and being very careful with it will solve this issue.

B.t.w. no laughing.

---

### Post by hurzilipochtli on 2011-01-03
Thanks, I did that now but the CD drive definitely doesn't work. Good thinking though - should have been the first thing to try out...

---

