---
title: "Disk Error, Memtest +86 won' start, ubuntu won't start"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by redmorning on 2010-10-24
Hi,

I'm using ubuntu for about 4 years and till today i always found my answers in the forums, google... but tonight i'm stuck. I need some help please.

Hardware:
Acer Aspire X Timeline 3820TG
OS
Ubuntu 10.04, latest kernel (can.t rememver now) [Dual boot with windows 7]

Story;

In the last boots i was getting disk checks but last two times i skipped this check (once i saw message that there are errors on disk). About 5 hours ago my pc hibernated because of critically low battery. (Normally -most of time- when i plug in charge ,when it boots up i get my all programs running, clean). This time when i restarted my laptop i got a blank screen. It looks like the system is running (i understand that because of the fan, it turns really fast) but not responding, just blank screen. After first try i booted the pc many times but the result doesn't change, blank screen. From grub menu i chose ubuntu recovery, it did some checks (i can't follow all the actions, it is a little bit fast) and stucks at the end, like battery information. I tried memtest for testing the drives but when i chose memtest from grub menu i can only see blue screen for two seconds and it disappers and reboots.

Now i'm on the dual windows 7.

So i can reach to command line from the grub menu, but i don't know what to do because i don't know what is the problem exactly. I need your help to discover the problem. The command line is not same as the terminal, that's why i am stuck, i can not reach anything in this command line.

For tomorrow i have to complete a project and all my development environment is on ubuntu. So this is urgence.

Thanks in advance.

---

### Post by spiky001 on 2010-10-24
Try booting into live cd 1st see what yo can accsess from there, you will also need that for repairing system

---

### Post by redmorning on 2010-10-24
hi skipy001,

i don't have a cdrom, but i will create a usb startup disk and boot with that. Without live cd (usb) can i see what is wrong in the command line (in grub menu) ?

---

### Post by spiky001 on 2010-10-24
You will be able to get a normal terminal with live usb

---

### Post by redmorning on 2010-10-24
it is a little cheap question but do you know a unetbootin equal program to create bootable usb in windows?

edit: nevermind, i got it, trying now. i will let you know.

---

### Post by redmorning on 2010-10-24
i got in the system with bootable usb, looked at the /etc/fstab; for the "/" directory it says "errors=remount-ro". I changed this parameter to "defaults" but this silly solution didn't work of course. now i can reach to my system but don't have internet connection because the modems ethernet port doesn't work and as you know for wireless we need drivers.

What you advice me to look, what could be the reason that makes me get blank screen?

edit: now i am in the live usb and i can reach to my system. Could you help me a little more

---

### Post by swoody on 2010-10-24
Firstly, I would recommend to make backups of anything you can before continuing. If you can boot from a liveCD/USB and copy any important data/documents/pictures/etc. to another device/CD/what-have-you it may save you a headache down the road. These suggestions are very safe, but there is always a chance for data loss when working with file systems.

This could be one of a couple issues. From the sounds of it your filesystem may have been damaged when your computer was shutdown abruptly. It also sounds like this may be a physical hard-drive issue and may need to be replaced before it *really* gets bad.

What company is your drive made by? Most manufacturers offer a hard drive testing tool which can be booted from a liveCD (or in your case using the same USB creator program you used previously). I would *highly* recommend downloading and running that. Do be careful, as with some of these tools, they have an option to format your drive as it's tested. Make sure not to select that option if it's available ;) I would also recommend running a "full test" with these tools instead of a "short test". This will take a bit longer to run, but will be much more thourough and will have a better chance at detecting any issues.

If your hard drive passes the test without issue, I would then run fsck as many times as needed to try and get your system to boot safely again. When you changed "errors=remount-ro" it didn't fix the issue, it simply told your computer to ignore the issue and attempt to mount the partition regardless if it had errors.

Edit: I just noticed you indicated that you are on the liveUSB now. Run "sudo fdisk -l" and it should show your hard drive and USB. Now, making sure you have identified the correct drive, run:

```
sudo fsck -fyC /dev/xxx
```

