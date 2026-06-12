---
title: "Asus Eee PC linux"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Astrikor on 2009-01-28
Trying to get this running - all ok except that USB & external drives won't mount.
Any ideas for appropriate sudo code?
Thanks

---

### Post by cmnorton on 2009-01-28
I have not seen the layout of an Asus EEE. Is there a /media directory? You would -- as root -- create a mount directory there, like ex_disk1. Assuming your disk is formatted ext3, you would mount

sudo mount -t ext3 /dev/sdb1 /media/ex_disk1. I may be off on the sdb1. It depends on what your onboard drive is called. You can find that out by entering a df command.


sudo mount /dev/sdb1 /media/

---

### Post by djbushido on 2009-01-28
could you post the output of ```
sudo fdisk -l
``` with the usb devices plugged in?

---

### Post by Astrikor on 2009-01-28
> **cmnorton said:**
> 
sudo mount /dev/sdb1 /media/

results in sudo: /media: command not found.

> **djbushido said:**
> could you post the output of ```
sudo fdisk -l
``` with the usb devices plugged in?


results in fdisk: invalid option --1

Any more ideas please ?
Thanks

---

### Post by arochester on 2009-01-28
Try: forum.eeeuser.com

---

### Post by djbushido on 2009-01-28
Also make sure it is "sudo fdisk -l" with a lowercase "L"

---

### Post by Therion on 2009-01-28
> **djbushido said:**
> Also make sure it is "sudo fdisk -l" with a lowercase "L"
If it helps, my Kingston thumb drive mounts to: **/dev/sdc1** on my eee 1000.

/sda1 and /sdb1 being the 8 and 32 GB SSD drives respectively.

---

### Post by dje on 2009-01-28
I take it you have installed ubuntu on your eeepc?

If so run the following command in the terminal:
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```
In the file that opens look for a line with '/media/cdrom0' in it. Put a # at the very beginning of this line. Save and close the file then try inserting your USB drive again

hope that helps,
dje

---

### Post by Astrikor on 2009-01-29
> **djbushido said:**
> Also make sure it is "sudo fdisk -l" with a lowercase "L"

That makes all the difference and I get a screenful of code as a result - only problem now, how do I list the terminal code on this forum?
Thanks
Astrikor

---

### Post by djbushido on 2009-01-29
ok, change this to ```
sudo fdisk -l > fdisk.txt
```
This will create a file fdisk.txt in the current directory, post the contents of that, preferably inside the "CODE" tag.

---

### Post by Astrikor on 2009-01-29
Thanks djbushido.
sudo fdisk -l results as follows:
```

Disk /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         187     1502046   83  Linux
/dev/sda2             188         241      433755   83  Linux
/dev/sda3             242         242        8032+   c  W95 FAT32 (LBA)
/dev/sda4             243         243        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3936     1007600    e  W95 FAT16 (LBA)

```
So, can anyone see why the USB drive (which sda is it?) "does not have the required permissions" ?

---

### Post by ChildOfMana on 2009-01-29
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3936     1007600    e  W95 FAT16 (LBA)
```

This is your USB drive

**EDIT:** when you say USB drive, do you mean a USB external HDD, or a USB Pen Drive?

---

### Post by redseventyseven on 2009-01-29
Just a hunch - hope this helps!

Have you used the USB drives on a Windows machine before? If so, sometimes if you forget to "Safely Remove" the drive when you were using it in Windows, the drive still registers as still being in use elsewhere.

Try plugging them into a Windows machine, unmount them properly using the "Safely Remove Hardware" utility, and see if that makes any difference.

Not guaranteed to work, but at least it might help to eliminate a possibility...

---

### Post by Astrikor on 2009-01-29
> **ChildOfMana said:**
> when you say USB drive, do you mean a USB external HDD, or a USB Pen Drive?

Th code above was for a 1GB USB pen flash drive.
However, I get a similar result from a 300GB external hard drive connected to the USB socket.

---

### Post by Astrikor on 2009-01-29
> **redseventyseven said:**
> Just a hunch - hope this helps!

Have you used the USB drives on a Windows machine before? If so, sometimes if you forget to "Safely Remove" the drive when you were using it in Windows, the drive still registers as still being in use elsewhere.
...
No luck - I have even tried reformatting to FAT32 but still the same permission block.

---

