---
title: "Prepare partitions step 4 of 8"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Jeaux on 2011-02-19
I've read posts on this subject but as this is the make or break of my system and every post seems to be individualized by different circumstances I'm making a new thread.  

I've install 10.04 with wubi on XP and am now trying an installation to it's own partition.  The end result will be a dual boot with XP and Ubuntu as options.  I've added a screenshot of the step I'm at and want to use the 5G space dev/sda3 to test what I'm doing.  I'm using Unetboot to try and achive this from XP as my CD is shot. If I select the aforementioned partition and click forward it tells me no root file system is defined.  If I click change...  all I know is FAT 16 FAT 32 and swap.  tbh I'm afraid to do anything for fear of screwing it up.  Plz advise as how to proceed

Many thx,
Joe

---

### Post by Dutch70 on 2011-02-19
Tick the format box in front of sda3 & format it to ext4 journaling file system.

After you format the partition, you should get a drop down box to select that partition as root. "/" will show up under "mount point" after you do that, then select forward.

---

### Post by Jeaux on 2011-02-19
Followed instructions and now get this error message. and found this.  

[http://ubuntuforums.org/archive/index.php/t-1237721.html](http://ubuntuforums.org/archive/index.php/t-1237721.html)

Are the unmount switches what I need to perform?

---

### Post by Dutch70 on 2011-02-19
> **Jeaux said:**
> Followed instructions and now get this error message.

[COLOR="Red"]EDIT:[/COLOR] Go back, close all applications & try it again.

Typically, "mounted" means that you are using it(opened applications) or have the ability to use it. Idk if you can unmount it, or if it would be easier to start all over & not do anything but the install.
 You should be home free after you get past that.

 I've never tried to use the system (web browser) while installing it. Although I thought you could.

---

### Post by Jeaux on 2011-02-19
Rebooted system and ONLY ran the installer.  Recieved same error message.  Any suggestions?

Considering the title and original message of this thread have been solved should I start a new thread in installation?

---

### Post by Dutch70 on 2011-02-19
> **Jeaux said:**
> Rebooted system and ONLY ran the installer.  Recieved same error message.  Any suggestions?

Considering the title and original message of this thread have been solved should I start a new thread in installation?

Yes, I think it would be a good idea to mark it solved & open a new thread with your new problem if necessary.

You can probably search this forum or google, I'm betting someone has had the same problem, and you won't have to wait for an answer.

Good luck

---

### Post by Jeaux on 2011-02-19
Many thx 4 ur time and expertise

---

### Post by Dutch70 on 2011-02-19
> **Jeaux said:**
> Many thx 4 ur time and expertise

You're quite welcome. 

certainly no expert, but many of us here have received a lot of help, so in turn, we want to help others whenever possible. 

I think you'll probably find that several of the people here answering questions, are waiting on an answer to a problem they can't solve. 

Welcome to the Ubuntu Forums Jeaux.

---

