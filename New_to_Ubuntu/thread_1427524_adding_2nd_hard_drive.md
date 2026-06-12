---
title: "adding 2nd hard drive"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by albert s on 2010-03-11
ubuntu 9.10  32bit
Hi, currently have an HDD on sata, I would like to install a 2nd HDD, an IDE one,
the 2nd drive already has ubuntu on it, do I need to use Gparted to clean and format this drive(before I add it, its already in another old PC I have)? ext3/ext4.?
my current drive has /  =ext4   ,    /home  =ext3
am I also correct in thinking as I am adding an IDE drive to SATA then I set the 2nd(IDE) drive to master?
thanks.

---

### Post by LowSky on 2010-03-11
IDE and Sata use different controller, don't worry about what the IDE drive is set to, but if its the only one set it to Master to make it easy to remember for the future.

I would check BIOS before you boot to make sure which drive is chosen for primary boot. The format the drive to whatever you like. FAT32 is a great choice is you want to use the drive for backups, this way a Windows PC can also read the files.

---

### Post by albert s on 2010-03-11
thanks lowsky, I thought I needed to use NTFS for windows and ubuntu access.?
I have NO windows PCs at present, but is providing an option for the future,
perhaps split the drive 50/50, I dont want to lose too much speed(my PC isnt a rocket ship as it is!  :D
yes, I only have one IDE drive, main drive is SATA. both are only 80G each.
do I need to format before installing it?

---

### Post by ayenack on 2010-03-11
If you've got nothing on the drive that you want to keep then format it. Also when you install you'll need to make a directory on it for your files. We'll assume that the drive is /dev/hda1/ it may be different so open a terminal and type.

```
sudo fdisk -l
``` (That's an non capitol L at the end. This will bring up info on your drives you should be able to work out which is the new drive from here.)

Then.

```
sudo mkdir /dev/hda1/my_files
``` (This will make a folder on the drive called my_files then you'll need to change the permissions on the folder like so.

```
sudo chown your_user_name:your_user_name /dev/hda1/my_files
```

After this you can use the folder to put files in.

---

### Post by eriktheblu on 2010-03-11
Windows will read NTFS or FAT but not EXT. Linux support of NTFS has not always been as good as it is now, so FAT has been traditionally recommended. If you're not planning to use MS Windows, I would recommend EXT3 or EXT4 as those systems fragment considerably less than the MS natives.

If you don't need the data on the second drive, I would go ahead and format it. Depending on your BIOS settings, it may try to boot to the second drive. Just to be on the safe side, boot with a live CD first, and remove the boot flags from the IDE drive.

I read once with multiple HDDs you can spread your swap space between them to improve performance. You might consider that as well.

If you want to do 50/50, I would suggest the last half formatted as EXT, and leave the front half unformatted. This way you can later format the NTFS, install MS, and take advantage of the minor speed improvement of the front of the drive. If you end up not installing MS, you don't have to worry about deleting the NTFS partition should you choose to expand.

---

### Post by ayenack on 2010-03-11
Windows can be made to read ext3 not to sure about ext4 though.

Take a look at this.

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

---

### Post by albert s on 2010-03-11
thanks ayenack, and eriktheblu, I have no intention of putting windows on this PC,
was thinking of a future PC perhaps having windows on it,
but couldnt I just then send the files to windows from my ubuntu machine? then I could have my new drive on ext3/4?
I have backed up the files I need to keep to an external HDD.
will do this at the weekend, and boot from liveCD just to check all is well first, 
thanks folks.  :)

---

### Post by ayenack on 2010-03-11
Yes you could do this. An easy solution would be to share a folder on the drive using SAMBA which will make it a network share.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Or you can right click on the folder and select share. Think there may be a problem with SAMBA on 9.10 though so do a google search on it.

And yes you can have ext3/4.

---

### Post by albert s on 2010-03-11
like I already share folders between my PC and the wifes laptop ? (both on ubuntu though)
if so then I have no worries, just format in ext and Im done.
it means I can pick and chose which folders are accessible to other machines.

---

### Post by albert s on 2010-03-12
sorry to drag this back up again,
but do I need a mount point on my second hard drive?
I would prefer to have it mounted permanently if possible,
ie, as if I have a 160g HDD as such instead of two 80g drives.
thanks.

---

### Post by ayenack on 2010-03-12
The drive will be mounted at boot. But like I said you'll need to create a folder on it to put files into.

It's possible to make the whole drive owned by your user but better to make a folder and use that to put files into. It's theoretically more secure to do it this way.

You'll find the folder you created in places under the name you called it.

It's kinda like having a 160GB drive as the folder will appear as a folder within the file directory and will appear as if it's just another folder.

So if the Hard Drive was an newly added 8GB drive formatted to EXT3/4 it'd automatically be owned by root and you'd have no access to it so you'd have to create a folder using mkdir (Make Directory) and chown (Change Owner).  Lets say it's called music then you could chuck a bunch of music into it. 

Bit complicated and not explained to well but hopefully you get the gist.

My previous post explains how to use chown and how to make a folder.

As for sharing folders between your PC and your misses lappy if you're using SAMBA then yes.

Just as a foot note you could use FAT32 as a previous poster suggested and the drive would just pop up and be available to all users but there are no permission settings with FAT32 so anyone can access it. So if you're paranoid or security aware it's not the best solution.

---

### Post by albert s on 2010-03-13
thanks ayenack, I think Ive got the gist of it.
I suppose once I get it in and running it will make more sense to me.
sorry about the simple questions.
Im not good with computers in any OS, but I seem to get on with ubuntu much better than anything else,(including windows!).
it just does what you ask it to do.

---

### Post by frank cox on 2010-03-13
Hi:

  I have a 40gb hd {ide] formatted to ext3 connected to my Ubuntu machine by a USB bridge. The other drives in the machine are sata if that matters.

I used the command sudo mkdir /dev/sdc1/my-files and it tells me it is not a directory.
I went ahead and reformatted to fat32 but would like to know the solution for leaving it as ext3 and using with bridge to shuttle files.

Thanks

---

### Post by ayenack on 2010-03-13
OK lets say you've formatted the drive to ext3 and it's called usbdrive to add a folder to it you'd do this.

```
sudo mkdir /media/usbdrive/my_files
```

You may be able to write to it without having to do this so test first. The media tags is used because it's a removable drive.

Then change permission on the folder as described in my earlier post.

---

### Post by frank cox on 2010-03-15
> **ayenack said:**
> OK lets say you've formatted the drive to ext3 and it's called usbdrive to add a folder to it you'd do this.

```
sudo mkdir /media/usbdrive/my_files
```You may be able to write to it without having to do this so test first. The media tags is used because it's a removable drive.

Then change permission on the folder as described in my earlier post.

Thanks,when I formated it to fat it worked but now I know.

---

### Post by lyall on 2010-03-15
see the following link for InstallingANewHardDrive
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

this link should answer your question about adding a second hard drive

if you have time to look over TitleIndex Ubuntu documentation
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")

there is a lot a info to help you get your laptop/pc work the way you like

good luck and have fun learning

---

### Post by ayenack on 2010-03-17
> **lyall said:**
> see the following link for InstallingANewHardDrive
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Just a quick comment on this guide. Where it say to use:-

```
sudo gparted 
``` Use instead:-

```
gksudo gparted 
``` There's a possible permissions issue with using sudo to open a graphical programme apparently.

---

