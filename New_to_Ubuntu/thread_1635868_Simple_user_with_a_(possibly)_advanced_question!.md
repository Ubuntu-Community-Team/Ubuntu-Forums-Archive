---
title: "Simple user with a (possibly) advanced question!"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by bobman500 on 2010-12-02
I have been using Ubuntu for a couple of months now, but always had it as a dual-boot with Vista for gaming and Netflix. I recently recieved a desktop with XP that I am now using for those purposes, and so no longer need a Windows boot on this system. 

How do I totally remove Vista, all the programs, and all the documents, while keeping everything I have in Ubuntu safe?
Keep in mind that I have little to no experience in Terminal/programming/coding and the like.

Thanks!

---

### Post by bug67 on 2010-12-02
When you run the Ubuntu installer, it will ask you if you want to use the entire disk.  Click "yes" and Vista will be but a distant memory.:)

**_EDIT_**:

I just realized you said you wanted to keep your current Ubuntu. I read somewhere on here a long time ago a way to do it but, I can't remember where.  If it was me (and this is just me) I would drag and drop the entire /home folder onto an external hard drive. Then do a clean/fresh Ubuntu install in the manner described above. Afterwards, the /home folder you backed up the the external contains everything.

---

### Post by bobman500 on 2010-12-02
What installer? I already have Ubuntu, like I said, I have been using it for a couple of months, and have dozens of GBs of things I don't want to lose by reinstalling.

---

### Post by chamira on 2010-12-02
I would boot in to you Windows Vista & back-up all your data and note down all the licences for the paid software you have installed (so you can install them in your XP PC) - including your Vista license!

Then I would boot in to your Ubuntu and format your Vista partition/drive. If you format it ext3/ext4 you can use it extra storage for Ubuntu. You can do this from the Disk Utility, not need to go in to the command line.

Then you can rebuild you Grub menu, this will remove the dual boot option as it will not see another OS. This means when you boot your Ubuntu PC it will go straight to Ubuntu login from then on.

But forst of all....
What version of Ubuntu are you running?
Also, is you Windows Vista on a separate hard-drive or on a partition?

---

### Post by Elfy on 2010-12-02
Depends on whether this is a real install or a wubi one.

From inside ubuntu - open a terminal and run

```
sudo fdisk -l
```

paste the output here please

---

### Post by bobman500 on 2010-12-02
I am running 10.10, and have no idea what an ext3/ext4, or a grub menu is, let alone how you change any of them.

---

### Post by bobman500 on 2010-12-02
@ forestpiskie

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd1c734b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            9201       30402   170295297    5  Extended
/dev/sda5            9201       29536   163344384   83  Linux
/dev/sda6           29537       30402     6949888   82  Linux swap / Solaris

---

### Post by chamira on 2010-12-02
I think you should first of all do as **forestpiskie** asked above, then we can see how your hardware is setup.

Then I'm sure we can guide you step-by-step.

---

### Post by bobman500 on 2010-12-02
[B]UPDATE

[/B]I deleted the 75gig partition I had for Vista, so I THINK all of the actual information is gone, but it is still showing up in my boot menu.

---

### Post by ayashif on 2010-12-02
> **bobman500 said:**
> I have been using Ubuntu for a couple of months now, but always had it as a dual-boot with Vista for gaming and Netflix. I recently recieved a desktop with XP that I am now using for those purposes, and so no longer need a Windows boot on this system. 

How do I totally remove Vista, all the programs, and all the documents, while keeping everything I have in Ubuntu safe?
Keep in mind that I have little to no experience in Terminal/programming/coding and the like.

Thanks!
Logon to ubuntu.

