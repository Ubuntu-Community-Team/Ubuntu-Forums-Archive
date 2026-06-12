---
title: "grub error 15 for jaunty"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by dougleduck on 2009-04-23
My main install works fine, but after installing 9.04 onto seperate partition (sharing /home) and keeping the grub on my main 8.10 dist to boot with, get an error 15 when trying to boot 9.04.

included 9.04 with the correct uuid in the menu.lst.

One problem I see is there are two kernels listed in /boot but the new jaunty kernel isn't there.

---

### Post by unutbu on 2009-04-23
One problem is that your /boot/grub/menu.lst says
```

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		e7b80ee4-a0d7-43f2-a307-e79639472dc1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e7b80ee4-a0d7-43f2-a307-e79639472dc1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```

but /boot/vmlinuz-2.6.27-11-generic is the Intrepid kernel, not the Jaunty kernel.
I don't think this file even exists on your Jaunty partition, sda12.

To make sure we correct it properly, please post the output of 

```
sudo mount /dev/sda12 /mnt
ls -l /mnt/boot
ls -l /mnt/boot/grub
```

---

### Post by JohnFH on 2009-04-23
I don't know how you get into this state, but here's what I see from your results file (helpful output by the way - nice one).

The 9.04 entries in the menu.lst file are using the correct uuid as you say, but not the correct kernel.  For some reason the 9.04 entries are trying to load the 2.6.27-11-generic kernel and not the 2.6.28-11-generic kernel, so grub doesn't look setup correctly.  The 2.6.27-11-generic kernel is on a different partition, so grub can't find it and hence it reports error 15 (file not found).  

Changing the 9.04 entries in grub to use the correct kernel will help, but there's also no initrd setup for Jaunty.

Hope that helps in some way.

---

### Post by dougleduck on 2009-04-23
I had seen that the wrong kernel was being used, and unsurprisingly there wasn't the corresponding file in /boot.

So as you can see its in the mounted boot folder, and the grub folder doesn't exist.

What I did was an install onto a separate partition and didn't allow it to install grub as I didn't want to mess up my current install. Is there a way around this, or should I set up a separate /boot/grub partition?



```
ls -l /mnt/boot/
total 5612
-rw-r--r-- 1 root root  529118 2009-04-08 07:46 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   96795 2009-04-08 07:46 config-2.6.28-11-generic
-rw-r--r-- 1 root root  128796 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1456232 2009-04-08 07:46 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1074 2009-04-08 07:48 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3501744 2009-04-08 07:46 vmlinuz-2.6.28-11-generic
$ls -l /mnt/boot/grub
ls: cannot access /mnt/boot/grub: No such file or directory

```

---

### Post by unutbu on 2009-04-23
There are many ways to setup GRUB for a multi-boot system. (See [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)).

I think the best thing to do is install a /boot/grub directory in sda12 and install GRUB to the boot sector on sda12 (note this is different than the MBR on sda). This will not change your Intrepid installation on sda10 in any way.

Then, edit the menu.lst on sda10 (Intrepid), replacing all mention of Jaunty with 

```
title      	Jaunty
root       	(hd0,11)
chainloader +1
```

This redirects GRUB to boot from the sda12 partition. Control of the boot process is then handed off to the /boot/grub/menu.lst on sda12. 

The disadvantage of doing it this way, is you see two GRUB menus pop up on your screen, though there are ways to make this quick, or hide one completely.

The advantage of doing it this way is you don't have to mess with updating your menu.lst by hand when you update your linux kernels under Jaunty.

If you'd like to try this, boot Intrepid, open a terminal and run

```
sudo mount /dev/sda12  /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt       
apt-get install linux-image-2.6.28-11-generic       # See Note below
apt-get install grub

grub
root (hd0,11)
setup (hd0,11)
quit

update-grub
```

Note: There is one issue which the above may not solve -- you are missing initrd.img-2.6.28-11-generic. I think, but am not sure, that this file is created by an installation script in the linux-image-2.6.28-11-generic Jaunty package. If I'm right, you'll also have to reinstall this package to create /boot/initrd.img-2.6.28-11-generic

---

### Post by JohnFH on 2009-04-23
> **dougleduck said:**
> 
What I did was an install onto a separate partition and didn't allow it to install grub as I didn't want to mess up my current install. Is there a way around this, or should I set up a separate /boot/grub partition?


Are you comfortable with editing the menu.lst configuration file directly?  If so, in the 9.04 menu entries, change the kernel from 2.6.27... to 2.6.28... and you should be ok.

If you don't install grub though, then for any kernel updates you'll need to update grub yourself rather than it being done automatically for you.

EDIT:  Beaten to it as usual.  Useful info, unutbu, thanks!

---

### Post by dougleduck on 2009-04-24
I successfully managed to install 9.10 and 8.04! Somehow though I've managed so that when I restart it boots straight into 9.04 and when I press escape I go to the 9.04 menu. :S

Think this means I've changed where stage1.5 points to somehow. Can't work out how to check where this points to to change this.

---

