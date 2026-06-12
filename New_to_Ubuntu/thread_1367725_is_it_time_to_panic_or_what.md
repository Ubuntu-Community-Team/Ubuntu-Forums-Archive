---
title: "is it time to panic or what?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Festerbaun on 2009-12-29
To say that I am a newbie would be an understatement.  If anyone can help with this problem I would be most appreciative.  Here is the problem.  I deleted a partition from my hardrive using Ubuntu Remix.  Rebooted and now I get the following message.  
 
error:  unknown filesystem
grub rescue
 
I'm pretty much lost here guys.  Since I'm using a netbook I have no optical drives.  I backed up my windows restore disk to flash drive and tried to boot, no luck.  I tried using my flash that I have Ubuntu on and no luck.  I'm really frustrated at this point.  <insert sigh here>

---

### Post by Project PWNED on 2009-12-29
You deleted your Windows partition?

---

### Post by Festerbaun on 2009-12-29
ok, let me try this againl.  I don't know if I deleted the windows os or not, I really don't think I did because my windows partition was showing a 30gig partition and the one I deleted was 70+gig

---

### Post by Festerbaun on 2009-12-29
I installed Ubuntu twice (I told you I was a newbie).  That left me with a few partitions that were not being used.  I read some forums and made the decision to delete one of the partitions.  I deleted the partition and I'm sure it wasn't my windows os partition, and Ubuntu was still running fine until I rebooted the system.  Now, I get nothing.

---

### Post by tom.swartz07 on 2009-12-29
> **Festerbaun said:**
> To say that I am a newbie would be an understatement.  If anyone can help with this problem I would be most appreciative.  Here is the problem.  I deleted a partition from my hardrive using Ubuntu Remix.  Rebooted and now I get the following message.  
 
error:  unknown filesystem
grub rescue
 
I'm pretty much lost here guys.  Since I'm using a netbook I have no optical drives.  I backed up my windows restore disk to flash drive and tried to boot, no luck.  I tried using my flash that I have Ubuntu on and no luck.  I'm really frustrated at this point.  <insert sigh here>

ALrighty, it sounds like you threw GRUB into a panic, but you dont need to panic yourself. Easy to fix.

When you deleted your partition, you most likely deleted Windows, as your Ubuntu partition would have been locked (it was in use at the time)

What you need to do is get a hold of an Ubuntu LiveUSB. Most likely the one you used to install Ubuntu in the first place. 

When you get that, boot to it and select 'try ubuntu w/out changes'

It will load to the desktop. Open the Terminal (apps>accessories>terminal) and type ```
sudo update-grub
```

This will look through your installed partitions and update your GURB bootloader so that you could get back into your system.
That should solve your problem. 
If you need any more help, just give a shout!

---

### Post by tom.swartz07 on 2009-12-29
Actually, It might be better if, when you open the terminal, post the output of the command ```
sudo fdisk -l
```

This way we could get a better look at what your harddrive looks like.

---

### Post by stlsaint on 2009-12-29
> **tom.swartz07 said:**
> ALrighty, it sounds like you threw GRUB into a panic, but you dont need to panic yourself. Easy to fix.

When you deleted your partition, you most likely deleted Windows, as your Ubuntu partition would have been locked (it was in use at the time)

What you need to do is get a hold of an Ubuntu LiveUSB. Most likely the one you used to install Ubuntu in the first place. 

When you get that, boot to it and select 'try ubuntu w/out changes'

It will load to the desktop. Open the Terminal (apps>accessories>terminal) and type ```
sudo update-grub
```

This will look through your installed partitions and update your GURB bootloader so that you could get back into your system.
That should solve your problem. 
If you need any more help, just give a shout!


The poster has stated...1)They did not delete Windows...2)They are on a netbook..not able to boot cd!

I suggest booting windows to make sure all is well and then boot into usb that you used to install windows. if you installed ubuntu twice as you state then you have a small bit of mess to clean up. Boot into usb and see if you can access the internet from it...then go into your terminal, Applications>Accessories>Terminal 
and run
```
gksudo gedit /boot/grub/menu.lst
``` (unless your on karmic then it would be grub.cfg) and post the contents of it here. Also do as last poster suggested and in another terminal run: ```
sudo fdisk -l
``` and post the output of that here as well!

