---
title: "Laptop not booting anymore"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by jeannot_unbu on 2011-05-11
My laptop was working ok until this morning. Last night I did not shutdown normally, just closed the laptop and this morning when I tried to reboot i am directed to a screen where I have different option to choose from (i.e. ubuntu, with Linux 2.6.35-28-generic or  ubuntu, with Linux 2.6.35-28-generic (recovery mode) - this down to version 22). I have tried all of them and all i get is some text (quite a bit to type, I could type it all if really needed) but one of the line that jump out is:
Kernel panic - not syncing: Attempted to kill init!

After the last line of text, I get an - (hyphen) and the PC is not doing anything else. I hope I made myself clear.

Any suggestion on what I can do to fix that, thanks.
JC

---

### Post by jeannot_unbu on 2011-05-11
Also on the recovery mode, some scripting appears and the last line is: (initramfs). And then nothing else happens.
One of the line reads:
mount: mounting /sys on/root/sys failed: no such file or directory
mount: mounting /proc on/root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg

JC

---

### Post by Rubi1200 on 2011-05-11
Hi,
please do the following so we can get a better overview of the current state of the system.

Download and run the boot info script. There is a link at the bottom of my post with instructions.

Post the results back here in a new post and please wrap the text with code tags (highlight all text and click on the # symbol on the toolbar).

Thanks.

---

### Post by jeannot_unbu on 2011-05-11
> **Rubi1200 said:**
> Hi,
please do the following so we can get a better overview of the current state of the system.

Download and run the boot info script. There is a link at the bottom of my post with instructions.

Post the results back here in a new post and please wrap the text with code tags (highlight all text and click on the # symbol on the toolbar).

Thanks.
Rubi1200, sorry for not replying to your post earlier. A couple of question for running the script, obviously I can't login onto the computer, so I have downloaded the script on a different machine. Now shall I copy file onto a CD or an USB key and run it on the faulty laptop. If yes how do I do that, sorry about the question but I am not that technical, thanks.
JC

---

### Post by Rubi1200 on 2011-05-11
No, I need to apologize. I was in a hurry when I posted and didn't make things clear enough.

Here are more precise instructions:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jeannot_unbu on 2011-05-11
Still trying to launch the CD, I have clicked on Try Ubuntu, little wheel spinning but nothing else happening (for over 1hr now). I may need to download a new ISO of ubuntu just in case this one is not working. But is won't the same version now, is this going to be ok?
JC

---

### Post by jeannot_unbu on 2011-05-11
Getting an error message now trying to lauch Try Ubuntu:

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 139)
:(

---

### Post by xdragonforce on 2011-05-11
Friend, i hate to say it, but you may have a faulty cd drive.

It sounds like that the offline internal configuration center, has not been read properly.I would suggest booting from a LiveUSB

---

### Post by jeannot_unbu on 2011-05-11
> **xdragonforce said:**
> Friend, i hate to say it, but you may have a faulty cd drive.

It sounds like that the offline internal configuration center, has not been read properly.I would suggest booting from a LiveUSB

Downloading the ISO as we speak. Will try from an USB (never tried before). 
JC

---

### Post by jeannot_unbu on 2011-05-11
OK I have got the script running, finally!! It says Searching sdal for information....  This has been going on for a while now. How should it take to return something? THanks

JC

---

### Post by Rubi1200 on 2011-05-12
The script should only take a few seconds to run and create a RESULTS.txt

Okay, the next thing to try is download and burn to CD a live distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Then try booting the laptop again and following the instructions I posted previously. The only difference is that in the terminal on Slax you do not need to preface the command with sudo (Slax comes with a root terminal by default).

Good luck!

---

### Post by jeannot_unbu on 2011-05-12
Finally!!! Managed to get the script using Slax.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009ede

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,332,799   112,330,752  83 Linux
/dev/sda2         112,334,846   117,209,087     4,874,242   5 Extended
/dev/sda5         112,334,848   117,209,087     4,874,240  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda                                                iso9660    SLAX                          
/dev/sda1        170c1f77-d0c1-4bec-a9bb-25ef958654f4   ext4                                     
/dev/sda5        dc63bc8a-6eef-4aee-a0b1-ca7628f6e07d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=2f049554,xino=/mnt/live/memory/.aufs.xino,nowarn_perm)
/dev/hda         /mnt/hda                 iso9660    (ro,noatime)


==================== hda: Location of files loaded by Grub: ====================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file

```

---

### Post by Rubi1200 on 2011-05-12
It looks as if there might be some damage to the file-system on sda1.

Do you have backups of important data?

We can try and fix this from the Slax CD with this command:

```
e2fsck -f -y -v /dev/sda1
```Let it run until complete and then, assuming there are no more errors reported, you can reboot taking out the CD and hopefully be back in Ubuntu.

Let me know what happens please.

---

### Post by jeannot_unbu on 2011-05-12
> **Rubi1200 said:**
> It looks as if there might be some damage to the file-system on sda1.

Do you have backups of important data?

We can try and fix this from the Slax CD with this command:

```
e2fsck -f -y -v /dev/sda1
```Let it run until complete and then, assuming there are no more errors reported, you can reboot taking out the CD and hopefully be back in Ubuntu.

Let me know what happens please.

Thanks Rubi for your help. No I don't too much important data. I just use this laptop to surf the net and do a bit of self learning Python. I let you know what happens, thanks again.

JC

---

### Post by jeannot_unbu on 2011-05-12
Hooray and triple hooray. It is working again. Rubi you are the MAN!! do you know what caused the problem. I did nothing on the laptop as far as I can remember.

Again many thanks
JC

---

### Post by Rubi1200 on 2011-05-12
> **jeannot_unbu said:**
> Hooray and triple hooray. It is working again. Rubi you are the MAN!! do you know what caused the problem. I did nothing on the laptop as far as I can remember.

Again many thanks
JC
Excellent! I am really pleased you got things working again :D

Kernel panics can have a number of causes and without investigating the logs for errors I wouldn't like to speculate as to the exact source of this.

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy :-)

---