### Post by unutbu on 2009-04-24
Congratulations! Run the boot_info_script again and look at RESULTS.txt. I think you have this under control, but if you'd like some help, post the RESULTS.txt again.

---

### Post by jmduwa on 2009-04-25
Hi,
 
I have a similar problem but cannot boot at all.  
 
Details:
 
Upgraded from 8.10 to 9.04
 
Came to reboot and attempted the default system and got the following error:
 
GRUB Error 15 File not found
 
Tried entering GRUB interactive mode using "c" and tried 
 
find /boot/grub/stage1
 
(found this in a previous post related to upgrading but not to jaunty)
 
The machine then hung (no disk activity no response to keyboard)
 
Any suggestions gratefully received.

---

### Post by unutbu on 2009-04-25
jmduwa, please follow these instructions to run boot_info_script:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3). Then attach the RESULTS.txt file here.

---

### Post by dougleduck on 2009-04-25
So I fixed everything, besides the crappy vista partition but think I need to find the install disk for that. Just posting here in case somone has a similar problem

Somehow had re-installed grub on the MBR to boot from the wrong partition.

To fix this I mounted the partition I wanted to be the first for grub to boot off (/dev/sda9)

```
mount /dev/sda9 /mnt
mount --bind /sys /mnt/sys
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc

```

(not sure what binding these does but was suggested elsewhere and worked for me, but I don't know enough to guarantee this isn't dangerous)

then 

```
chroot /mnt
grub
find /boot/stage1
root (hd0,8)
setup (hd0)
```

think this installs grub onto the MBR telling it to boot from sda9.

Then had to re-do grub on the other partitions, sda10 and sda11

same as above but then doing

```

root (hd0,9)
```

so grub on the MBR wasn't written over and setup chainloading for the other partitions.

---

### Post by jdash1 on 2009-04-25
I'm trying to dual boot here.

also had an error 15 when loading grub in 9.04

attached is the result.txt here


thanks

---

### Post by jdash1 on 2009-04-25
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 78906800 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''


how do i fix this ?

---

### Post by jdash1 on 2009-04-25
up again

---

### Post by meierfra. on 2009-04-25
jdash1:

> Boot sector type: Grub
Boot sector info: Grub is installed in the boot sector of sda1 and looks
at sector 78906800 of the same hard drive for the
stage2 file, but no stage2 files can be found at this
location.
Mounting failed:
mount: unknown filesystem type ''


This means that you installed grub to the boot sector your Windows partition.  It will prevent  you from booting Windows. But it can be  fixed fairly easily with testdisk:

Boot from the Ubuntu Live CD, download  the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"BackupBS"
Type "Y" to confirm
Press "q" a few times to quit  testdisk.


This should be enough to fix the boot sector of your NTFS partition.


But the corrupted boot sector is not the cause of your  Grub error. Actually according to RESULTS.txt, Grub seems to configured correctly.
Did you upgrade from an earlier version of Ubuntu?  Or is this a fresh install?

 Let's see what happens if you reinstall grub. Open a  terminal in the LiveCD:

```

sudo mount /dev/sda5 /mnt  
cd /mnt
sudo mount --bind {/,}proc
sudo mount  --bind {/,}sys
sudo mount  --bind {/,}dev
sudo chroot /mnt

```

and at the new prompt
```
grep -v rootfs /proc/mounts> /etc/mtab
grub-install  --recheck /dev/sda

```
Post the whole content of terminal. Then reboot.

If this does not work, report exactly what happens during boot up. Do you get to the Grub count down? If yes, press  "Esc"  during the count down. Does the  the grub menu appear?

---

### Post by jdash1 on 2009-04-25
^ its a fresh install.. trying to dual boot it in windows xp



great. 
ill try it now.. 

i really appreaciate the help.  

i stopped using ubuntu for almost 3yrs.
now i'm deciding to go back again.

---

### Post by jdash1 on 2009-04-25
**when i use sudo mount /dev/sda6 /mnt**

ubuntu@ubuntu:~/Desktop$ sudo mount /dev/sda6 /mnt
/dev/sda6 looks like swapspace - not mounted
mount: you must specify the filesystem type
ubuntu@ubuntu:~/Desktop$ 



[B]should i use sda5 ?
[/B]


sda5 = ext4 /
sda6 = swap
sda7 = ext4 /home


**if i use sda5 then its ok**

**but when i use the 2nd command**  --bind {/,}proc command 

ubuntu@ubuntu:~/Desktop$ sudo mount --bind {/,}proc
mount: mount point proc does not exist
ubuntu@ubuntu:~/Desktop$ sudo mount  --bind {/,}sys
mount: mount point sys does not exist
ubuntu@ubuntu:~/Desktop$ sudo mount  --bind {/,}dev
mount: mount point dev does not exist


**how should i proceed ?**

**thanks for replying**

---

### Post by meierfra. on 2009-04-25
Yes, it should be "/dev/sda5". Sorry about that.

---

### Post by meierfra. on 2009-04-25
Opps. There is another problem. I left out "cd /mnt". I corrected my original post.

---