---

### Post by Festerbaun on 2009-12-29
I cannot boot into anything at this point.  I have the flash drive that I installed Ubuntu with and I've tried to boot with it and again, no luck.  I cannot boot to windows or Ubuntu.  I can only get as far as 
 
error:  unknown filesystem

---

### Post by Festerbaun on 2009-12-29
The only command that I can get any response with is   "ls".  I get a string of (hd0) (hd0,7)  etc. etc.

---

### Post by stlsaint on 2009-12-29
> **Festerbaun said:**
> The only command that I can get any response with is   "ls".  I get a string of (hd0) (hd0,7)  etc. etc.

in terminal can you run: ```
sudo fdisk -l
``` 
and post exactly what you get here?

---

### Post by stlsaint on 2009-12-29
> **Festerbaun said:**
> I cannot boot into anything at this point.  I have the flash drive that I installed Ubuntu with and I've tried to boot with it and again, no luck.  I cannot boot to windows or Ubuntu.  I can only get as far as 
 
error:  unknown filesystem

If you say you did not touch windows partition in any way than you may want to try and use recovery cd's (if you have them to fix startup errors for windows).

---

### Post by cprofitt on 2009-12-29
I am unfamiliar with the model you have, but you may have to hit an F-key like F12 or some such to get it to give you 'boot options' and then select the USB drive. That should let you boot again to the LiveUSB.

Let me know if that helps... and then I, or others, can help further.

---

### Post by Festerbaun on 2009-12-29
This is one of the biggest reasons I'm so excited about Ubuntu/linux (the community).  I'm working on it guys thanks for all the info.  I'll post when I get some results to share.

---

### Post by starcannon on 2009-12-29
Note:
The "Esc"ape key is a common boot menu key as well; so, if F12 doesn't get you a boot menu, give Esc a try.

---

### Post by Festerbaun on 2009-12-30
Let me see if I can be more specific and see if this helps out.  I am running a Dell mini 10 netbook that came with Windows XP.  After I deleted a partition on my hard drive I then rebooted.  After reboot I get this error
 
error: unknown filesystem
grub rescue>
 
Trying to boot into either windows or ubuntu (had dual boot) has failed.  Using the same sd card that I originally put ubuntu on the netbook in the first place has yielded no results so far.  Made a flash copy of my windows dvd and tried to boot to it also yielded no results.  I've noticed in the forums that sometimes the devil is in the details so to speak so here is the exact sequence I followed to get at this most frustrating point.
 
Downloaded Ubuntu-remix to flash card
installed on netbook
my 2  year old turned my computer off during installation and it crashed
could not get ubuntu to boot up
re-installed ubuntu a second time which resulted in "extra" partitions
re-install worked great and ubuntu worked fine
backed up ubuntu files from flash drive to external hard drive
reformatted flash drive
decided to reclaim unused partitions and deleted a partition from hard drive using ubuntu
all went well until I rebooted and got error mentioned above
tried to reinstall copied files back to flash drive and reboot with no results
 
Now, I cannot boot into windows or ubuntu.  Using F12 and selecting usb boot has no effect.  Copied Windows restore dvd to flash and tried to reboot to flash again, no results.

---

### Post by Methuselah on 2009-12-30
ESC is a possible key to get the boot menu.
On the eeepc this is the key used.
Just keep hitting ESC as the machine starts up since you said F12 doesn't work.
A Grub screwup should not prevent you from booting from a USB stick and that would be really helpful to resolve the issue.

---

### Post by TBABill on 2009-12-30
Festerbaun, is it possible when you reformatted the flash card that you did not make it bootable? I know it sounds overly simplistic (and is likely not the problem), but if the files were simply copied to it, just as it would fail on a flash drive, it would not be recognized as a bootable device.
 
