---
title: "tried to upgrade to 10.10, now computer won't start"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by lupulin on 2010-10-19
Does anyone know a way for me to go back to my previous version of ubuntu? I had 8.04 and tried to upgrade to 10.10 and now the computer won't boot. I turn it on, the monitor goes into sleep and nothing happens. I put my 8.04 disk into the machine and tried to install ubuntu from there but it stops in the middle of installation and also becomes unresponsive. Is there anything I can do easily to get a functional version of ubuntu?

---

### Post by Hippytaff on 2010-10-19
How did you install it? if you downloaded the 10.10 iso are you able to boot from live cd?

---

### Post by Calash on 2010-10-19
Sounds like ether your disk is faulty or you have a hardware problem with your computer.

If the install of 8.04 stopped half way through the disk copy then there is not much we can do outside of suggest downloading the ISO again and trying with a new CD.  You may also want to run a CD cleaning utility and, if possible, run any system tests available on the computer in it's current state.  I believe the Ubuntu CD has a memory tester, try that as well.

---

### Post by lupulin on 2010-10-19
Thanks guys. I tried to update by downloading from the web here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I will try to burn a new install CD. Theoretically, if the CD is good, I should be able to install 8.04 with no problem, right?

---

### Post by lhb1142 on 2010-10-19
> **lupulin said:**
> Does anyone know a way for me to go back to my previous version of ubuntu? I had 8.04 and tried to upgrade to 10.10 and now the computer won't boot. I turn it on, the monitor goes into sleep and nothing happens. I put my 8.04 disk into the machine and tried to install ubuntu from there but it stops in the middle of installation and also becomes unresponsive. Is there anything I can do easily to get a functional version of ubuntu?

Try this < [http://www.dban.org/download](http://www.dban.org/download) >. Running DBAN on your computer will completely 'wipe' everything on your hard drive. (I hope you had backed up all your Documents, Music, Pictures, and Videos to an external hard drive.) Read the instructions about how to use DBAN; you'll be creating a boot medium so you want to set your BIOS to open first from your CD disk drive. It takes a few hours for DBAN to run completely, depending on the size of your hard drive (I let it run overnight).

Once your computer is 'wiped,' you can effect a 'clean' reinstallation of Ubuntu 10.10.

I hope this helps.

---

### Post by amjjawad on 2010-10-19
Don't get me wrong but this is very interesting problem ... I'd like to know what will happen.

Okay, first thing first, most likely you'll need to wipe everything and install Ubuntu again but as mentioned previously, I hope you have a backup for everything.

2nd step is: Boot from Ubuntu LiveCD and DO NOT install, just choose "try without installation".

3rd step: while you're on the live session, try to use GParted to format the root (/) partition and format the swap partition too.
If you have /home partition then keep it, DO NOT format it.

4th step: Try to install Ubuntu again. Try 8.10 or 10.10. I'd recommend to try 8.10 as 10.10 has lots of issues lately.

If nothing changed then ...

5th step: boot into the liveCD, choose "try ubuntu without installation" and use GParted to wipe everything. Remember, you need a backup for your important files before anything.

Few things you need to do:

1- Whenever you download any version of Linux, not even Ubuntu, it's always good to check the MD5sum. 
For Ubuntu, this is how: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2- Backup your important files. This is a must.

3- Always have a CD, DVD or USB as a rescue media so that you could boot into your PC when other media fail to do so.

4- The more problem you get, the more experience you'll have and eventually you'll fix your own problems so don't panic :)

5- Good luck :D

---

### Post by sikander3786 on 2010-10-19
> I put my 8.04 disk into the machine and tried to install ubuntu from there but it stops in the middle of installation and also becomes unresponsive. 

Don't forget to check the integrity of downloaded image before burning it to disc. It always saves you from lots of problems.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

> I should be able to install 8.04 with no problem, right?

Why don't you try downloading the latest versions, either 10.04 or 10.10 and do a clean install.

I know 8.04 is still officially supported but 10.04 supports newer hardware and works fine most of the time as does 10.10.

---

### Post by lupulin on 2010-10-19
> **sikander3786 said:**
> Don't forget to check the integrity of downloaded image before burning it to disc. It always saves you from lots of problems.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)



Why don't you try downloading the latest versions, either 10.04 or 10.10 and do a clean install.

I know 8.04 is still officially supported but 10.04 supports newer hardware and works fine most of the time as does 10.10.

I guess I will be trying a clean install since my 8.04 disk is messed up according to the disk scan and I don't even know where I'd get another 8.04 disk. I got a 10.10 disk from a friend.

Foolishly, I did not have everything backed up. He suggested I partition the hard drive at install. Hopefully that will work, unless that's a silly idea.

---

### Post by 29732 on 2010-10-19
> **lupulin said:**
> I don't even know where I'd get another 8.04 disk.
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
and being off topic, anyone knows what the very first ubuntu was like? im curious :)

---

### Post by sikander3786 on 2010-10-19
> I did not have everything backed up.

If there are some important files, once the Live CD boots successfully, you can mount your related partitions and copy your data over to a safe location. I would actually recommend doing that as backing up is always a safer approach.

---

### Post by lupulin on 2010-10-19
> **sikander3786 said:**
> If there are some important files, once the Live CD boots successfully, you can mount your related partitions and copy your data over to a safe location. I would actually recommend doing that as backing up is always a safer approach.

Thanks! I assume there will some options which are fairly obvious as to partitioning and how to do so when I load the new CD. I'll report back after the new install.

---

### Post by amjjawad on 2010-10-19
> **lupulin said:**
> Thanks! I assume there will some options which are fairly obvious as to partitioning and how to do so when I load the new CD. I'll report back after the new install.

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

---

### Post by opdiebokke! on 2010-11-07
Same happened to me...why is it that EVERYTIME I upgrade my uBuntu, I have to jump through hoops to get it to boot properly again. This has been ongoing for four years now - I eventually opted for the LTS this year, and yesterday I ran the update - hadn't done one in months (fearing this scenario), and the infernal machine won't boot uBuntu again...so back to Windows: at least GRUB is ok...

---

### Post by thatsmyboy on 2010-11-07
> **29732 said:**
> anyone knows what the very first ubuntu was like? im curious :)

Ok curious [here you go]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_4.10_.28Warty_Warthog.29")!

---