Mount the drive where the WinOS is installed(Well, u can mount the drive using "mount" command in terminal or select the drive from places(C:\ drive, most probably...). You can recognize either by the size of the disk or its contents after it is mounted.

[Otherwise, just format the drive using "Gnome Partition Editor" (or other softs u prefer)
   install GPartEd using the command "sudo apt-get install gparted" without the quotes...]

Now just delete the entire Files and folders in that drive..

Now open up a terminal(Ctrl+Alt+T) and update grub as root.

You are done... :D

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> [B]UPDATE

[/B]I deleted the 75gig partition I had for Vista, so I THINK all of the actual information is gone, but it is still showing up in my boot menu.

```
sudo update-grub
```

As you say there's no ntfs partition so all you need to do now if you wish is create a partition you can use

---

### Post by bobman500 on 2010-12-02
> **ayashif said:**
> Logon to ubuntu.

Mount the drive where the WinOS is installed(Well, u can mount the drive using "mount" command in terminal or select the drive from places(C:\ drive, most probably...). You can recognize either by the size of the disk or its contents after it is mounted.

[Otherwise, just format the drive using "Gnome Partition Editor" (or other softs u prefer)
   install GPartEd using the command "sudo apt-get install gparted" without the quotes...]

Now just delete the entire Files and folders in that drive..

Now open up a terminal(Ctrl+Alt+T) and update grub as root.

You are done... :D


Literally no idea what any of that meant. To reiterate, ABSOLUTE beginner! My idea of technical prowess is knowing that control+C is copy, instead of having to right-click.

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> ```
sudo update-grub
```As you say there's no ntfs partition so all you need to do now if you wish is create a partition you can use

Again, I am sorry, but I really don't understand what that means.

I had 75gigs put aside in a partition that had Vista on it. I deleted that partition, so I am assuming that 75gigs has now joined the rest in Ubuntu. When I reboot my system, Vista is still there to select.

Can somebody please tell me how the hell to get Vista off my machine, preferably using real words. :p

---

### Post by ayashif on 2010-12-02
> **bobman500 said:**
> [B]UPDATE

[/B]I deleted the 75gig partition I had for Vista, so I THINK all of the actual information is gone, but it is still showing up in my boot menu.
Just update GRUB using the command "sudo update-grub".
This will certainly help.

Regards,
Yash!

---

### Post by bobman500 on 2010-12-02
I have done 'sudo update-grub', but Vista is still selectable, which surely means there is still Windows crap on the machine somewhere, and would like to me clear of it more than a married man getting back from Vegas would like to be clear of hooker-induced herpes.

---

### Post by Stephen Morgan on 2010-12-02
> **bobman500 said:**
> Can somebody please tell me how the hell to get Vista off my machine, preferably using real words. :p

Vista is already gone, "sudo update-grub" will remove it from the menu. The 75gigs formerly occupied by windows is now empty, it hasn't "joined the rest in ubuntu". It's possible through the GPartEd programme to expand the / root partition (on which ubuntu is) to occupy the space, but it's quicker and less risky to create a new partition in that space.

"ext3/ext4" refers to the type of filesystem used by default in Ubuntu, as opposed to NTFS/HPFS and FAT* used in Windows.

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> Again, I am sorry, but I really don't understand what that means.

I had 75gigs put aside in a partition that had Vista on it. I deleted that partition, so I am assuming that 75gigs has now joined the rest in Ubuntu. When I reboot my system, Vista is still there to select.

Can somebody please tell me how the hell to get Vista off my machine, preferably using real words. :p

It's a command to run in a terminal - you managed with the fdisk one so I assumed you'd be ok with this one :)

Basically it will run the various scripts that grub uses to set the menu list up - one of which is os-prober - THAT one looks for any other OS's on the system - as it will not it should update your menu so that vista no longer shows.

You have removed vista - all you have now is a line in the menu list saying vista - which is possibly better than having vista actually work :lol:

---

### Post by carrarin on 2010-12-02
What tool did you use to delete windows Vista 75gb? 
or ... How did you delete it?

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> I have done 'sudo update-grub', but Vista is still selectable, which surely means there is still Windows crap on the machine somewhere, and would like to me clear of it more than a married man getting back from Vegas would like to be clear of hooker-induced herpes.

Please run both of these commands in a terminal - please paste the whole output including the commands in a new post.

It will be long - please put [noparse]```
[/noparse] at the beginning of the paste and put [noparse]
```[/noparse] at the end of the paste.

```
sudo os-prober
cat /boot/grub/grub.cfg
```

---

### Post by bobman500 on 2010-12-02
I deleted it using the disk utility.

OK, it's gone but its annoying name remains. If it's easy to get rid of the name on the boot list, then great, someone tell me, but if it's endlessly complicated, then don't bother.

Could somebody please tell me how I get the now presumably empty 75gigs to 'rejoin' the rest of the storage?

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> Please run both of these commands in a terminal - please paste the whole output including the commands in a new post.

It will be long - please put [noparse]```
[/noparse] at the beginning of the paste and put [noparse]
```[/noparse] at the end of the paste.

```
sudo os-prober
cat /boot/grub/grub.cfg
```

```
 ### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=4a6624d9-2318-4a5b-a2e7-18236953bbfd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=4a6624d9-2318-4a5b-a2e7-18236953bbfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4a6624d9-2318-4a5b-a2e7-18236953bbfd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4a6624d9-2318-4a5b-a2e7-18236953bbfd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4a6624d9-2318-4a5b-a2e7-18236953bbfd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by carrarin on 2010-12-02
So you deleted the partition (the thing with Windows7/Vista), but you have not done anything else. You have not created a new partition?

---

### Post by Elfy on 2010-12-02
All you should have in the menu is 2 sets of linux kernels and a couple of memtest options.

You don't have any ntfs partitions on the drive - unless they are not showing up in fdisk -l.

Have you rebooted since you ran the update-grub command?

---

### Post by bobman500 on 2010-12-02
> **carrarin said:**
> So you deleted the partition (the thing with  Windows7/Vista), but you have not done anything else. You have not  created a new partition?


I don't know! I am an absolute beginner, eagerly awaiting instruction! Other than something to run another OS on, I don't even know what a partition is for!

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> All you should have in the menu is 2 sets of linux kernels and a couple of memtest options.

You don't have any ntfs partitions on the drive - unless they are not showing up in fdisk -l.

Have you rebooted since you ran the update-grub command?


Yes I have rebooted, and yes, "Vista (Loader)" remains clinging on by the fingernails.

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> Yes I have rebooted, and yes, "Vista (Loader)" remains clinging on by the fingernails.

Ok - can you run the os-prober command again and post it's out put as I asked in post #19

If it doesn't actually say anything about vista though don't bother posting it.

Ity might help if you run this script - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions carefully - if the result you get does NOT look like [http://ubuntuforums.org/showpost.php?p=10187947&postcount=6](http://ubuntuforums.org/showpost.php?p=10187947&postcount=6)

Then try the instructions for it here - [http://ubuntuforums.org/showpost.php?p=10187738&postcount=5](http://ubuntuforums.org/showpost.php?p=10187738&postcount=5)

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> Ok - can you run the os-prober command again and post it's out put as I asked in post #19

If it doesn't actually say anything about vista though don't bother posting it.

Ity might help if you run this script - [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions carefully - if the result you get does NOT look like [http://ubuntuforums.org/showpost.php?p=10187947&postcount=6](http://ubuntuforums.org/showpost.php?p=10187947&postcount=6)

Then try the instructions for it here - [http://ubuntuforums.org/showpost.php?p=10187738&postcount=5](http://ubuntuforums.org/showpost.php?p=10187738&postcount=5)


It doesn't say anything about Vista. If it really is only there by name and not taking up any space, I am not that bothered. It would be a huge help if you could tell me how to make the 75gigs of now 'free space' available.

---

### Post by carrarin on 2010-12-02
Your hard drive(the thing that you store your files on) can be divided into separate regions. We call this partitioning(for rather obvious reasons). When you first installed Ubuntu the Ubuntu installer divided your hard-drive into two parts -- an Ubuntu part(called an Ubuntu partition) and a windows part(called an Windows partition). 

This is where things get tricky ... each part(partition) of the hard drive can be formatted differently. Formatting basically writes the file-system on the partition. In your case the Ubuntu partition is probably formatted in ext2 or ext4, your Windows partition is probably formatted in NTFS or fat32.

You dont need to know that information to fix your problem, it is just for future reference. :)

---

### Post by carrarin on 2010-12-02
The easiest way to fix your problem is to use a tool called gparted, but I dont have time right now to explain how this is done :(

---

### Post by germanix on 2010-12-02
Hi bobman500. I can see that a number of people are trying to help you, but as you yourself have said, you are very inexperienced working with linux. Now all of the advice you have been getting here are good advice and valid, but I can see from your questions that you cannot see the wood for the trees at this stage. So my advice to you is similar to what another user already advised namely:
Keep it simple/stupid. Just backup your personal files on Ubuntu to an external drive, then re-install ubuntu new, thereby choosing when prompted by the installer to use the whole disk. After the new install just copy your files back.
This will solve all of your problems and is easy enough to do.

---

### Post by bobman500 on 2010-12-02
> **carrarin said:**
> The easiest way to fix your problem is to use a tool called gparted, but I dont have time right now to explain how this is done :(

I can't even install the damn thing. I downloaded and unzipped it, and now I have a load of folders filled with text files and **** I haven't got a clue about.

I know it's asking a lot. But could somebody, please, please just explain in simple terms, how I can make 75gigs of unallocated free space back into usable space on Linux? It can't be that complicated, surely?

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> It doesn't say anything about Vista. If it really is only there by name and not taking up any space, I am not that bothered. It would be a huge help if you could tell me how to make the 75gigs of now 'free space' available.

First you are going to need to create a partition - as you are not going to be mucking about with mounted partitions you can do this in your running ubuntu.

First install gparted - in a terminal ```
sudo apt-get install gparted
``` or search for gparted in software centre or synaptic - choice is yours.

Now run it - it will be in the sys admin menu - either as gparted or partition editor

You will see a representation of your hard drive - at the left hand side should be a large block that is unallocated - this is where vista was. 

Right click on that block and create a new partition - ext4 and make it as large as it can be 

Then hit the apply button - once that has finished you will have created a partition to use as storage.

Now you will want to get that mounted so it is available when you boot.

So do all of ^^ then please run this command

```
ls -l /dev/disk/by-uuid/
```

paste the output here 

Also what do you want the data storage area to be mounted as - that is what do you want to call it - best to not have lots of words and spaces ;)

---

### Post by akand074 on 2010-12-02
> **bobman500 said:**
> I can't even install the damn thing. I downloaded and unzipped it, and now I have a load of folders filled with text files and **** I haven't got a clue about.

I know it's asking a lot. But could somebody, please, please just explain in simple terms, how I can make 75gigs of unallocated free space back into usable space on Linux? It can't be that complicated, surely?

It isn't. I don't think you'll be able to add it to your Linux while your booted into Linux. The Ubuntu disk you made to install Ubuntu. Put that into your disk drive and run it. Choose "Try Ubuntu" and this will allow you to play around in Ubuntu right off the CD without touching your hard drive. 

1. Go to System > Administration > GParted Partition Editor
2. Now it will show you all your partitions. Your Ubuntu partition should be the file system type "ext4" with mount point "/". You should also be showing 75GB unallocated somewhere if you deleted it correctly.
3. Right click on your Ubuntu partition and select "Resize/Move".
4. Resize it to the max you can (75GB larger than it is now)
5. Confirm and apply all operations. 
6. Shut down, take out the disk.

That should do it.

---

### Post by Elfy on 2010-12-02
> **bobman500 said:**
> I can't even install the damn thing. I downloaded and unzipped it, and now I have a load of folders filled with text files and **** I haven't got a clue about.

I know it's asking a lot. But could somebody, please, please just explain in simple terms, how I can make 75gigs of unallocated free space back into usable space on Linux? It can't be that complicated, surely?

It's not hard nor complicated - but what you have to do is give people a chance to actually answer you - we aren't all waiting for your next post :D

---

### Post by matt_symes on 2010-12-02
Hi

Me thinks, too many cooks in this thread.

Listen to 

forestpiskie

or 

akand074

Kind regards

---

### Post by ArunavAm on 2010-12-02
> **akand074 said:**
> It isn't. I don't think you'll be able to add it to your Linux while your booted into Linux. The Ubuntu disk you made to install Ubuntu. Put that into your disk drive and run it. Choose "Try Ubuntu" and this will allow you to play around in Ubuntu right off the CD without touching your hard drive. 

1. Go to System > Administration > GParted Partition Editor
2. Now it will show you all your partitions. Your Ubuntu partition should be the file system type "ext4" with mount point "/". You should also be showing 75GB unallocated somewhere if you deleted it correctly.
3. Right click on your Ubuntu partition and select "Resize/Move".
4. Resize it to the max you can (75GB larger than it is now)
5. Confirm and apply all operations. 
6. Shut down, take out the disk.

That should do it.
Why don't u use gparted? That's a frontend that will surely help you.
Just keep in mind.. ROOT DRIVE'S mount point is "/" (without the inverted commas).
And select ext4 as the formatting type.

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> First you are going to need to create a partition - as you are not going to be mucking about with mounted partitions you can do this in your running ubuntu.

First install gparted - in a terminal ```
sudo apt-get install gparted
``` or search for gparted in software centre or synaptic - choice is yours.

Now run it - it will be in the sys admin menu - either as gparted or partition editor

You will see a representation of your hard drive - at the left hand side should be a large block that is unallocated - this is where vista was. 

Right click on that block and create a new partition - ext4 and make it as large as it can be 

Then hit the apply button - once that has finished you will have created a partition to use as storage.

Now you will want to get that mounted so it is available when you boot.

So do all of ^^ then please run this command

```
ls -l /dev/disk/by-uuid/
```paste the output here 

Also what do you want the data storage area to be mounted as - that is what do you want to call it - best to not have lots of words and spaces ;)

I have created the partition and everything, how do I mount?

---

### Post by Elfy on 2010-12-02
Please do all the things I ask :)

> 
```
ls -l /dev/disk/by-uuid/
```

paste the output here

Also what do you want the data storage area to be mounted as - that is what do you want to call it - best to not have lots of words and spaces 

---

### Post by bobman500 on 2010-12-02
> **forestpiskie said:**
> Please do all the things I ask :)


Ah, ok, sorry, I thought you wrote mount it THEN post the thing. 

lrwxrwxrwx 1 root root 10 2010-12-02 10:33 221d3590-8cd0-43ca-afed-48a001da02dd -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-12-02 10:33 4a6624d9-2318-4a5b-a2e7-18236953bbfd -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-12-02 11:48 55bc0164-5850-4cca-9752-03cbf9f7d1d1 -> ../../sda1

Don't care what it's called, hard drive 2 or whatever

---

### Post by Elfy on 2010-12-02
Ok - now decide on what you want to call it - I call mine data - I would suggest a single word for it. Below I have used data - change it if you want :)

Then decide if you want an icon for the new area on the desktop or not - if NOT then change all the media to mnt 

In the terminal 

```
sudo mkdir /media/data
```

This gives the system a place to mount the partition.

Now we will be editing the file that tells the system where to mount stuff - before we do so let's back it up 

In a terminal 

```
sudo cp /etc/fstab /etc/fstab.0212
```

Now we can open the file for editing

```
gksudo gedit /etc/fstab
```

Go to the last line then enter a couple of times to get some clear space then paste this in 

```
##/dev/sda1
UUID=55bc0164-5850-4cca-9752-03cbf9f7d1d1 /media/data ext4 defaults 0 2
```
Enter to get a new line and save the file.

Now you should be able to mount it 

In a terminal 

```
sudo mount -a
```

It should look like nothing happens - the terminal should just go back to a prompt.

But you should now have an icon on the desktop that says whatever you called the folder in the beginning.

So you know what I mean by /media and /mnt the lines would read as this if you did not want the icon on the desktop

```
sudo mkdir /mnt/data
```

```
##/dev/sda1
UUID=55bc0164-5850-4cca-9752-03cbf9f7d1d1 /mnt/data ext4 defaults 0 2
```

---

### Post by bobman500 on 2010-12-02
Done, there is an icon for the 75 gig hard drive on the desktop, and now under 'computer' my hard drive says "250 GB Hard drive : 75 GB File System" 

Has the rest of it gone? I didn't even want it on the desktop. I didn't want a partition. I just wanted one hard drive, all available, with no <snip> Vista on it.

---

### Post by bobman500 on 2010-12-02
Now I tried to open it from the dropdown menu, and it says "failed to mount 75 gb Filesystem"

I formatted it and remounted it, but I still don't want it on the desktop, and I still don't know how to access the rest of the hard drive.

What is "lost and found"? It's the only thing on there.

---

### Post by Elfy on 2010-12-02
> I didn't even want it on the desktop. I specifically asked you this - did you not bother to read all of the last post?

> I didn't want a partition. I just wanted one hard drive, all availableTo do that you need to resize the existing drive - not create a new partition.

I am not going to look at this thread again until the morning.

Please do not allow your frustration to get the better of you - keep your language family friendly.

I have edited a post for swearing I do not want to do so again.

---

### Post by bobman500 on 2010-12-02
Look, I am sorry I got angry, but it's because I am posted on an absolute beginner thread, and have been given nothing but jargon I don't understand, and then been told off for not understanding it! 

I DID read your last post, but didn't understand it. Clearly nobody bothered to read my posts because all I wanted was for the 75gig space to combine with the rest, and I made that very clear, but everyone started harping on about the different kinds of partitions there are!

When someone comes on here, and says they really don't understand, how about messaging them? Offering them help at their speed. Instead, I am given half-page instructions I can barely follow, and then berated when I am confused with a message that may as well read "jhfvreuigfbweoifnws6578292.balls"

---

### Post by Elfy on 2010-12-02
Please see my PM

---

### Post by matt_symes on 2010-12-02
Hi

bobman500. Just relax. There are loads of people here to help you. Language _must_ be kept family friendly.

I suggest you sleep on it and pick up this thread tomorrow.

Kind regards

---

### Post by bobman500 on 2010-12-02
I don't have a PM.

---

### Post by akand074 on 2010-12-02
> **bobman500 said:**
> Look, I am sorry I got angry, but it's because I am posted on an absolute beginner thread, and have been given nothing but jargon I don't understand, and then been told off for not understanding it! 

I DID read your last post, but didn't understand it. Clearly nobody bothered to read my posts because all I wanted was for the 75gig space to combine with the rest, and I made that very clear, but everyone started harping on about the different kinds of partitions there are!

When someone comes on here, and says they really don't understand, how about messaging them? Offering them help at their speed. Instead, I am given half-page instructions I can barely follow, and then berated when I am confused with a message that may as well read "jhfvreuigfbweoifnws6578292.balls"

If you read my post earlier. I gave you step by step on how to add that 75GB to your existing Ubuntu partition.

---

### Post by thatguruguy on 2010-12-02
> **bobman500 said:**
> Look, I am sorry I got angry, but it's because I am posted on an absolute beginner thread, and have been given nothing but jargon I don't understand, and then been told off for not understanding it! 

I DID read your last post, but didn't understand it. Clearly nobody bothered to read my posts because all I wanted was for the 75gig space to combine with the rest, and I made that very clear, but everyone started harping on about the different kinds of partitions there are!

When someone comes on here, and says they really don't understand, how about messaging them? Offering them help at their speed. Instead, I am given half-page instructions I can barely follow, and then berated when I am confused with a message that may as well read "jhfvreuigfbweoifnws6578292.balls"

1. Not a single person who has tried to help you so far is being paid to do so. Each of them is simply a user, like yourself, trying to help other users.

2. If you don't understand something, ask.

3. Sometimes, you don't NEED to understand the instructions given. You just need to follow them.

4. Again, this is not a paid help-desk. Getting angry won't help. In fact, it will probably hurt your cause. Anyone who tries to help you is doing so out of the goodness of his or her heart. Negativity and abusiveness on your part makes it less likely that people will feel like helping you.

5. The simplest instruction was given to you on page 3 of this thread, wherein you were told to do this:
> **germanix said:**
> Hi bobman500. I can see that a number of people  are trying to help you, but as you yourself have said, you are very  inexperienced working with linux. Now all of the advice you have been  getting here are good advice and valid, but I can see from your  questions that you cannot see the wood for the trees at this stage. So  my advice to you is similar to what another user already advised namely:
Keep it simple/stupid. Just backup your personal files on Ubuntu to an  external drive, then re-install ubuntu new, thereby choosing when  prompted by the installer to use the whole disk. After the new install  just copy your files back.
This will solve all of your problems and is easy enough to do.
... the fact that you decided not to follow that advice is no one's problem but your own.

6. Did I mention yet that this isn't a paid help desk?

---

### Post by akand074 on 2010-12-02
I agree with the above post, comment 5. If you are still having trouble with my instructions I can try to explain in more detail, but your saying your a beginner and your trying to do something more advanced. If your still having trouble, then yes the easiest and most efficient way to do this, is to reinstall Ubuntu from scratch, using the entire disk. Backup your data before hand. You should have a back up anyways. You never know what might happen unintentionally.

---

### Post by matt_symes on 2010-12-02
Hi

> I agree with the above post, comment 5.akand074. While i don't disagree with you, that is the windows way of doing things.

Maybe for a newbe that is the way, but.....

I would resize said partition as per your instructions.

Kind regards

---

### Post by thatguruguy on 2010-12-02
> **matt_symes said:**
> Hi

akand074. While i don't disagree with you, that is the windows way of doing things.

Maybe for a newbe that is the way, but.....

I would resize said partition as per your instructions.

Kind regards

I'd resize the partition, too. But the OP should just reinstall.

---

### Post by Elfy on 2010-12-02
After a chat on IRC - the OP is going ahead with a resize.

Personally I'd rather have a small / and /home and then other partitions to keep data on. But hey-ho all about choice ;)

---

### Post by thatguruguy on 2010-12-02
> **forestpiskie said:**
> After a chat on IRC - the OP is going ahead with a resize.

Personally I'd rather have a small / and /home and then other partitions to keep data on. But hey-ho all about choice ;)

Good point.  A month after I first started using ubuntu (which was the first linux distro I used day-to-day), I did a full reinstall simply because I hadn't put /home and / into their own partitions.  He'll figure out the benefit of doing that eventually.

---

### Post by amx401 on 2010-12-02
Thank everyone for they're help on this.  I'm learning the command line, but am still a NUB with under a month of linux under my belt.  For the sake of not creating a new forum, and maybe helping this guy in the future, can you please explain to me the benefit of having / and /home on two separate partitions?  

As a noob, I love how linux operates, and this makes it easy for me.  Also, with different partitions, will cd still work to go between / and /home? 

Thanks guys (and gal?)

---

### Post by matt_symes on 2010-12-02
Hi

  > Also, with different partitions, will cd still work to go between / and /home? Yes... but _please_ start a new thread for your questions. Don't muddy the waters.

Kind regards

---