Do you have the ability to use a USB Flash Drive on your system? I would assume you have USB ports. If you have access to another computer and a flash drive you could create a bootable drive with the Ubuntu .iso. Then you'd have to run the liveUSB and make the system changes necessary to restore the computer.
 
I think the first order of business, however, is to figure out why the system will not boot from your Windows backup. To me that suggests your backup of the DVD is somehow either not setup as bootable or is corrupt because it should have a boot loader as well.

---

### Post by Festerbaun on 2009-12-30
Pressing the *esc* key has very little effect on the system.  I do get a very brief (to brief to read) screen that pops up but immediately it goes back to my grub error screen.
 
The first time I tried to boot from flash I did not have the ISO image file on the flash card, just a back up of the files.  I then downloaded the Ubuntu remix file for a second time to flash just as I did when I first set the machine up.  This time it was exactly as it was when I first installed Ubuntu, tried to boot from flash with no luck. 
 
I have an extra box that I'm goint to install Ubuntu on, and once installed I'm going to try and use that to make a bootable flash.  But I just can't figure out why the flash card didn't work once I downloaded the ISO file the second time.....  The saga continues.

---

### Post by Festerbaun on 2009-12-30
This is what is on my flash card at this time.
 
ubuntu-9.10-netbook-remix-1386.iso
 
My computer will not boot with this.

---

### Post by eeeandrew on 2009-12-30
Theres a problem with that.On your working box go into system->administration and select USB startup creator. Select the 9.10 iso and the USB stick you wish to make bootable. Now it should allow you to boot from it. 

If your on windows then google a program called unetbootin and this will allow you to do the same. 

To answer your original question, its not time to panic yet!

Good luck.

---

### Post by rottentree on 2009-12-30
I don't know what netbook you are using but on my Asus 1005ha I had to enter the BIOS(with F2) then I had to disable 'Bootbooster' there and only after that did pressing the ESC key work properly.

This might help if I understood your previous post correctly.

---

### Post by FinalCoyote on 2009-12-30
This seems like you don't have a bootable USB stick.

However if it worked before, it should work this time too.

Look in the netbook's manual / instructions, it should tell you how to get to the BIOS and change the boot priority.

---

### Post by spiky001 on 2009-12-30
i googled  that latop f2 to get in to bios

---

### Post by cprofitt on 2009-12-30
if there is an .iso file on your memory stick that is not what is needed. That .iso file has to be used to create a boot device. Usually a CD, but you can make a one with the LiveCD 'USB Startup Disk Creator' found on the System | Administration menu.

---

### Post by 2lagos on 2009-12-30
I think you deleted the partition that has c kernel in it maybe u should run it again. Is just an opinion

---

### Post by TBABill on 2009-12-30
The .iso file should only be on the hard drive you downloaded it to. When you create a bootable flash drive or memory card, your system will format that item as bootable AND it will expand the .iso into directories and files necessary to be executed (including the boot loader). The .iso file cannot boot directly just as a .iso file. Brasero or similar apps will do all the work for you. 
 
I would recommend you go to another machine or a friend's machine, taking the .iso with you since you have it on the flash card. COPY that file to their hard drive and then find the right app for their operating system that can create a bootable flash card or USB flash drive. Run that program and select the .iso file for it to create the bootable device from.
 
After you create the bootable source, look at it under whatever file manager they have (windows explorer or other) and you will not see the .iso file listed. There are other files and directories....letting you know it's done correctly. If you only see the .iso you have missed a step or two along the way.

---

### Post by Festerbaun on 2009-12-30
Here is a screen shot of of my hard drive partitions before I started deleting stuff.  If you look to the right side of the shot you will see two partitions 63gig and a smaller partition like 3 or 4gig.  these are the two I deleted. I know it wasn't the partition for the ubuntu I was using becaue I tried to delete it to and it wouldn't let me :).  Windows was clearly labeled OS and I didn't delete that.  I'm going to try some of the suggestions here and see what I can come up with.  I've got to get my other box setup with ubuntu first tho.  Thanks for all the replies and suggestions folks.

---

