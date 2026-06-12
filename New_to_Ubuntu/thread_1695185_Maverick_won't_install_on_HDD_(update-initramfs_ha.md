---
title: "Maverick won't install on HDD (update-initramfs hangs)"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Screenshot on 2011-02-25
I successfully installed Ubuntu 10.10 (64bit CD-image) on an SD-Card, but I can't manage installing it on my PC's built-in HDD.

The installation hangs at "Configuring hardware", especially at "[FONT=Courier New]update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic[/FONT]".
I once let my PC run throughout the night but no progress was made. (The attached log file is a different one!)
I tried skipping the image-creation by editing [FONT=Courier New]/target/etc/initramfs-tools/update-initramfs.conf[/FONT] from "update-initramfs=yes" to "[FONT=Courier New]update-initramfs=no[/FONT]" as soon the mentioned file was created by ubiquity (This happens long before initramfs-tools are executed). But it didn't change anything.

Is there something I can do about it? Is it a problem with my HDD?


System Specs:
Acer Aspire M5201
HDD: 750GB (Western Digital 7500AAKS-22RBA0)
CPU: AMD Phenom X4 9750, 4x 2.40GHz
Memory: 8GB DDR2
graphics card: ATI Radeon HD 4870  512MB

I attached user.log of my latest attempt and 2 screenshots (from GParted and Disk Utility).

---

### Post by Ben Page on 2011-02-25
I'm not sure about this, but I think it's because you are installing it into an extended/logical partition, try installing it to primary partition and use mounting point: just the "/"

---

### Post by nm_geo on 2011-02-25
I would use file type EXT4 instead of EXT3.

---

### Post by Hedgehog1 on 2011-02-25
The error about installing on the hard drive is because you have used up your primary partitions. You are allowed 4 base (primary) ones. A primary can be turned into and extended partition, and this extended partition can be filled with many more partitions.
 
The Picure of the Disk Utility tells the story nicely (thanks for that - it really helps).
 
/dev/sda1 is PQSERVICE (Primary - boot))
/dev/sda2 is ACER (NTFS - Windows)
/dev/sda3 (or 4) is the extended partition - but it only has one partition in it - sda5.
/dev/sda4 (or 3) is data partition.
 
To install ubuntu, you need to:
 
1) shink the partition before the /dev/sda3 (or 4) extended partition (by 30 gigs?)
2) Move-expand the /dev/sda3 (or 4) extended partition to fill that (30 gigs?) space
3) Move the /dev/sda5 partition to the left side of the extended partition
4) Add a 25 gig partition in EXT4 for your /home (/dev/sda6)
5) use the rest of the extended partition for unix swap (/dev/sda7)
 
You want the extended partition to look like this in the Disk Utility:
 
|--------------------- Extended -------------------------|
|----sda5---|-------------sda6---------------------|sda7|
 
|--------------------- Extended -------------------------|
|----ext4---|-------------ext4---------------------|swap|
 
Then reinstall ubuntu with the manual mode, selecting:
 
/dev/sda5 as both Boot and '/'
/dev/sda6 as '/home'
/dev/sda7 as 'swap'
 
:KS

---

### Post by Hedgehog1 on 2011-02-25
> **nm_geo said:**
> I would use file type EXT4 instead of EXT3.
 
I agree -
 
Unless you have an overwhelming reason not to, formatting /dev/sda5 as ext4 is best.

---

### Post by nm_geo on 2011-02-25
> **Hedgehog1 said:**
> I agree -
 
Unless you have an overwhelming reason not to, formatting /dev/sda5 as ext4 is best.
 
+1 on all that Hedgehog1 put down good eyes there hedge.  What is up with [COLOR=red]/target?[/COLOR]
[COLOR=black][/COLOR]

---

### Post by Hedgehog1 on 2011-02-25
> **nm_geo said:**
> +1 on all that Hedgehog1 put down good eyes there hedge. What is up with [COLOR=red]/target?[/COLOR]

 
When you are built close to the ground.....:P
 
really, I just built a Ubuntu USB stick - so it was on my mind.
 
*Not following the '/target?' question - sorry.*

---

### Post by nm_geo on 2011-02-26
> **Hedgehog1 said:**
> When you are built close to the ground.....:P
 
really, I just built a Ubuntu USB stick - so it was on my mind.
 