where xxx is your faulty partition (sda1, sda2, sdb1, etc.). Please note that you may need to run this a few times to restore functionality to your drive. If after several attempts at fixing this still doesn't let your system bootup, let us know as this is a sign of a more serious error.

Please let us know if you have any other questions, or if this doesn't work for you :)

- Woody

---

### Post by redmorning on 2010-10-24
Hello swoody

thank you very much for your help. i am backing up some of my important files. i will let you know in a short time.

---

### Post by redmorning on 2010-10-24
swoody!
You saved my life and teached me a short but valuable information. thank you. after checking filesystem i got a long output. It fixed my filesystem. Now i am back in my beatiful box/environment. \\:D/

Thank you very much again.

Ciaou!


```

ubuntu@ubuntu:~$ sudo fsck -fyC /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
                                                                              
Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 3571984: 7193056
Multiply-claimed block(s) in inode 3588122: 7193056
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 2 inodes containing multiply-claimed blocks.)

File /var/lib/gdm/.gconfd/saved_state (inode #3571984, mod time Sun Oct 24 17:01:49 2010)
  has 1 multiply-claimed block(s), shared with 1 file(s):
    ... (inode #3588122, mod time Sun Oct 24 16:12:11 2010)
Clone multiply-claimed blocks? yes

File ... (inode #3588122, mod time Sun Oct 24 16:12:11 2010)
  has 1 multiply-claimed block(s), shared with 1 file(s):
    /var/lib/gdm/.gconfd/saved_state (inode #3571984, mod time Sun Oct 24 17:01:49 2010)
Multiply-claimed blocks already reassigned or cloned.

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity                                       
Pass 4: Checking reference counts
Unattached inode 3588122
Connect to /lost+found? yes

Inode 3588122 ref count is 2, should be 1.  Fix? yes

Unattached inode 4997129                                                      
Connect to /lost+found? yes

Inode 4997129 ref count is 2, should be 1.  Fix? yes

Pass 5: Checking group summary information                                    
Block bitmap differences:  -9998339 +9998340 +(11157593--11157595) +(11169128--11169141) -12144866 -12147069 -(20678680--20678683) -20678688 -(20678696--20678697) -(20678704--20678713) -(20678720--20678723) -(20678728--20678734) -(20701221--20701230) -(20701237--20701254) -(26613760--26613770) -(26613783--26613793)
Fix? yes

Free blocks count wrong for group #0 (32166, counted=32165).                  
Fix? yes

Free blocks count wrong for group #340 (13796, counted=13779).
Fix? yes

Free blocks count wrong for group #370 (0, counted=2).
Fix? yes

Free blocks count wrong for group #631 (11732, counted=11788).
Fix? yes

Free blocks count wrong for group #812 (32164, counted=32186).
Fix? yes

Free blocks count wrong (28875932, counted=28875994).
Fix? yes

Inode bitmap differences:  -3539839 +3588122 -4997125 +4997129 -6062461 -6062545 -10338330 -10338463 -10338465 -(10338469--10338470) -(10338480--10338482) -(10338487--10338488) -10338491 -13303811 -13303816 -(13303818--13303819)
Fix? yes

Free inodes count wrong for group #216 (10111, counted=10112).                
Fix? yes

Free inodes count wrong for group #219 (16359, counted=16358).
Fix? yes

Free inodes count wrong for group #370 (14994, counted=14996).
Fix? yes

Free inodes count wrong for group #631 (15256, counted=15267).
Fix? yes

Free inodes count wrong for group #812 (16367, counted=16371).
Fix? yes

Free inodes count wrong (18513353, counted=18513370).
Fix? yes


/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 410150/18923520 files (1.3% non-contiguous), 8965802/37841796 blocks



```

edit: i also want to mension that i guess ubuntu is not very succesful at hibernate mode, i experinced this hibernate problem for a few times but it is enough for me to change the battery preference "when battery critically low : hibernate" to "shut down". i am not sure if this is safer but hibernate is a little bit mixing things. if you have any idea or experience on this hibernate issue, share with me please.

---

