---
title: "Trouble Installing GRUB onto RAID0 Array"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Banacek on 2009-01-04
I've installed Ubuntu desktop Intrepid Ibrow onto a fakeRAID array using an IDE Promise 20276 RAID MBFastTrak133 Lite controller and have tried using the [FakeRAID Guide]("https://help.ubuntu.com/community/FakeRaidHowto"). After the Ubuntu install I start the process to install GRUB but I get this:

```
ubuntu@ubuntu:~$ sudo mkdir /target
mkdir: cannot create directory `/target': File exists
ubuntu@ubuntu:~$ sudo mount /dev/mapper/pdc_iighbfdg2 /target
ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev
ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /target/sys
ubuntu@ubuntu:~$ sudo chroot /target
bash: groups: command not found
root@ubuntu:/#
```

The pdc_iighbfdg2 is my / partition and my /boot partition would be at 1.

Then there's this:

```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "pdc_iighbfdg" already active
RAID set "pdc_iighbfdg1" already active
RAID set "pdc_iighbfdg2" already active
RAID set "pdc_iighbfdg3" already active
RAID set "pdc_iighbfdg5" already active
RAID set "pdc_iighbfdg6" already active
RAID set "pdc_iighbfdg7" already active
RAID set "pdc_iighbfdg8" already active
ubuntu@ubuntu:~$ sudo dmraid -s
*** Active Set
name   : pdc_iighbfdg
size   : 240206080
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
ubuntu@ubuntu:~$ cd /dev/mapper
ubuntu@ubuntu:/dev/mapper$ ls
control       pdc_iighbfdg1  pdc_iighbfdg3  pdc_iighbfdg5  pdc_iighbfdg7
pdc_iighbfdg  pdc_iighbfdg2  pdc_iighbfdg4  pdc_iighbfdg6  pdc_iighbfdg8
ubuntu@ubuntu:/dev/mapper$ sudo modprobe dm-raid45
FATAL: Module dm_raid45 not found.
ubuntu@ubuntu:/dev/mapper$ sudo dmraid -r
/dev/sdb: pdc, "pdc_iighbfdg", stripe, ok, 120103040 sectors, data@ 0
/dev/sda: pdc, "pdc_iighbfdg", stripe, ok, 120103040 sectors, data@ 0
ubuntu@ubuntu:/dev/mapper$ 