### Post by jdash1 on 2009-04-25
working on it now..

ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}proc
ubuntu@ubuntu:/mnt$ sudo mount  --bind {/,}sys
ubuntu@ubuntu:/mnt$ 
ubuntu@ubuntu:/mnt$ sudo mount  --bind {/,}dev
ubuntu@ubuntu:/mnt$ 
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/# grep -v rootfs /proc/mounts> /etc/mtab
root@ubuntu:/# grub-install  --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub


im restarting it now..


ill post again the results.

---

### Post by jdash1 on 2009-04-25
**afterrebooting...**

it booted my windows normally without grub menu option?


*currently online in windows xp

---

### Post by meierfra. on 2009-04-25
```
It booted my windows normally without grub menu option?
```

????? Did your run "fixmbr" or something like that after  you posted "RESULTS.txt"? 
At  least  your Windows  boot sector seems to be  fixed.

Could you run the boot_info_script and post the RESULTS.txt again?

---

### Post by jdash1 on 2009-04-25
> **meierfra. said:**
> ```
It booted my windows normally without grub menu option?
```

????? Did your run "fixmbr" or something like that after  you posted "RESULTS.txt"? 
At  least  your Windows  boot sector seems to be  fixed.

Could you run the boot_info_script and post the RESULTS.txt again?


yes i did, i didn't execute any fixmbr command but i tried to use my windows installer coz at that time i losing hope that i have to reinstall my xp again.

until i saw your post.

does it run the "fixmbr" automatically when i insert the windows installer?



**i think that installer fixed it.**

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.CO

[B]
so.. how do i install grub now ? i hope i'm close now

[COLOR="Red"]here's the file again[/COLOR].[/B]


**thanks for the response**

---

### Post by meierfra. on 2009-04-25
> i think that installer fixed it.
Did you run "testdisk"? 

> does it run the "fixmbr" automatically when i insert the windows installer?

It depends on the CD you are using. Your CD did run "fixmbr".


But the "grub-install" should have  reinstalled grub to the  mbr.
What LiveCD are you using? Is it  Ubuntu 9.04?

Try this:

```
sudo grub
```
and at the grub prompt:

```

root (hd0,4)
setup (hd0)
quit
```

Before typing "quit" post the whole content of the terminal. 
Then reboot.

---

### Post by jdash1 on 2009-04-25
> **meierfra. said:**
> Did you run "testdisk"? 


none at all

> 
It depends on the CD you are using. Your CD did run "fixmbr".

i think so

> 
But the "grub-install" should have  reinstalled grub to the  mbr.
What LiveCD are you using? Is it  Ubuntu 9.04?

live CD of ubuntu 9.04

> 
Try this:

```
sudo grub
```
and at the grub prompt:

```

root (hd0,4)
setup (hd0)
quit
```

Before typing "quit" post the whole content of the terminal. 
Then reboot.

Doing it now...

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


**rebooting..**

---

### Post by jdash1 on 2009-04-25
yeah i've noticed that there was a count down after rebooting it.

i pressed "ESC" and went straight to ubuntu  9.04


**problem is i didn't see any grub menu ?**



thanks

---

### Post by meierfra. on 2009-04-25
> i pressed "ESC" and went straight to ubuntu 9.04

You probably pressed it to late. 
Let's edit menu.lst so that you won't have to press "esc":

In a terminal in Ubuntu

```
gksudo gedit /boot/grub/menu.lst
```

This opens the file "menu.lst"
Change

timeout 3

to

timeout 10

Change

hiddenmenu

to

#hiddenmenu


Add this to the very end of the file:

title Window XP
rootnoverify (hd0,0)
chainloader +1

Save the file and reboot. You should now automatically get the Grub menu.

---

### Post by jdash1 on 2009-04-25
> **meierfra. said:**
> You probably pressed it to late. 
Let's edit menu.lst so that you won't have to press "esc":

In a terminal in Ubuntu

```
gksudo gedit /boot/grub/menu.lst
```

This opens the file "menu.lst"
Change

timeout 3

to

timeout 10

Change

hiddenmenu

to

#hiddenmenu


Add this to the very end of the file:

title Window XP
rootnoverify (hd0,1)
chainloader +1

Save the file and reboot. You should now automatically get the Grub menu.



done with the steps!
i will reboot it after the update manager is done with its updates (11mins more)


i really appreciate the help :P

but one last question  about the (hd0,1),(hd0,4) you gave as a sample i don't understand this yet. 

thanks

---

### Post by meierfra. on 2009-04-25
Sorry, typo again.



title Window XP
rootnoverify (hd0,0)
chainloader +1

---

### Post by meierfra. on 2009-04-25
Grubs start counting at zero. So (hd0,0) means the first partition on the first hard drive. (hd0,4) means fifth partition on the first hard drive.

---

### Post by jdash1 on 2009-04-25
great.

MY case is solved.

thanks a lot for proactively responding

---

### Post by meierfra. on 2009-04-25
> MY case is solved.
Good.  Has been a strange case: I don't know what caused the Grub error 15 and  I'm not even sure what fixed it.
Sorry for the typos, has been a busy day.
Have fun with XP and Ubuntu.

---

