---
title: "Just Updated to 10.04 - Says error: the symbol Grub_puts"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by hollowtd on 2010-04-30
Just Updated to 10.04 - Says error: the symbol Grub_puts_not found
grub rescue> 

Any ideas what to do. I know it's on there but looking in the wrong partition (I have mac os and ubuntu on one machine)

Thanks

---

### Post by Sealbhach on 2010-04-30
Hi, please try these instructions here to reinstall Grub from the Live CD:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Here is an explanation of what might have happened to cause this error message:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509797/comments/2](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/509797/comments/2)

Good luck.
.

---

### Post by hollowtd on 2010-04-30
Tahnks. I'll give those a shot too. thanks

---

### Post by hollowtd on 2010-04-30
I am capable of doing most everything myself with help from such a great community, but this is a little hard for me. I am downloading the livecd now. Does anyone want to walk me through this this weekend? I can make a phone call if anyone knows how to help me with this and walk me through it. This seems really difficult and I'd love to access the new 10.04 soon. It's on here somewhere.

---

### Post by Sealbhach on 2010-04-30
Hi, maybe this documentation makes it easier to follow?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

It's really just a matter of following the instructions given, the only thing you need to be careful with is getting the right partition e.g. sda1, or sda2 etc.

You can find out by looking at fdisk -l. Maybe post the result of that here, and we can give you the correct commands to use?

.

---

### Post by hollowtd on 2010-05-01
Here is the readout I get for my HD. I'm not sure what all the partitions are: I should have maybe one swap, one for MAC (30 gig or so) and one for Linux (8 or 9 gig). 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     92422183  Mac OS X HFS+
 3       92422184     92424137  Unknown
 4       92424138    116066716  Basic Data
 5      116066717    117210206  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     92422183  af  Mac OS X HFS+
 3 *     92422184     92424137  ef  EFI System (FAT)
 4       92424138    116066716  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 92422184:
 Boot Code: Unknown, but bootable
 File System: Unknown
 Listed in GPT as partition 3, type Unknown
 Listed in MBR as partition 3, type ef  EFI System (FAT), active

Partition at LBA 92424138:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 116066717:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


Do you know then what I might type in in terminal then so that I don't get confused?

---

### Post by Sealbhach on 2010-05-01
You need to do fdisk -l to get the sda names.

```
sudo fdisk -l
```

.

---

### Post by hollowtd on 2010-05-01
Ok I'll try that and show it. Well, give me a minute. I'm making the Live CD first. Thanks

---

### Post by hollowtd on 2010-05-01
Here is what it reads

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        5754    46006272   af  HFS / HFS+
/dev/sda3   *        5754        5754         977   ef  EFI (FAT-12/16/32)
/dev/sda4            5754        7225    11821289+  83  Linux
ubuntu@ubuntu:~$


*I know with Leopard, I've got like 30 gig free. On Ubuntu I have around 7 or 8 gig free if that helps distinguish which is which. And, I have been using reFit before when I boot my computer.

---

### Post by hollowtd on 2010-05-01
Anyone got any ideas as to what to type in to get grub 2 working again?

---

### Post by Sealbhach on 2010-05-01
Hi, your Linux partition is on /dev/sda4.

Now here's what you need to do with the Live CD:

Boot to the LiveCD Desktop.

Open a terminal by selecting *Applications,  Accessories, Terminal* from the menu bar. 

```
sudo mount /dev/sda4 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Shut down the Live CD session and remove CD.

Reboot.

Refresh the GRUB 2 menu with 

```
sudo update-grub
```

.

---

### Post by hollowtd on 2010-05-01
Should I boot into the live CD then and then run the terminal commands?

What If I've got reFit on my computer? What usually happens is I turn on the computer and then it goes to reFit and I can choose mac os or linux. Will this still happen once I restart?  

Thanks again ps. How can you tell it's sda4? Cheers

---

### Post by diablo75 on 2010-05-01
Go here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Follow "Method 2".  It's easier than the steps you've been shown by previous posters so far.  It worked for me.

---

### Post by Sealbhach on 2010-05-02
> **hollowtd said:**
> Should I boot into the live CD then and then run the terminal commands?

Yes, that's how it's done.

> 
What If I've got reFit on my computer? What usually happens is I turn on the computer and then it goes to reFit and I can choose mac os or linux. Will this still happen once I restart?  

I don't know anything about reFit so I can't say.... maybe ask on the Mac forums, there's also an Apple users forum on the ubuntuforums which is here:  [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

.

---

### Post by hollowtd on 2010-05-02
Hiya Thanks for your help. That worked perfectly! It works now. I do have one more question: When I log in to ubuntu, it's like I have to reset all my settings. Like Compiz and the like doesn't stay "saved" when I log out. Any ideas why?

---

### Post by hollowtd on 2010-05-02
I just save the session for now but think it might be a bug, as I found a link that others were having similar problems.

---

### Post by Sealbhach on 2010-05-02
> **hollowtd said:**
> Hiya Thanks for your help. That worked perfectly! It works now. I do have one more question: When I log in to ubuntu, it's like I have to reset all my settings. Like Compiz and the like doesn't stay "saved" when I log out. Any ideas why?

I have the same problem, I think it's a bug. Glad you got the grub bit sorted out, congrats.

.

---

### Post by james.whanger on 2010-05-02
I upgraded from ubuntu 9.10 to 10.04 and bcmwl driver is not working.  Solutions to this problem that worked for 9.10 are not working for 10.04.  I believe I could resolve it by setting a ubuntu CD as a repository, but I installed using a Live USB.  My question is: Is it possible to set the Live USB as the CD repository in synaptics package manager?

---

### Post by hollowtd on 2010-05-02
Yes, thanks for your help SealbHach. I don't think I could have done it without you. I still am not sure how to mark this as solved. Thanks

---