### Post by Roger Allott on 2009-12-30
> **Festerbaun said:**
> This is what is on my flash card at this time.
 
ubuntu-9.10-netbook-remix-1386.iso
 
My computer will not boot with this.

That's where your problem is!

---

### Post by Festerbaun on 2009-12-30
finally got ubuntu to boot from flash drive.  can anyone help with where to go from here?  How can I figure out what is wrong?

---

### Post by Festerbaun on 2009-12-30
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5249    42117128    7  HPFS/NTFS
/dev/sda3           18184       19457    10233405   db  CP/M / CTOS / ...
/dev/sda4            5250       18183   103892355    5  Extended
/dev/sda5           17827       18183     2867571   82  Linux swap / Solaris
/dev/sda6            5250        9377    33158097   83  Linux
/dev/sda7            9378        9560     1469916   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2021 MB, 2021654528 bytes
20 heads, 19 sectors/track, 10390 cylinders
Units = cylinders of 380 * 512 = 194560 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10391     1974145+   6  FAT16

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> finally got ubuntu to boot from flash drive.  can anyone help with where to go from here?  How can I figure out what is wrong?

Alright, great news.

go to applications>accessories>terminal

type in ```
sudo fdisk -l
```
and paste the output here

and type in ```
sudo update-grub
```
and paste the output here also.

Ill keep this page open so i could see it asap when you reply, I could take it from here.

---

### Post by Festerbaun on 2009-12-30
here is the out put

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5249    42117128    7  HPFS/NTFS
/dev/sda3           18184       19457    10233405   db  CP/M / CTOS / ...
/dev/sda4            5250       18183   103892355    5  Extended
/dev/sda5           17827       18183     2867571   82  Linux swap / Solaris
/dev/sda6            5250        9377    33158097   83  Linux
/dev/sda7            9378        9560     1469916   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2021 MB, 2021654528 bytes
20 heads, 19 sectors/track, 10390 cylinders
Units = cylinders of 380 * 512 = 194560 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10391     1974145+   6  FAT16
ubuntu@ubuntu:~$

---

### Post by danastasio on 2009-12-30
Did
```
sudo update-grub
```

do anything?

Love your signature BTW :D

---

### Post by Festerbaun on 2009-12-30
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by tom.swartz07 on 2009-12-30
Alrighty.
I just got a good look at your system. Phew. Its a little messy, but we could definitely save it.


I need you to follow these step by step. If you have any question, at all, ASK. As we do this, its critical that you follow them and only do what is needed, otherwise you will end up losing everything on your drive.

I will try to be as descriptive as possible.

First, go to system>administration>gparted. (if it isnt there, install it from the software center-applications>software center)

It will open and show you a bar graph representing your hard drive.

