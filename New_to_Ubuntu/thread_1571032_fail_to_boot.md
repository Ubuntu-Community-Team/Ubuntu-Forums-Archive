---
title: "fail to boot"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by mapman88 on 2010-09-09
I have 10.04 that will not boot up after a week of being shut down normally. I get a boot screen that recognizes my 320 gb hard drive, DMI data pool message, then skips to blank screen with cursor blinking upper right. After 30 minutes get ubuntu screen with message drive not ready,  F to Fix, I to Ignore, S to Skip, M to Manual recovery. I pressed F to fix, get message "Disk drive for /tmp is not ready or not present" "Continue to wait, S to Skip, M to Manual recovery". Then I tried I for Ignore, and I am currently on an Ubunto screen for 30 minutes, nothing happening.
 
Please help! thanks

---

### Post by jtarin on 2010-09-09
> will not boot up after a week of being shut down normally.What happened before this period of a week? What software have you installed that you can remember? Possibly something has borked your Grub configuration.A possible Live CD Grub reinstall is what's needed.

---

### Post by mapman88 on 2010-09-09
I think the youtube "Downloader" was upgraded, and I also installed Guayadeque music player, and I have an external HD with music on it. I am running 10,04, but only have a 9.10 live CD. Should I get a 10.04 CD or USB to fix the GRUB?

---

### Post by jtarin on 2010-09-09
> **mapman88 said:**
> I think the youtube "Downloader" was upgraded, and I also installed Guayadeque music player, and I have an external HD with music on it. I am running 10,04, but only have a 9.10 live CD. Should I get a 10.04 CD or USB to fix the GRUB?
9.10 if my memory serves me correctly :p  has Grub2. Is Ubuntu your only operating system on that disk?

---

### Post by jtarin on 2010-09-09
This is the method I prefer. If your Grub is not installed in The MBR there are 2 steps that will need to be modified slightly.
[Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2")>METHOD 3 - CHROOT

---

### Post by mapman88 on 2010-09-09
Thanks Jtarin,
 
I am at work right now, will try this tonight when I get back to my room. I looked over method 3 and am hopeful it works. This computer has only ubuntu on it. I purchased a new hard drive for it when I loaded 9.10 on it about January - when 10.04 came out I went through the upgrade process. I have been running fine since 10.04 upgrade, mostly listening to music, downloading some youtube, and surfing the internet. I have this computer in my room at a remote worksite where I am there a week and at home a week. Sometimes I leave the computer on when I am gone, and sometimes I power down when I leave. thanks again for the advice.

---

### Post by jtarin on 2010-09-09
I have used that method successfully several times. I like to move partitions around and Grub complains sometimes so I use that to quieten it down.

---

### Post by mapman88 on 2010-09-10
On my broken computer I am able to boot to my 9.10 liveCD, but it is 32 bit and I was running 10.04 64 bit, which it says updating GRUB might not work with that conflict. I have downloaded 10.04 64 bit and tried to create a bootable flash drive, but it didn't seem to work. I will research that some more, or try to burn a ISO disc.

---

### Post by mapman88 on 2010-09-21
On my Gateway computer I installed a new hard drive about January and put only Ubuntu 9.10 on it. In April I upgraded to 10.04. I have been running ok until recently I could not boot up. (See beginning of this thread). I was finally able to reload a new copy of 10.04, which worked for a few days until - Three days ago, I could not boot up again, same symptoms. I tried to reload 10.04 new again, but the install hangs at the very end (for hours). After the hang up install, which I end by turning the power off, I can boot off the CD and in terminal, see I have 10.04 installed on my hard drive, but cannot get the hard drive to boot. Last night I tried to install 9.10 Live CD and overwrite 10.04 - same thing, the install hangs up at the end, for hours. The only thing I can do is shut the power off, and then I cannot boot my computer, can only boot to CD, which of course hangs up on yet another install. So I am hanging up whether booting up to my computer, or installing 9.10 or 10.04. Any suggestions? 
 
I was thinking of booting to the CD, and formatting my hard drive before trying to install, (I have had so many install failures), but I am not sure how to format tha hard drive from CDLive.

---

### Post by jtarin on 2010-09-21
I'm not sure of your partition or disk setup so you might want to use Gparted.

---

### Post by mapman88 on 2010-09-21
My last install attempt (9.10), which ran for eight hours at 98%, was still running at 99% complete at 12 hours. I will be able to check it again tonight and see how it is doing. When I install ubuntu, I always have let the software partition as it wants to. I tried to partition for a separate home partition, but it didn't work for me, so I just let ubuntu install using the entire disk. I think I end up with partitions sda1, sda2, and sda5(swap)

---

### Post by mapman88 on 2010-11-10
I installed a hard drive out of an older machine I had, loaded ubuntu, and fired right up. I guess the new 320gb hard drive I had failed after six months, oh well.....

---

### Post by wkhasintha on 2010-11-11
glad you have solved it bro. mark the thread as solved

---