*_Not following the '/target?' question - sorry_.*

Unless the OP annotated both screenshots the mount points are designated  [COLOR=Red]/target.  [COLOR=Black]Instead of just / .  I have never seen that before.

Yeah the log shows this.

Feb 25 16:51:52 ubuntu ubiquity: /usr/lib/ubiquity/apt-setup/generators/01setup: 7: cannot open /target/etc/apt/sources.list: No such file
Feb 25 16:51:52 ubuntu in-target: locale: Cannot set LC_CTYPE to default locale: No such file or directory
[/COLOR] [/COLOR]

---

### Post by Dutch70 on 2011-02-26
> **Ben Page said:**
> I'm not sure about this, but I think it's because you are installing it into an extended/logical partition, try installing it to primary partition and use mounting point: just the "/"

 You **can** install Ubuntu into a logical partition. as long as your bootloader is in a primary partition. So, if you only have Ubuntu, it would have to be in a primary partition.

You can have 4 primary partitions...
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

And only 1 extended partition, which counts as one of the 4 primary partitions.(hence the sda3)

The number of logical partitions you can have inside of an extended partition is only limited by the size of your hdd, and they will always start with /dev/sda5, even if you only have 1 primary.

As you can see in my pic. Ubuntu is installed in a logical partition, As is "swap" otherwise, it would count as a primary. Also, I don't have a /dev/sda4. That's because I only have 3 primary partitions & one of them is an extended partition.

---

### Post by Dutch70 on 2011-02-26
> **Screenshot said:**
> I successfully installed Ubuntu 10.10 (64bit CD-image) on an SD-Card, but I can't manage installing it on my PC's built-in HDD.

The installation hangs at "Configuring hardware", especially at "[FONT=Courier New]update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic[/FONT]".
I once let my PC run throughout the night but no progress was made. (The attached log file is a different one!)
I tried skipping the image-creation by editing [FONT=Courier New]/target/etc/initramfs-tools/update-initramfs.conf[/FONT] from "update-initramfs=yes" to "[FONT=Courier New]update-initramfs=no[/FONT]" as soon the mentioned file was created by ubiquity (This happens long before initramfs-tools are executed). But it didn't change anything.

Is there something I can do about it? Is it a problem with my HDD?

Did you check the sd card?
I would try to re-create the sd card, or use a usb stick, or cd/dvd.

I think it's a bug, what is up with the /target?

---

### Post by Hedgehog1 on 2011-02-26
> **nm_geo said:**
> Unless the OP annotated both screenshots the mount points are designated  [COLOR=Red]/target.  [COLOR=Black]Instead of just / .  I have never seen that before.
[/COLOR] [/COLOR]

See - I caught the 'base' partitions were used up - but completely missed '/target' on the screen shots.  *It takes a village* (I applied for village idiot, but the position was filled).

That really should be '/'. No wonder the question didn't click with me.

Hopefully the OP will makes sense of all this and get Ubuntu installed on the HDD.

---

### Post by nm_geo on 2011-02-26
Are we missing the /target here ...

Wonder if in a re-install, if the OP put / in for the mount point what would happen?  Do you think the OP would have a working 10 megabyte Maverick in the third partition?

---

### Post by Dutch70 on 2011-02-26
> **nm_geo said:**
> Are we missing the /target here ...

Wonder if in a re-install, if the OP put / in for the mount point what would happen?  Do you think the OP would have a working 10 megabyte Maverick in the third partition?

I have no idea what /target is, but he took that pic from the live cd or whatever, it wouldn't show up as / "root" until he was installing it, or had it installed, right?

---

### Post by nm_geo on 2011-02-26
> **Hedgehog1 said:**
> See - I caught the 'base' partitions were used up - but completely missed '/target' on the screen shots.  *It takes a village* (I applied for village idiot, but the position was filled).

That really should be '/'. No wonder the question didn't click with me.

Hopefully the OP will makes sense of all this and get Ubuntu installed on the HDD.

Yeah if the OP reads it and does the /  only it should go well.

---

### Post by nm_geo on 2011-02-26
It appears the OP typed /target in the mount point.
instead of just the /

---

### Post by Screenshot on 2011-02-26
Thank you for all the input. I am really impressed of the amount of replies.

