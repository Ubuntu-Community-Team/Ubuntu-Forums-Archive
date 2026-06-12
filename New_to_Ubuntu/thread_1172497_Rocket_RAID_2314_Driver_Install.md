---
title: "Rocket RAID 2314 Driver Install"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by cbanakis on 2009-05-28
Help, Please.

So Frustrated.

I'm trying to get my (HighPoint - Rocket RAID 2314) to work in Ubuntu.

I'm using Ubuntu Server 8.04 64bit With the gnome-core installed.

The drivers are available for Ubuntu by the manufacturer at this page.
[http://www.highpoint-tech.com/USA/bios_rr2314.htm](http://www.highpoint-tech.com/USA/bios_rr2314.htm)

I got all the RAID management software to work, (not sure how, but it works now) LOL

But no matter what I do, the driver is not working.

When I run "install.sh" I get the following..

"The disk you insert is for linux kernel 2.6 Please reboot the system to use the new driver module."

When I run "uname -r" it shows that my kernel version is 2.6.24-23-server

Am I doing something wrong, or does HighPoint just have bogus drivers on their site?

---

### Post by cbanakis on 2009-06-04
Seriously?
No one knows?
LOL
We'll I've sacrificed allot in order to get windows out of my life, but there is no chance I am gonna ditch my 26TB file server...
I have been back and fourth with High Point about this, and they keep giving me drivers that all do the same thing.
Their support is by email only and I'm not sure if they even understand my requests.

They often reply with an answer to a question I did not ask, instead of answering what I did ask.

Please Please Please...
There has to be someone out there who can help me with this.

I have 12TB's of data I have not been able to access for over 2 weeks and I'm shaking in withdrawal.

---

### Post by ronparent on 2009-06-04
I presume you have been following the instruction in the driver manual (of course it may require additional interpretation). Have you completed Step 2 in setion 3? Also have you checked whether or not the driver is installed per section 4 (ie "Checking Devices Status
    Using the following command to show driver status:
           # cat /proc/scsi/rr2310_00/x"

I think that what the message "The disk you insert is for linux kernel 2.6 Please reboot the system to use the new driver module." is telling you is merely that the system has to be rebooted for the driver to become active. Step 2 of section 3 of the manual was telling you what to add to /etc/fstab for the raid's file system to be mounted. You may already be operational once the raid drive is mounted! Let us know how you make out.

---

### Post by cbanakis on 2009-06-05
Thank you for your reply

ok, so I do the following...

           chris@File-Server:~$ cd Desktop
           chris@File-Server:~/Desktop$ cd driver
           chris@File-Server:~/Desktop/driver$ sudo sh install.sh

And I get this...

           The disk you insert is for linux kernel 2.6
           Update initrd file /boot/initrd.img-2.6.28-11-server for 2.6.28-11-server
           Please reboot the system to use the new driver module.

Then after re-booting, I run this...

           cat /proc/scsi/rr2310_00/x

And all I get is

           No such file or directory

-----

I'm gonna lose my hair before I figure this out!

---

### Post by cbanakis on 2009-06-06
Is there any way I can just pay someone money to remote desktop to my system and make this work.

I'm not sure what price would be fair, but I need to get this working.

I literally cannot sleep because I know this isn't working.

Its driving me nuts

---

### Post by cbanakis on 2009-06-06
Now, I'm thinking the driver is not the problem..
It is listed as an active restricted proprietary driver in System>Administration>Hardware Drivers

Maybe the problem lies with their RAID Management Console?

When I try to connect to the controller card, it says "System Unreachable"

The instructions for installing the RAID Management software say I need to have "gtk library v1.2 shared libraries" installed

I have no idea what that is, and when I search in package manager, I get thousands of results...

And I assume it wont help my cause if I just install all of them, Especially if the one I need is installed already

---

### Post by ronparent on 2009-06-06
Have you edited the /etc/fstab to mount the raid drive? Where is it mounted?

---

### Post by cbanakis on 2009-06-06
I did paste the line from the instructions in fstab
I'm not sure what that is for though...
there are 20 hard drives connected to the card, and they all show up in "computer" Even before I installed the driver.
my problem is that the 20 drives should only be detected as 1 drive, and I can't set it up because the RAID Management software cannot communicate with the card to recognize the array

---

### Post by ronparent on 2009-06-06
At this point I am over my head. Why don't you post in the servers forum to get some specific advice. I sense that your raid drives are ok but you do need specific instuctions to properly access them with your raid controller.

---

### Post by micster on 2009-06-10
I'm also trying to get my rocketraid to work, but with 9.04 Have you configured the RAID within the BIOS already? I have yet to download the drivers, but we will see if I have any more luck.

---

### Post by cbanakis on 2009-06-12
> **micster said:**
> I'm also trying to get my rocketraid to work, but with 9.04 Have you configured the RAID within the BIOS already? I have yet to download the drivers, but we will see if I have any more luck.
I am also trying to use 9.04...
I'm using 20 drives in a single array, and the RAID BIOS does not support that.

I have a few custom built drivers from High Point that will allow 20 drives using the RAID Management software.

So far I have collected the following...

A Windows driver with 20 drive support
A Ubuntu 8.04 driver with 20 Drive Support
2 versions of Ubuntu 9.04 drivers with 20 drive support
And an Ubuntu 9.04 driver without 20 drive support

If you can get me your contact info, I will gladly send you whatever you need.

Maybe you can get it working, then tell me how the heck you did it :)

I seem to be able to install the drivers correctly, but the RAID Management software cannot see the hardware

---

### Post by micster on 2009-06-12
Well, I don't have 20 drives... I only have 4 striped together in a RAID 0, but I GOT IT TO WORK!

I had been configuring my RAID through the BIOS, but then I came across [this information]("http://debianclusters.cs.uni.edu/index.php/HighPoint_RocketRAID:_Installation") that said to use the management utility provided by HighPoint. So I installed that (had to use Alien to convert the .RPM into .DEB) but still could not get Ubuntu to see the 4 drives as one large disk.

So I compiled the driver from source located at the bottom of [this page here]("http://www.highpoint-tech.com/USA/bios_rr2314.htm"). The instructions are included with the download, but it is really simple. I just entered the directory I had untar'd the files to and issued:
```
make
sudo make install
``` After rebooting the drives were all seen as one HUGE drive automagically.

I ran into some more problems once I tried creating a partition and formatting. Not really sure what was going wrong, but I was getting a bunch of read/write errors. I eventually used gparted and created a GPT partition table and formatted with XFS. Which finally seemed to work.

I added the new array to my /etc/fstab and now it mounts every time. My file transfers right now are really really slow though. I'm not sure exactly why. It might be that one of my hard drives is getting ready to die and causing problems or maybe I'm using USB 1.0 instead of USB 2.0 for the external drive that I'm transferring from.

I realize that my situation was not the same as yours, but I do have my HighPoint RocketRaid 2314 successfully connected to my Ubuntu 9.04 and mounting, which is better than nothing.

---

### Post by micster on 2009-06-12
> I seem to be able to install the drivers correctly, but the RAID Management software cannot see the hardware

I first tried installing the pre-compiled drivers and they appeared to work and install, but issuing the command```
sudo fdisk -l
``` would still list each drive individually. My Bios would always see the drives even before I installed any drivers. After compiling my own drivers, Ubuntu started seeing them as one drive.

If Ubuntu can see your hard drives but the RAID Management Utility can not, I think you have a different problem.

I downloaded and installed the GUI Based "GUI Linux v3.13-4" from [HighPoint]("http://www.highpoint-tech.com/USA/bios_rr2314.htm") which unzips as a couple of .RPM packages that you have to convert to .DEB (instructions are included I believe). There are two scripts that it installs: hptsvr and hptraid. I had to create a config file for the hptsvr located in```
/etc/hptcfg
``` which I only typed one thing in it, the name of the driver module ```
rr2310_00
``` after starting hptsvr and logging into it with hptraid I was able to initialize my drives and configure the array.

Hope that helps, good luck.

-Mic

---