### Post by Astrikor on 2009-01-29
A new angle on this issue.
I have discovered that looking at the properties of the inaccessible file gives a Permissions tab.
In that tab are a list of permissions for read, write, Exec and Special for Owner, Group and Others.  All options are greyed out so I cannot edit them.
Both the Owner and the Group are stated t be "Root" so it seems to me that the Owner and Group need to be User ? But how to change these settings?
Any ideas?
Thanks

---

### Post by ChildOfMana on 2009-01-29
[This]("http://www.psychocats.net/ubuntu/mountlinux") might help.

Scroll to the bottom and read the part about changing ownership and permissions.

---

### Post by dje on 2009-01-29
**I had this problem when i installed Ubuntu Eee on my Eee PC, i fixed it by doing the following**

Run the following command in the terminal (backs up fstab then opens it in a text editor):
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```
In the file that opens look for a line with '/media/cdrom0' in it. Put a # at the very beginning of this line (this line that mounts volumes in the optical drive, obviously the eee pc does not have an optical drive and this messes things up). Save and close the file then try inserting your USB drive again

hope that helps,
dje

---

### Post by Astrikor on 2009-01-29
> **ChildOfMana said:**
> [This]("http://www.psychocats.net/ubuntu/mountlinux") might help.

Scroll to the bottom and read the part about changing ownership and permissions.

Thanks, looks as if its the same sort of thing, but I don't understand it.  I bought this Eee PC only three days ago - how do Asus expect general public to cope with these Linux issues (Curry's couldn't help - and neither could the Asus tech help line!)

Can anyone decipher ChildOfMana's suggestion in the context of my previous code as above and suggest apprporiate code to change user to allow anyone to access any USB drive?
Thanks

---

### Post by Astrikor on 2009-01-29
> **dje said:**
> 
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```dje

Doesn't work for me, I get as follows:
bash: gksu: command not found

---

### Post by ChildOfMana on 2009-01-29
Just to clarify; have you installed Ubuntu on your EeePC or are you using the OS that came with it (based on Xandros I believe)?

---

### Post by Astrikor on 2009-01-29
> **ChildOfMana said:**
> Just to clarify; have you installed Ubuntu on your EeePC or are you using the OS that came with it (based on Xandros I believe)?

It is just as it came out of the box.  I don't know which Linux version is in use - how do I identify it?

---

### Post by ChildOfMana on 2009-01-29
Okay, the Linux version the EeePC ships with is a custom version of Xandros Linux.

The commands/advice we've all been giving you are from an Ubuntu perspective.

Though Xandros and Ubuntu are both Linux-based Operating Systems there are many (often subtle, other-times drastic) differences between them.

The procedures in one won't necessarily translate to the other, although many of the commands may be the same.

I'm sure someone on these forums will be able to help you, but you may get a quicker and more accurate answer on the [EeePC User Forums]("http://forum.eeeuser.com/").

---

### Post by ChildOfMana on 2009-01-29
Incidentally, you can try posting your question again (or asking a mod to move this thread) on this very forum in the [Other OS Talk]("http://ubuntuforums.org/forumdisplay.php?f=147") catagory.

Hope you find a solution. :)

---

### Post by oyroy on 2009-01-29
Just a question here. When you say EeePC, do you mean the stationary EeePC, or do you mean one of the netbook (mini-laptop) EeePCs? The Stationary is Called EeeBox or EeeTOP (touchscreen), while the netbooks are called Eee(700/701/900/901/904HD/1000/1000H/S101/N10J - Prob even more, but I cant remember them all). Those are the ones I have personal experience with. 