```

The modprobe is telling me there is no dm_RAID45 but the others are seeing my RAID0 partitions just fine and telling me they exist. What the hell is going on here?

---

### Post by Banacek on 2009-01-13
Does anybody know what to do for this?

---

### Post by uk_freelancer on 2009-01-13
I too had a similar problem with my fake RAID0 setup and no matter what I tried using fakeRAID to get around this problem the installation caused errors to spring up during and after installation. It was at this point I was ready to call it a day and stick with Vista.

However, when all else fails, sometimes you have to find a compromise that in my case meant I had no other choice but to disable my RAID ARRAY completely and have my two hard disks independent of each other..  Once I did this I re-installed Vista (need it only to play some graphic intensive games) on one hard disk and on the second hard disk I created 13 Gigs of free space for Ubuntu 8.10. Installing Ubuntu was now a breeze, no errors during the installation and GRUB now works flawlessly. I now have both OS's working as they should side by side and Ubuntu works right-out-of-the-box. I have not noticed any degrade in speed in loading/using vista so disabling my RAID ARRAY was not such a high price to pay in installing Ubuntu.

Hope this helps.

---

### Post by Banacek on 2009-01-14
That's not an option for me. I **had** an install of Gusty Gabon and was trying to install 8.04 desktop. I have had my /home directory as a separate partition and with the new installation I need it to be kept as it is without being formatted. Doing what you did would lose everything on that partition.

---

### Post by hotweiss on 2009-01-14
you can use the alternate CD or you can use my guide:

[http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/](http://seethisnowreadthis.com/2008/12/25/how-to-set-up-soft-raid-dmraid-in-linux-mint-6-felicia/)

---

### Post by Banacek on 2009-01-14
I'm not sure when I'll be able to download and make an alternate CD and that guide is near the same to the guides I've already seen. It does not explain why chroot would break bash and how to fix it. What seems to be happening here is that on doing "sudo chroot /target" bash breaks. Why would chroot break bash and what can be done about it?

---

### Post by caljohnsmith on 2009-01-14
Instead of using "sudo chroot /target", how about trying:
```
sudo chroot /target /bin/bash
```
And does that return an error?

---

### Post by Banacek on 2009-01-14
Yes

```
ubuntu@ubuntu:~$ sudo modprobe dm-raid4-5
ubuntu@ubuntu:~$ sudo dmraid -ay         
RAID set "pdc_iighbfdg" already active   
RAID set "pdc_iighbfdg1" already active  
RAID set "pdc_iighbfdg2" already active  
RAID set "pdc_iighbfdg3" already active  
RAID set "pdc_iighbfdg5" already active  
RAID set "pdc_iighbfdg6" already active  
RAID set "pdc_iighbfdg7" already active                               
RAID set "pdc_iighbfdg8" already active                               
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: pdc, "pdc_iighbfdg", stripe, ok, 120103040 sectors, data@ 0
/dev/sda: pdc, "pdc_iighbfdg", stripe, ok, 120103040 sectors, data@ 0                                        
ubuntu@ubuntu:~$ sudo dmraid -s                                       
*** Active Set                                                        
name   : pdc_iighbfdg                                                 
size   : 240206080                                                    
stride : 128                                                          
type   : stripe                                                       
status : ok                                                           
subsets: 0                                                            
devs   : 2                                                            
spares : 0                                                            
ubuntu@ubuntu:~$ cd /dev/mapper                                       
ubuntu@ubuntu:/dev/mapper$ ls                                         
control        pdc_iighbfdg2  pdc_iighbfdg6                           
pdc_iighbfdg   pdc_iighbfdg3  pdc_iighbfdg7                           
pdc_iighbfdg1  pdc_iighbfdg5  pdc_iighbfdg8
ubuntu@ubuntu:/dev/mapper$ sudo mkdir /target
ubuntu@ubuntu:/dev/mapper$ sudo mount pdc_iighbfdg2 /target
ubuntu@ubuntu:/dev/mapper$ sudo mount --bind /dev /target/dev
ubuntu@ubuntu:/dev/mapper$ sudo mount -t proc proc /target/proc
ubuntu@ubuntu:/dev/mapper$ sudo mount -t sysfs sys /target/sys
ubuntu@ubuntu:/dev/mapper$ sudo chroot /target /bin/bash
bash: groups: command not found
root@ubuntu:/#

```

There didn't use to be such a problem with chroot and bash back when Gusty was the latest. Did they foul something up in the repositories regarding bash or chroot since then?

---

### Post by Banacek on 2009-01-26
Okay, I finally got use of another machine (with internet access) long enough to download the ISO of the text based installer and burn it to CD-R. (Before, it wasn´t feasible to download an image of near 700 MB to working RAM as per the LiveCD. I had to download it onto a USB memory stick. Using the LiveCD I couldn´t get the image from USB burned to CD-R without it being corrupted.) The text based installer for Ubuntu 8.10 i386 worked like a charm and I now have Intrepid Ibrow up, running nicely.

However, before when I installed Gusty and then Hardy the LiveCD desktop installers both worked just fine as long as I followed the [FakeRAID Guide]("http://wiki.auzigog.com/My_Ubuntu_(7.10)_Installation"). Nown, not only does it not work using the Intrepid LiveCD but when I tried a reinstall of Gusty or Hardy the LiveCD wouldn´t get the job done either. Did somebody foul up on a new version of one of the files the job uses? I would still like to know what was going on with that.

---

