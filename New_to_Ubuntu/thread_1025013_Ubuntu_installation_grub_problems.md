---
title: "Ubuntu installation: grub problems"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by hillslaura on 2008-12-29
I hope someone can help. I know there has been a lot of threads on this forum to resolve grub-related issues but none that i have tried so far has helped. 

I got an old computer with Win98 installed on it and I tried to install Ubuntu with an original Ubuntu install CD version 5.0.4. At some point in the installation after I had chosen that the entire partition be used for linux hoping to wipe off the Windows OS. At some point during the installation, I got the message that the CD was corrupted and this was confirmed when I checked the integrity of the CD. In trying to stop the installation, I got a warning message that stopping the process might make the computer unusable. As I had no choice, I stopped the install and burnt an install CD to use to reinstall. The second process went to completion but during rebooting, I have been getting grub loading error. The computer just hangs there with the message "grub loading" Stage1_5 or something like that. I am still able to use the live CD to bring up Ubuntu and would appreciate a solution that involves the command line in the terminal brought up via live CD.

For the command
fdisk -l /dev/hda

the output was

Device    boot Start   End   Blocks    Id   System
/dev/hda1  *   1      1005   807263    83   Linux
/dev/hda2      1006   1007   176715     5   Extended
/dev/hda3      1006   1007   176683+   82   Linux swamp / solaris

I have tried different things including

(1) the whole sequence 

# Boot the Ubuntu Live CD.

#Press Ctrl-Alt-F1

# Find the partition where your /boot directory is (normally the root partition) check the previous tip for that.

# sudo mount /dev/hda1 /mnt

# sudo chroot /mnt

# grub

# find /boot/grub/stage1 (will output a partition name like (hd0,3) )

# root (hd0,3)

# setup (hd0)

# quit

# Now restart the system and remove the Live CD 

(2)burning supergrub on a CD to reboot but the computer wouldn't even recognize supergrub. 

I am almost at the point of trying either of the two ideas below. Please help me tell which would help me get a clean reinstall or if you have a better idea.

(1)
sudo fdisk -l
sudo shred -n 1 -v -z /dev/hdXY
mkfs to reformat.


(2)
dd if=/dev/zero of=/dev/hda bs=512 count=1


==========

Please help me. Thanks so much

---

### Post by ByteJuggler on 2008-12-29
It sounds like you have half a (broken) install, so reinstallation is probably recommended.  

From the LiveCD, open a terminal, then enter:

```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```

Then start the installer.  The above command wipes clean the partition table, effectively making it look like the hard disk is blank.

---

### Post by hillslaura on 2008-12-29
> **ByteJuggler said:**
> It sounds like you have half a (broken) install, so reinstallation is probably recommended.  

From the LiveCD, open a terminal, then enter:

```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```

Then start the installer.  The above command wipes clean the partition table, effectively making it look like the hard disk is blank.

Thank you so much. I'll try that right away.

---

### Post by hillslaura on 2008-12-29
Well, this is frustrating !

After I tried the dd command above, the output was 

1+0 records in
1+0 records out
512 bytes transferred in 0.011619 seconds (44066 bytes/sec)

So i started the reinstall process in the course of which I chose to erase the entire disk which formerly ran Windows 98. when it was time to partition, I chose 
Erase entire disk.

Then i got the following messages(written here in italics) :
[I]
IDE1  master (hda)    8.5GB WDC AC28400R
#1 primary 8.3GB   ext3  /
#5 logical 180.9MB swap  swap[/I]


[I]The partition tables of the following devices are changed:
IDE1 master (hda)
[/I]

[I]The following partitions are going to be formatted:
partition #1 of IDE1 master (hda) as ext3
partition #5 of IDE1 master as swap[/I]

*Write changes to disks ? <Yes>*

After all of these and more (excluded here) I was super-convinced the installation had proceeded well. Except when it was time to reboot, computer tried to boot from the hard drive except that I got the same message as in the start of this problem:[I]

Grub loading Stage 1.5

Grub loading, please wait ...[/I]

which was exactly my problem in the first place. Is this installation doable at all ? Someone please help me. Thanks a lot.

---

### Post by caljohnsmith on 2008-12-29
In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by ByteJuggler on 2008-12-29
> **hillslaura said:**
> 
Grub loading, please wait ...[/I]

which was exactly my problem in the first place. Is this installation doable at all ? Someone please help me. Thanks a lot.

OK, Just to confirm, what version of Ubuntu are you installing, exactly?  Secondly, this is starting to sound suspiciously like some bootup GRUB problems I've not seen for a while.  On older PC's/versions of Ubuntu, the bootloader's view of reality would be different during boot compared to while running from the OS.  As a result, the bootloader would be installed with incorrect information during installation, causing bootup problems.  The real problem was/has to do with the BIOS and when it's view of reality changes/differs during boot from the rest of the system's view.  What drives, exactly do you have installed?  

There's several people with lots of Grub experience on the forums.  We can probably help you sort this out, if you're patient.  Sorry to see  you've run into trouble at the first hurdle. :(

---

### Post by hillslaura on 2008-12-30
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

Thanks CalJohnSmith. The trouble is I don't know  where to type in your suggested command. If it's at the dot prompt, then I can't get there. If it's on the terminal after having booted with the live CD, then that won't work either since my computer isn't connected to the internet. It's a pretty old computer and I just thought it was a good way to try my hands at installing linux for the first time. Thanks anyway. I appreciate your help.