If you have a netbook-version I would suggest eeebuntu ([http://eeebuntu.org](http://eeebuntu.org)) or the new Easy Peasy ([http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)) for your OS, which has a much better interface and better community (regular ubuntu and the eee-community). I have 2 EeePC (700 Surf 2GB and 901) myself, and never Xandros again. (700 didnt even have ssh built-in!!!).

---

### Post by djbushido on 2009-01-29
Yeah, if it's just out of box, you have Xandros (eww...). Anyway, to mount, try this (with drive plugged in)
```
sudo mkdir /media/usb
sudo mount /dev/sdc1 /media/usb
```
This should mount the device in /media/usb, so check there.
This should work for any machine running Linux with sudo, but post results.

---

### Post by Astrikor on 2009-01-30
> **oyroy said:**
> Just a question here. When you say EeePC, do you mean the stationary EeePC, or do you mean one of the netbook (mini-laptop) EeePCs? The Stationary is Called EeeBox or EeeTOP (touchscreen), while the netbooks are called Eee(700/701/900/901/904HD/1000/1000H/S101/N10J - Prob even more, but I cant remember them all). Those are the ones I have personal experience with. QUOTE]

I had no idea there were so many Eee PC versions - mine is a mini laptop 700 with a 2GB hard drive - hence the need to activate some external storage.  Incidentally, I get the same rejection on inserting an SD card (which would be a preferred small drive extension because it lies within the profile of the case.)

What is "ssh" ?



[QUOTE=djbushido;6642558]
```
sudo mkdir /media/usb
sudo mount /dev/sdc1 /media/usb
```
This should mount the device in /media/usb, so check there.
This should work for any machine running Linux with sudo, but post results.

Still no good.

sudo mkdir /media/usb  results as follows:
"mkdir: cannot create directory'/media/usb' No such file or directory"

sudo mount dev/sdc1 /media/usb results as follows: 
"mount: mount point: media/usb does not exist"

Still looking for ideas - meanwhile I will try the other forums suggested by oyroy.

---

### Post by oyroy on 2009-01-30
It might be you have no /media folder in the first place. The Eee you got I think is the Eee 700 2G Surf. Have the same one myself if thats the case.
Try first "sudo mkdir /media" and then "sudo mkdir /media/usb" if that works.

Else, for other OS, I would reccomend either eeeXubuntu ([http://wiki.eeeuser.com/#eeexubuntu](http://wiki.eeeuser.com/#eeexubuntu)) or eeebuntu Base ([http://eeebuntu.org/index.php?page=base](http://eeebuntu.org/index.php?page=base)). I use the eeebuntu on my 700, tho its only a backup for my Eee 901 atm.

Oh, and ssh is a way to connect to other computers ([http://en.wikipedia.org/wiki/Ssh]("http://en.wikipedia.org/wiki/Ssh")) which is kinda of basic linux-tool. I was just so supprised that a linux-distro came without it :)

---

### Post by djbushido on 2009-01-30
also, try this:
precede my previous commands with the "su" command, and then take out sudo.

And Xandros has no ssh? That really sucks...

---

### Post by Astrikor on 2009-01-30
> **oyroy said:**
> It might be you have no /media folder in the first place. The Eee you got I think is the Eee 700 2G Surf. Have the same one myself if thats the case.
Try first "sudo mkdir /media" and then "sudo mkdir /media/usb" if that works.

Now we're getting somewhere.
Done first "sudo mkdir /media" and then "sudo mkdir /media/usb" and it works.
However, I found I had to repeat this if I removed the USB drive and replaced it - until I tried rebooting the eeepc with the USB drive still in the machine.  Now it recognises it and allows access all the time.  EXCELLENT ! MANY THANKS OYROY

I have another (4GB) usb drive and that has the same problem - but I will try it again after I have emptied and reformatted it.

I also need to set up the SD card drive in the same way.  Should I use "sudo mkdir /media/SD" or is there something else more appropriate?
Thanks

---

### Post by Astrikor on 2009-01-30
Update for anyone interested:

Although the 4GB USB drive receives an "open In File Manager" request, it does not then appear in the file manager.  I have no solution here.  Tried yet another (2GB) USB drive and that works perfectly and allows me the option of transfering files between machines and loading other software via the USB socket.

After applying "sudo mkdir /media/SD" and rebooting, the 4GB SD card now also works perfectly and effectively extends the 2GB hard drive to 6GB withing the existing case dimensions.

Getting to grips with seemingly simple procedures (it's always easy when you know how!) has been a steep learning curve for me on the EeePC software.

I now have a great little notebook to use on my travels.

Many thanks to all those who have contributed to this thread.

Astrikor

---

### Post by ChildOfMana on 2009-01-31
Glad you found your solution Astrikor. Welcome to Linux :)

---

### Post by cjv8888 on 2009-01-31
By the way , there is ssh on the eeepc.  I use that to link the eeepc Xandros to my Ubuntu desktops all the time.

---

### Post by stalkingwolf on 2009-01-31
I have an EEE 701 4G.  Right after I got it I installed 8.04.1
EEE version.  I have never had a problem with any external media.
Thumb drives ( i use 4 different ones.) Sd cards (it came with a 4gb one)
or my USB CDRW.  The internal wireless works better than some of my full sized laptops.

---