Now we need to clean up the drive from your extra install (there's no sense in leaving 2 complete installs of Ubuntu on your system)

Select SDA7 and click the trash can at the top. This will get rid of your extra swap partition. Click Apply (the checkmark)

You can, if you so choose, extend your Linux partition - SDA6- to the end of your drive so that it will give you more room to do things once you get it up and running. Just click it, and then select the arrow with a line at the end ->| and extend it to the end of the drive (all of the gray space at the end.

Click apply and let it do its thing.

Now, we will rebuild your GRUB bootloader. 

Go to applications, Accessories, Terminal.

type```
sudo mount /dev/sda6 /mnt
```
then ```
sudo mount /dev/sda2 /mnt
```

Next type ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Now, just to be sure, type
```
sudo update-grub
```


This will restore the Grub bootloader to point to your 2 OS's, Windows and Ubuntu.

Reboot your computer, and you should be set

---

### Post by Festerbaun on 2009-12-30
Ok, I'm trying to follow this to the letter.  I know how stupid this next question is going to sound but, I don't see a trash can at the top.

---

### Post by Festerbaun on 2009-12-30
Does the key icon mean anything?  There is a key icon beside sda7 as well as a few more.

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> Ok, I'm trying to follow this to the letter.  I know how stupid this next question is going to sound but, I don't see a trash can at the top.

My bad, its the circle with the cross through it. I had it confused with the older version.

The keys mean that your drives are locked. You need to right click them, and either select 'unmount' or 'swapoff'. It will ask you if you are sure, say yes and continue.

---

### Post by lavinog on 2009-12-30
I think what you did was you erased an old ubuntu partition that was still being used by grub.  Grub can only be setup to use one partition.

You need to reinstall grub:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

It might be easier to erase the other ubuntu partition and reinstall ubuntu completely.
You should remove the extra swap partition too.

not sure what partition 3 is, does anyone else know?

Edit: For some reason, I didn't see the last couple of posts after refreshing the page.

---

### Post by Festerbaun on 2009-12-30
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

Looks good so far.
Try rebooting without your USB. It should boot back up like usual. If not, Restart with the USB and let me know.

---

### Post by theozzlives on 2009-12-30
GOD! He has a Dell Mini 10!!! Do people read? To the poster: in your Windows, without installing Ubuntu, use unetbootin to create your flash drive, then boot off it. Select "Try without changes to my computer", then run sudo fdisk -l and post the results here.

---

### Post by tom.swartz07 on 2009-12-30
> **theozzlives said:**
> GOD! He has a Dell Mini 10!!! Do people read? To the poster: in your Windows, without installing Ubuntu, use unetbootin to create your flash drive, then boot off it. Select "Try without changes to my computer", then run sudo fdisk -l and post the results here.

I believe that if you 'had read' the post, you would see that the OP had accidentally ruined his GRUB bootloader, and was unable to boot into anything.

I respectfully ask that you keep comments of this type for the community cafe.

---

### Post by theozzlives on 2009-12-30
> **tom.swartz07 said:**
> I believe that if you 'had read' the post, you would see that the OP had accidentally ruined his GRUB bootloader, and was unable to boot into anything.

I respectfully ask that you keep comments of this type for the community cafe.

GRUB has nothing to do with a live USB, Mr. "Extra Shot"

---

### Post by tom.swartz07 on 2009-12-30
> **theozzlives said:**
> GRUB has nothing to do with a live USB, Mr. "Extra Shot"

I am not here to argue or point fingers. I am certain that the aid that other members and I have provided have helped the OP not only diagnose the problem (He or she had installed Ubuntu twice, and deleted one version of Ubuntu, thus sending GRUB into a panic), but allowed us to aid him or her re-create a LiveUSB to not only do what you had told the OP to do, but to also remove the extraneous install and restore the GRUB bootloader to a working condition. 


The number of posts has absolutely nothing to do with the quality of aid that I can provide. I have been through the process of restoring GRUB bootloaders nearly a dozen times. I appreciate the willingness to help, but I do not believe that it is productive to harass and demean others trying to help.

I again respectfully ask you to keep this kind of behavior out of the support forums.

---

### Post by Festerbaun on 2009-12-30
> **theozzlives said:**
> GOD! He has a Dell Mini 10!!! Do people read? To the poster: in your Windows, without installing Ubuntu, use unetbootin to create your flash drive, then boot off it. Select "Try without changes to my computer", then run sudo fdisk -l and post the results here.


I read one time, back in 87" I think it was.  Though I can't recall the article seems it was an obscure author a Mr. Chesterton I believe.

Tom, thanks for all the help you've given, it has really been very helpful and I am at least able to get a different messge.

sh grub> ( I think that is what it said anyway.)  I still could not boot to either os.

---

### Post by theozzlives on 2009-12-30
> **tom.swartz07 said:**
> I am not here to argue or point fingers. I am certain that the aid that other members and I have provided have helped the OP not only diagnose the problem (He or she had installed Ubuntu twice, and deleted one version of Ubuntu, thus sending GRUB into a panic), but allowed us to aid him or her re-create a LiveUSB to not only do what you had told the OP to do, but to also remove the extraneous install and restore the GRUB bootloader to a working condition. 


The number of posts has absolutely nothing to do with the quality of aid that I can provide. I have been through the process of restoring GRUB bootloaders nearly a dozen times. I appreciate the willingness to help, but I do not believe that it is productive to harass and demean others trying to help.

I again respectfully ask you to keep this kind of behavior out of the support forums.

Once he gets booting into a live Ubuntu environment, he can restore his system. Or, if he chooses, his recovery info is on sda1. I wouldn't go that route however. I apologize, I just get frustrated when people offer advice on a eeepc when he stated he had a Dell Mini 10. I'm here to help, not criticize.

---

### Post by Festerbaun on 2009-12-30
No offense Oz, but you are assuming that I know how and what to do which I do not.  I know very shameful.  If you would, please give me step by step instructions as you would explain it to a child.

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> I read one time, back in 87" I think it was.  Though I can't recall the article seems it was an obscure author a Mr. Chesterton I believe.

Tom, thanks for all the help you've given, it has really been very helpful and I am at least able to get a different messge.

sh grub> ( I think that is what it said anyway.)  I still could not boot to either os.

This means that you have GRUB installed, but it doesnt know where to look.

Okay, Since youre back up in LiveUSB, try this
I don't know if this totally fixes the problem, but its well worth a shot.

System > Administration > Synaptics Package Manager,
searched for grub-pc,
right-click on the entry in the list and select "Mark for Reinstallation",
and then apply the changes.

Post the updated output of 
```
sudo fdisk -l
```

Reboot, and see if it helps. 

If not, You might have to go through the steps I had listed with the grub-install. This time, mount all Ubuntu related partitions.



sudo mount /dev/sda6 /mnt
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

This will mount all of your partitions and refresh the Grub Install.

---

### Post by theozzlives on 2009-12-30
> **Festerbaun said:**
> No offense Oz, but you are assuming that I know how and what to do which I do not.  I know very shameful.  If you would, please give me step by step instructions as you would explain it to a child.

I'm not a good teacher, but I'll try. On your Windows Box, go to Google and search for unetbootin. Download and install it and start the program. You'll need the *.iso for the netbook remix. Load the *.iso, with the flash drive in, and create your live USB. When you boot, choose "Start without any changes to your computer". Post back when you get in the live environment.

---

### Post by tom.swartz07 on 2009-12-30
Looking up the solution further:

I found this method also.

If you get the prompt again,

```
sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/[COLOR="Red"]sda2[/COLOR] loop=/ubuntu/disks/root.disk ro
sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot

```

I have sda2 highlighted because you might have to enter sda1, sda2, sda3... etc until you find the location of the partition.

Follow this guide- several people said this helped the best.
[http://ubuntuforums.org/showpost.php?p=8330593&postcount=20](http://ubuntuforums.org/showpost.php?p=8330593&postcount=20)

Let me know! Im hoping this works!

---

### Post by Festerbaun on 2009-12-30
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5249    42117128    7  HPFS/NTFS
/dev/sda3           18184       19457    10233405   db  CP/M / CTOS / ...
/dev/sda4            5250       18183   103892355    5  Extended
/dev/sda5           17827       18183     2867571   82  Linux swap / Solaris
/dev/sda6            5250       17826   101024689+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2021 MB, 2021654528 bytes
20 heads, 19 sectors/track, 10390 cylinders
Units = cylinders of 380 * 512 = 194560 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10391     1974145+   6  FAT16

---

### Post by Festerbaun on 2009-12-30
is that output good or bad?

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> is that output good or bad?

it seems the grub install didnt take effect.

Try running it again, or follow the link in my previous post to boot from the grub:sh> prompt.

You might want to print out the guide if you do not have another computer available.

---

### Post by Festerbaun on 2009-12-30
Thanks Tom, I am up and running again.

---

### Post by tom.swartz07 on 2009-12-30
> **Festerbaun said:**
> Thanks Tom, I am up and running again.

AWESOME!

Im glad you got it to work.

PS- dont forget to mark this thread as solved from the thread tools so that others with the problem could refer here for help!

---

### Post by cprofitt on 2009-12-31
Thanks Tom for getting him through this... great to see the community work.

---