---

### Post by Malalo on 2008-12-30
This awfully sounds like an error I was getting with my old system. I had to manually create the partitions during the install, and create the /boot partition in the first 128 Mb of the drive (I personally chose 128 because the number has personal significance to me, however I think you only need 16 Mb or even less ? not sure here...) 
Try it out !

---

### Post by hillslaura on 2008-12-30
> **ByteJuggler said:**
> OK, Just to confirm, what version of Ubuntu are you installing, exactly?  Secondly, this is starting to sound suspiciously like some bootup GRUB problems I've not seen for a while.  On older PC's/versions of Ubuntu, the bootloader's view of reality would be different during boot compared to while running from the OS.  As a result, the bootloader would be installed with incorrect information during installation, causing bootup problems.  The real problem was/has to do with the BIOS and when it's view of reality changes/differs during boot from the rest of the system's view.  What drives, exactly do you have installed?  

There's several people with lots of Grub experience on the forums.  We can probably help you sort this out, if you're patient.  Sorry to see  you've run into trouble at the first hurdle. :(

Thanks as always ByteJuggler. I am installing 5.04. It was the original ubuntu CD I found in my research group. Just to add more info. which might be necessary, when the first CD failed (see my first post), my first reinstallation was to try with 8.11 (or whichever is the latest one) but i think it was too new for computer and had some apci problem (IIRC) so I went back to burning a new CD with 5.04 which is the same version as my live CD.

I have C: drive, CD-ROM drive and also a floppy drive.

I am not sure if I didn't mess up the BIOS at some point. 

In any case during boot-up I saw the following

IDE Pri. Master   CHS, UDMA 2, 8455 MB
IDE Pri. Slave    None
IDE Sec. Master   CDROM, Mode 4
IDE Sec. Slave    ZIP-100, Mode 0

==========

In fact the live CD is my only savior at this point because it's always come through whenever I have needed to correct something. I even tried OpenSUSE 11 thinking that it might be an Ubuntu problem but after the installation, I couldn't log on and I am using live CD to wipe everything clean and start over. I hope this episode will end sometime. It's daunting. But thanks to selfless people like you, I hope to pull this off even it takes me till next year ! :)

---

### Post by caljohnsmith on 2008-12-30
> **hillslaura said:**
> Thanks CalJohnSmith. The trouble is I don't know  where to type in your suggested command. If it's at the dot prompt, then I can't get there. If it's on the terminal after having booted with the live CD, then that won't work either since my computer isn't connected to the internet. It's a pretty old computer and I just thought it was a good way to try my hands at installing linux for the first time. Thanks anyway. I appreciate your help.
Sorry I wasn't clear about where to run the script, but yes, you should run it in a terminal. Since you don't have access to the Internet when using the Live CD, how about right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "save target as...", save the script, then transfer it to your other computer with maybe a floppy or USB stick; would that work for your setup? Bottom line, if you can transfer the script to your Ubuntu Live CD desktop, you can run it with:
sudo bash ~/Desktop/boot*.txt
In the terminal. Let me know if you still run into problems though.

---

### Post by hillslaura on 2008-12-30
> **Malalo said:**
> This awfully sounds like an error I was getting with my old system. I had to manually create the partitions during the install, and create the /boot partition in the first 128 Mb of the drive (I personally chose 128 because the number has personal significance to me, however I think you only need 16 Mb or even less ? not sure here...) 
Try it out !

Thanks Malalo. But how do I do that ? I am new to all of this. I have always been a UNIX user but this is the first time I am trying to peek behind the curtains. As it is now, I don't know how my computer is partitioned since I have used the dd command a couple of times. And I also don't know how to partition as you suggested. I would appreciate any sequence of commands you can suggest for me to use. Thanks a great deal.

---

### Post by Malalo on 2008-12-30
> **hillslaura said:**
> I am new to all of this. 

I'm not much of a guru myself... I can't say what command it was, since I used the gParted section of the installation from the CD (not through LiveCD). There's a section for partitioning, and I chose "manual", then setup the partitions as I stated earlier... Maybe someone could give you the commands for doing so ?

---

### Post by ByteJuggler on 2008-12-30
> **hillslaura said:**
> ... my first reinstallation was to try with 8.11 (or whichever is the latest one) but i think it was too new for computer and had some apci problem (IIRC) 
Hmmm.  OK, so your problem sounds a lot like an old problem we had with an older version of Ubuntu... and you're using an older version of Ubuntu.  1 and 1 seems to be making 2 here. :)  I really think we should use a newer version of Ubuntu, as 5.04 is not supported anymore and I've not got a reference platform for 5.04 anymore either.  I would therefore actually suggest you try 8.04, which is a LTS (Long Term Support) release.  8.10 is latest cutting edge but only supported for 18 months as it gets replaced again in 6 months time.

You can download 8.04 here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors)

If you're having acpi problems, then we'll explain how you can turn that off on boot.  (Have you posted about that before?)  You really should be able to get going with 8.04...  If you run into graphics driver problems then you also may want to get the alternate install CD instead of the graphical one. (The graphical installer requires a minimum of 384MB of RAM, ideally 512MB, as it boots the entire OS into RAM from CD.  The alternative installer has far less requirements.  See [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").  Note if your machine is low RAM/low power, XUbuntu is a better choice as Ubuntu expects a relatively modern machine and will likely be a bit sluggish on old machines.)

---