About /target: I used the "Try out" option on the CD and then opened the "Install Ubuntu 10.10" programme. If I'm right, it's called "ubiquity". This ubiquity does automatically mount the for the installation selected partition to /target and installs Ubuntu to /target. I was still running ubiquity at the point I made those screenshots.
And why I selected Ext3: I did some googling about whether to use Ext3 or Ext4 and some people said Ext4 was still bugged. Is this information outdated?


My installation settings were: "/" to "dev/sda5".
I didn't set anything for swap as it doesn't really matter for me if I can hibernate Ubuntu atm. This is the first time I use Ubuntu and I mainly want to see what it can do and if I like it. As mentioned above I have 8GB of RAM. Is a swap still neccessary? (I'm not going to run many programmes at the same time.)
I didn't set "/home" either. I thought if I want to save some personal files I can save it on my NTFS-Data partition which I can also access using Windows.
I didn't select a specific partition for GRUB so it would show up when BIOS boots on HDD and offer me all available OSs.

Now about the partitions:
I created the partition with Windows 7. I already had 3 primary partitions and selected "create new partition." I wanted to create a 10GB primary partition (reasons stated above) but Windows thinking it's so clever didn't ask me what I wanted to have, it just created a new 10GB-big extended partition containing a <10GB logical partition.
As Ubuntu can boot on logical partitions aswell I didn't delete it and create a new primary one using GParted from the Ubuntu-CD before installing Ubuntu.




> **Hedgehog1 said:**
> The error about installing on the hard drive  is because you have used up your primary partitions. You are allowed 4  base (primary) ones. A primary can be turned into and extended  partition, and this extended partition can be filled with many more  partitions.
....
To install ubuntu, you need to:
 
1) shink the partition before the /dev/sda3 (or 4) extended partition (by 30 gigs?)
2) Move-expand the /dev/sda3 (or 4) extended partition to fill that (30 gigs?) space
3) Move the /dev/sda5 partition to the left side of the extended partition
4) Add a 25 gig partition in EXT4 for your /home (/dev/sda6)
5) use the rest of the extended partition for unix swap (/dev/sda7)
....You couldn't know my installation settings, sorry.
With my installation settings, do I still have to repart my other partitions?



> **Dutch70 said:**
> Did you check the sd card?
I would try to re-create the sd card, or use a usb stick, or cd/dvd.The SD-card boots up fine. (but slow -.-)



> **nm_geo said:**
> Are we missing the /target here ...

Wonder if in a re-install, if the OP put / in for the mount point what  would happen?  Do you think the OP would have a working 10 megabyte  Maverick in the third partition?That's what I did. I'm really sorry for that confusing /target which ubiquity mounts to install Ubuntu.

---

### Post by Dutch70 on 2011-02-26
> With my installation settings, do I still have to repart my other partitions?

Windows did the right thing by making your 4th partition an extended partition since you didn't have one. Remember extended is also primary, but you can slice it into logical. The fact that yours is only 10GiB is the only downfall. Also, you won't be able to create another partition unless either you delete the extended partition, or create a logical partition inside the 10GiB extended partition. 

 If you just want to use the 10-GiB prt. to try Ubuntu for a little while, that should be fine. 

If you don't want to hibernate, you don't need "swap". I have 4 GiB of RAM & it's never used. Even when I try to really bog my system down.

---

### Post by nm_geo on 2011-02-26
Screenshot

"I didn't select a specific partition for GRUB so it would show up when BIOS boots on HDD and offer me all available OSs."

Grub must be installed in sda to find all OS's after the BIOS runs.  I would do a fresh install to sda5 making sure the mount point is / and that file type is EXT4.  EXT4  is  recommended for Maverick and works well. Grub installed in sda. 

If you ever get tired of Ubuntu and the Grub2 you will need to repair the MBR but it is not too tough if you have a windoz recovery disk or you can get help here on other methods.

Who knows you might end up like me with multiple Ubuntu versions on your puter.  See screenshot

---

### Post by nm_geo on 2011-02-26
Screenshot 

TRY this too.

B00t-info-script

boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
    * Download the Boot Info Script    [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

### Post by Screenshot on 2011-02-27
I wrote the following post in a text editor before reading the 2 last replies, so I'm going to answer them first.
> **nm_geo said:**
> Screenshot
"I didn't select a specific partition for GRUB so it would show up when BIOS boots on HDD and offer me all available OSs."
Grub must be installed in sda to find all OS's after the BIOS runs.That's what I was trying to say. When Ubiquity asked to choose where to install the "bootloader" to I selected my HDD and not a specific partition of my HDD. But the installation progress didn't get that far.
I ran that bootinfo script from the Ubuntu on my SD-card and uploaded it as an attachment because the following post will get too long anyway.

Here's what I was going to say:
Is it possible to manually install Ubuntu on my HDD by copying the files from the successful installation on my SD-card?
Here's my attempt:

Booting Ubuntu on my SD-card
Creating an archive of all files on my SD like described in some "Backup your Ubuntu"-tutorial
Reformatting sda5 to ext4 using Disk Utility (GParted disappeared.... ???)
Extracting the archive on sda5
Installing grub on sda
Updating grub and copying the output to /media/5fbb2d6c-cda1-4896-84a2-ab3910b80d20/boot/grub/grub.cfg



When booting from my HDD, grub offers my all OSs.
Booting Ubuntu from the SD-card and Windows 7 from my HDD does work fine, but booting Ubuntu from my HDD doesn't work.
When attempting to boot it displays some debug lines very quickly and then does "nothing" for some seconds. Then it says:

```
ALERT!    /dev/sd05 does not exist.    Dropping to a shell!


BusyBox v.1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_
```Uhm well, when I press a key nothing happens, probably because I have a USB-keyboard.


So I held down the power-button for some seconds, started my PC again and booted Ubuntu from my SD-card.
Then I opened up /media/5fbb2d6c-cda1-4896-84a2-ab3910b80d20/boot/grub/grub.cfg and edited in the entry
```
menuentry "Ubuntu 10.10 (10.10) (on /dev/sde5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 5fbb2d6c-cda1-4896-84a2-ab3910b80d20
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sde5
    initrd /boot/initrd.img-2.6.35-22-generic
}
```[FONT=Courier New]linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sde5[/FONT]
to[FONT=Courier New]
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5fbb2d6c-cda1-4896-84a2-ab3910b80d20[/FONT]


The odd thing about those lines is that it says hd1(/sde) and not hd0(/sda) where I installed Grub on. When running Grub from my HDD it also says my HDD is hd0 and my SD-card is hd1. But even more odd is the fact that the Windows 7 entry now also contains hd1+sde and boots correctly. Did something go wrong or is that fine?
When having a look at the error message I posted above you can see "ALERT!    /dev/sd05 does not exist.    Dropping to a shell!"
I have no idea why it does use the "correct"(?) sd05 then.

Ehm, well after editing this line I rebooted and selected the entry "Ubuntu 10.10 (10.10) (on /dev/sde5)" again.
Then it said:
```
ALERT!    /dev/disk/by-uuid/5fbb2d6c-cda1-4896-84a2-ab3910b80d20 does not exist.    Dropping to a shell!


BusyBox v.1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_
```Again pressing letters on my keyboard did nothing.



What am I doing wrong?
Another detail: When booting Ubuntu from my SD-card it sometimes shows those lines:
"[FONT=Courier New]ata5: softreset failed (device not ready)
ata3: softreset failed (device not ready)[/FONT]"
I don't know what that does mean but I have a feeling it is related because my extened partition is "3" and the logical one inside is "5". (Where I want to install Ubuntu.)


Any kind of help is much appreciated
If you want more details don't hesitate to ask.




After reading the post something comes up in my mind: (I couldn't find a place in the post to add this)
Grub says I have [FONT=Courier New](hd0) (hd0,1) (hd0,5) (hd0,2) (hd0,3) (hd1) (hd1,1)[/FONT]
The menu entry for booting Ubuntu from my HDD says:
"[FONT=Courier New]set root='(hd1,msdos5)'[/FONT]"
But when booting this entry the error-message says:
"[FONT=Courier New]/dev/sd05 does not exist.[/FONT]"
Does grub detect it incorrectly?
On my SD-card I don't have partition "5", that could be the explanation of the error message.

The Windows 7 entry says "[FONT=Courier New]set root='(hd1,msdos2)[/FONT]'" and boots up fine as mentioned before...


Where is the setting of "root" used by the way?
P.S.: Sorry for the mess :P

---

