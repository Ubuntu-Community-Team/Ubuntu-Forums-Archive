---
title: "Upgrade question"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by ArtLaForge on 2009-10-08
[B]Hi forum guru's:

I first installed Jaunty from the free cd 9.04, love it, but it was absolutely rock solid, everything worked perfectly, no challenge at all. So I downloaded Karmic on another machine, obviously at this stage I was not going to be a system tester, but the challenges were there to help me learn ubuntu. I started out with 32 bit and after reading the forums I decided to explore the 64 bit in spite of the driver issues, that has been fun. Enough babble, my question: After a few fresh installs I started to place my /home file on a separate hard drive. Soon I want to upgrade my 32 bit Jaunty machine to 64bit Karmic and my Karmic machine to the Lynx 64bit how will that effect the /home folder? I will backup, but should I format my /home and install completely fresh? ANY advice here would be appreciated. I will do it anyway just for fun. Without the forums I would really be struggling, you all do a great job Thanks a million.  :guitar:
[/B]

---

### Post by drs305 on 2009-10-08
You can leave your /home as it is if you prefer. When ext4 came out many users weren't completely comfortable with it (and still aren't) and so they kept their /home partition formatted as ext3 while running / with ext4. Just be sure you don't format /home when you upgrade/install.

I've had no problems with ext4 but still keep backups on an ext3 partition.

---

### Post by 3rdalbum on 2009-10-08
If you like a challenge, then dist-upgrade from Karmic to Lucid and keep up with the Lucid updates.

You will need to reinstall Ubuntu in order to go from 32-bit to 64-bit; just out of curiosity exactly what driver issues did you have? I've not heard of this on Linux as drivers can simply be recompiled for 64-bit.

As per your questions about the /home partition or hard disk, drs305 is right: Your /home won't be erased unless you actually tick the box to "format" it. It's perfectly safe to retain it for the new installation.

---

### Post by ArtLaForge on 2009-10-08
My driver issues were when I was using that other OS. Many of the driver issues were due to manufactures not supporting vista drivers. When I switched to ubuntu my HP all in one had not worked for months under vista because HP dropped support for the c6180, but it worked immediately after ubuntu install, however HP dropped support of the ink cartridge also, so I will have to buy a new printer when I can't find cartridges online anymore.

Thank you for the quick response's, I really appreciate that. I am using ext4 on all of my internal hard drives, but my backup's are on external drives with ext3 format.  :)

---

