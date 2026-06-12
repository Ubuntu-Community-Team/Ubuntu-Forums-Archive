---
title: "Boot crash graphic glitch"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by jjwilsontech on 2009-07-22
Greets all! I have Ubuntu 9.04 and I've been pretty successful at kicking my Windows habit but I've hit a snag. I tried upgrading my Ati radeon driver and now when my computer boots I see about a third of my desktop background for about 3 seconds then it is gone replaced with jumbled garbage. I am a total linux rookie so I am stuck. Can anyone give me the steps restore the old drivers from root.. or any other ideas. xfix definitly made no change.

---

### Post by prshah on 2009-07-22
> **jjwilsontech said:**
> then it is gone replaced with jumbled garbage. 

See [this post (with screenshots)]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") to see if your problem matches, as well as a potential solution.

---

### Post by jjwilsontech on 2009-07-22
Thank you for the reply. I have been doing some reading and I do think the problem is in the xorg.conf but I cannot seem to access the /ect /ect/X11 or /ect/X11/xorg.conf My screen is scrambled so I am doing it from recovery through root and yes I did login with my pw and I used sudo nano /etc/X11/xorg.conf but it cannot see the file and seems to create a new one.

---

### Post by prshah on 2009-07-22
> **jjwilsontech said:**
> am doing it from recovery through root and yes I did login with my pw and I used sudo nano /etc/X11/xorg.conf but it cannot see the file and seems to create a new one.

When you boot in recovery mode, it does not load your installations' settings and files, but creates a "virtual" filesystem with the defaults.

You can do it through recovery mode, but you need to manually mount your linux installation. This is slightly complicated.

You can do it more easily by loading in regular mode, and at the scrambled screen, press Ctrl+Alt+F1 to get a virtual terminal.

However, if you want to do it in recovery mode anyway (or if your virtual terminal is scrambled as well), use the commands (Note that in recovery mode, you do not need to use "sudo")```
mount /dev/sda1 /mnt -o defaults,rw
nano /mnt/etc/X11/xorg.conf

```

Replace /dev/sda1 with the actual linux partition that is mounted as root; use ```
fdisk -l
``` to list your partitions, and look for partitions with id of 83 (type of Linux).

Post back if you need further instructions or assistance.

---

### Post by jjwilsontech on 2009-07-22
I still cannot use the virtual terminal so I am using the recovery still. I have mounted the drive which turns out to be sdb5 but opening the file still only brings up a new file :(

---

### Post by jjwilsontech on 2009-07-22
I'm formating the whole system and starting over. I might just leave the drivers alone. Who cares if wow has 4 FPS....

---

### Post by jjwilsontech on 2009-07-22
Thank you for all your help in my frustration you taught me quite a bit about linux :)

---

