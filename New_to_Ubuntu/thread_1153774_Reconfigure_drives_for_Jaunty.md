---
title: "Reconfigure drives for Jaunty"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-09
Hi. Having messed about quite a bit with Ubuntu I have ended up with rather a complex setup of drives, and I would like to reconfigure them.

The current setup is like this:
hda1   Windows C:
hda5   Windows D:
hda6   Windows E:
hda7   Ubuntu / (Small)
hda8   Swap
hda9   Ubuntu /home (Small)

hdb1   Ubuntu / (Current Main Install)
hdb2   FAT32 storage drive
hdb3   Ubuntu /home (Current Main Install)

As you can see this was a windows installation - the small version of Ubuntu was added as a dual boot, and when I realised I preferred Ubuntu the current main installation was added, clearing out two other Windows partitions.

My current aim is for hda to become the main Jaunty installation, while hdb remains as *this* installation and the FAT32 storage partition.

However, there is a problem - Somehow, and not deliberately, I ended up sharing hda8 as the swap drive (I think! - At least there is no other swap partition). Also GRUB has all three of these OS's in the list, and I'm not sure how it would react when two of them are removed and replaced.

The reason for keeping the current installation is because I simply don't have the space to back it all up. Once Jaunty is installed I would transfer data across from the current installation, and then use the partition editor etc, to reformat hdb as a storage area.

Any ideas about how to best proceed with this? Like I said, I can't back *everything* up from hdb at the moment, so that has to stay AND be accessible.

If you need any other information please just ask.

cheers

Max

---

### Post by Didius Falco on 2009-05-09
> **MaxVK said:**
> Hi. Having messed about quite a bit with Ubuntu I have ended up with rather a complex setup of drives, and I would like to reconfigure them.

The current setup is like this:
hda1   Windows C:
hda5   Windows D:
hda6   Windows E:
hda7   Ubuntu / (Small)
hda8   Swap
hda9   Ubuntu /home (Small)

hdb1   Ubuntu / (Current Main Install)
hdb2   FAT32 storage drive
hdb3   Ubuntu /home (Current Main Install)

As you can see this was a windows installation - the small version of Ubuntu was added as a dual boot, and when I realised I preferred Ubuntu the current main installation was added, clearing out two other Windows partitions.

My current aim is for hda to become the main Jaunty installation, while hdb remains as *this* installation and the FAT32 storage partition.

However, there is a problem - Somehow, and not deliberately, I ended up sharing hda8 as the swap drive (I think! - At least there is no other swap partition). Also GRUB has all three of these OS's in the list, and I'm not sure how it would react when two of them are removed and replaced.

The reason for keeping the current installation is because I simply don't have the space to back it all up. Once Jaunty is installed I would transfer data across from the current installation, and then use the partition editor etc, to reformat hdb as a storage area.

Any ideas about how to best proceed with this? Like I said, I can't back *everything* up from hdb at the moment, so that has to stay AND be accessible.

If you need any other information please just ask.

cheers

Max

Let me just be sure I'm understanding what you want to do - do you want to get rid of all the windows partitions, and the Ubuntu (small) partitions on hda?

---

### Post by MaxVK on 2009-05-09
Yes, everything on hda is to become Jaunty (Three partitions - / home and swap).

Everything on hdb is to stay and the Ubuntu installation on hdb must remain bootable.

Unfortunately Ubuntu on hdb shares the swap on hda8.

cheers

Max

---

### Post by Didius Falco on 2009-05-09
That's not a problem. You can share a single linux swap file with as many linux installs as you have. I currently have 5 linux installs and they all use the same swap file.

Boot up with your Live CD and choose the "make no changes to this PC" option. After it boots, open Gparted from **System/Administration/Partition Editor** and delete:

hda1   Windows C:
hda5   Windows D:
hda6   Windows E:
hda7   Ubuntu / (Small)
hda9   Ubuntu /home (Small)

You can also delete and recreate hda8   Swap, if you want to position it at the very end of the drive. It won't hurt anything, and I'd do it if it were me, just to make things more tidy.

Then create your partitions. I'd suggest making a primary partition at the very front of the drive for your / partition. Then make an Extended Partition to hold your Logical drives. All the rest of your partitions will be created inside the Extended partition.

Next, make a partition for /Home.

Optionally, you can make another partition that will hold only your own data - name it whatever you want,it's not a system partition, it's just a place to put your own files and downloads. You can set it up to automount later after you get the installation done. 

If you do this, you can adjust the size of your /Home partition downwards, since your /Home partition will only have configuration files and emails, etc.

Then create the Linux Swap partition at the very back end of the Drive, inside the Extended partition.

For partition sizes, I'd suggest:

Root (/) - no more than 10-15 gigs. You'll have room to install a ton of stuff without running out of room.

Home - This depends on if you make the separate Data partition. Without a separate Data partition, go large, since this is where all your stuff, including downloads, music, etc. will go. With a separate Data partition, you can keep this down to about 10-15 Gigs and devote the rest of the space to your Data partition.

Data - see Home <G>

Swap - no larger than the amount of ram you have, and if you have more than 2 gigs, unless you edit very large files or use Hibernation, not even that much. I set mine at 5 gigs initially, and it never got used at all. The next time I installed a version of Ubuntu, I resized it down to 500 megs and it has still never been used.

After you have your partitions all set up, you are ready to start the install. When it gets to the partitioner, choose the **Manual (Advanced)** option, this will let you set up your handcrafted partitions. Highlight the Primary partition and click the **Edit Partition** button at the bottom of the partition screen. Set it to **Use**, **ext3** (or **ext4** if you want, but I'd suggest sticking with **ext3** for now - this is, after all, your main install) and set the **type** to /.

Do the same thing for your /Home partition. The Data partition, if you do that, can be labeled whatever you want, and you don't need to do anything aside from that.

The Swap partition doesn't need to be set up either - Ubuntu will see it and use it.

Then proceed with the install and be sure and let it write Grub. Grub will pick up the install on hdb and put it on the Grub menu.

That's it. It probably took me longer to type this out than it'll take for you to do this and finish the install - I'm horribly slow at typing.

Enjoy your new 9.04 setup!!

I hope this helps...

Regards,

Didius

---

### Post by MaxVK on 2009-05-09
Thanks Didius, that pretty much everything covered! one thing though - Will the hdb Ubuntu (The current installation) still be able to pick up the Swap? 

It wont be on the same partition once things have all changed - I'm planning on just the three partitions on hda, root, home and swap.

I know the sizes will be a bit over the top, but I use lots of space, which is why a large home partition *and* another 180G drive (hdb) will be used.

cheers

Max

---

### Post by Didius Falco on 2009-05-09
You'll have to edit the fstab file in the current install on hdb to reflect the new location - you can do that from the new install before you boot into one on hdb. the fstab is located at /etc/fstab on the partition on hdb that holds your soon-to-be old install. 


Post back after your done and let us know how it all went.


Regards,

Didius

---

### Post by MaxVK on 2009-05-10
Thanks Didius, I will do that - it might be helpful for someone else as well.

cheers

Max

---

### Post by MaxVK on 2009-05-10
Well, here I am on the LiveCD of Jaunty, and I'm doing my last minute checks to make sure I know exactly what I doing and where I'm going, and I realise that a question has not been asked!

> You'll have to edit the fstab file in the current install on hdb to reflect the new location - you can do that from the new install before you boot into one on hdb. the fstab is located at /etc/fstab on the partition on hdb that holds your soon-to-be old install.

Yes, Iv found that file already, just to make sure I know where I'm going, but I have realised that I have no idea what to *DO* with the file to edit it!

As you may imagine from my first post, there is quite a bit in there and I'm not 100% on what I should change. Ill post it below so you can see what I mean:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=1f07b51c-0271-473a-b4ce-ab277bb1a465 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=529a4c3b-5317-42dc-890d-8f0552aba081 /home           ext3    defaults        0       2
# /dev/hda1
UUID=72BC6E91BC6E4FA1 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D608058608056739 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=B24C9C1A4C9BD785 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=33234d93-9787-4e54-b670-a0c193a8ab83 /media/hda7     ext3    defaults        0       2
# /dev/hda9
UUID=703a8a85-fc86-46de-8fdc-2c58a2569f3d /media/hda9     ext3    defaults        0       2
# /dev/hdb2
UUID=42744CED744CE56F /media/hdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=b35ce5fe-7753-4ab4-ba0f-cd0bd2fe516e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

I can see the swap partition, but there is a whole lot more on there that I have no idea what to do with.

Any ideas?

[EDIT]
Also of possible concern - I just ran the partition editor and it found all my drives but is now calling them sda,sdb etc, which I know is not correct. It should be hda and hdb. Is this likely to cause a problem?
[/EDIT]

cheers

Max

---

### Post by Didius Falco on 2009-05-10
> **MaxVK said:**
> Well, here I am on the LiveCD of Jaunty, and I'm doing my last minute checks to make sure I know exactly what I doing and where I'm going, and I realise that a question has not been asked!



Yes, Iv found that file already, just to make sure I know where I'm going, but I have realised that I have no idea what to *DO* with the file to edit it!

As you may imagine from my first post, there is quite a bit in there and I'm not 100% on what I should change. Ill post it below so you can see what I mean:

<snip>

I can see the swap partition, but there is a whole lot more on there that I have no idea what to do with.

Any ideas?

[EDIT]
Also of possible concern - I just ran the partition editor and it found all my drives but is now calling them sda,sdb etc, which I know is not correct. It should be hda and hdb. Is this likely to cause a problem?
[/EDIT]

cheers

Max

On the partitioner - no, that isn't a problem. The fstab and menu.lst don't know and don't care what the partitioner calls the partitions.

After you finish all your partitioning, you'll want to make sure that all the partitions are listed correctly in your menu.lst and fstab files.

Download the BootInfoScript in my signature to your desktop in the Live CD, open a terminal and type (or cut and paste from here) ```
sudo bash ~/Desktop/boot_info_script*.sh
```.

That will produce a file named RESULTS.txt on your desktop. That file will contain information on all your drives, including the the new (hdx,y) and UUID info for all your partitions. It will also include copies of all your fstab and menu.lst files.

You can use that information to update those files on your drives. Just make sure that you check the (hdx,y) and UUID information for all your partitions, and edit them to reflect the new layout. Take your time. I find it helpful to copy the fdisk and blkid info and make a Master list of all my drives and what is on them. That gives you an easy-to-read reference that makes the editing of the fstab and menu.lst easier, and you can save it for future reference. I'm running 5 Ubuntu installs, for various purposes, so it can be confusing to keep everything in proper order otherwise. But you do whatever works best for you

Here is my master list:

```
sda1      (hd0,0)     Windows                          UUID=F454DABF54DA83B0                          /media/windows

  sda2      (hd0,1)     Extended Partition               n/a

  sda5      (hd0,4)     Linux Swap                       UUID=17dc755b-447b-4d6e-ba41-b60ef443d2ae       n/a

  sda6      (hd0,5)     Ubuntu 8.10                      UUID=349b1101-7d7d-4a0a-a364-a024bc2edd64      /media/810root

  sda7      (hd0,6)     Ubuntu 8.10 Home                 UUID=425a90ab-ea30-4a3a-a62e-d171e9844783      /media/810home

  sda8      (hd0,7)     (Win) File Storage               UUID=01C95D7514150B10                          /media/filestorage

  sda9      (hd0,8     (win) Backups                    UUID=01C95D7515140480                          /media/backups

  sda10     (hd0,9)     Ubuntu 9.04 Live CD Build        UUID=b6db7389-4840-4362-9685-fa57a431d8b5      /media/904livecd

  sda11     (hd0,10)    Ubuntu 9.04 32 Bit               UUID=e02ddaef-9065-4851-a66f-b417af080bc6      /media/jaunty32

  sda12     (hd0,11)    (Ext3) Data                      UUID=1e6ae425-84ca-4fb7-949b-6f38e2b24c67      /media/data

  sda13     (hd0,12)    Ubuntu 9.04 64 Bit               UUID=b99e7427-253b-4f2c-b72f-b494e8955ddb      /media/jaunty64

  sda14     (hd0,13)    Ubuntu 9.04 For Karmic Koala     UUID=eb10f132-4dbe-4e71-9b11-8c2aad061f5f      /media/karmic
```

That way, at a glance, I can see the list of all my drives in both the sdaX and (hdx,y) what is on that drive, the UUID number for that drive and the mount point to use in case I want to mount them in an install.

But as I said above, you use whatever system works best for you.

I think you'll do fine - you've certainly done your homework. If you do run into any problems or further questions, just post 'em.

Regards,

Didius

---

### Post by MaxVK on 2009-05-10
Thanks Didius - lots of helpful information that I would have had to go and find!

One thing: (another one!) If I just install Jaunty on hda as planned but don't edit the fstab on hdb, am I right in thinking that hdb will still be accessible as data on Jaunty? It just wont be able to boot, yes?

I'm just making sure that I understand things correctly, because it might be that I don't even need to edit the old fstab on hdb.

If the old hdb installation is available as data then I am thinking that I should be able to copy any required data across directly (such as emails and config files etc). Is this correct?

If it is, then my next question is: Presumably the new install of GRUB will find the old hdb installation and add it to the startup menu, so is it then possible to remove that item (Old hdb) from the GRUB list so that the machine simply boots without the need for the grub menu at all?

thanks for your patience

regards

Max

---

### Post by Didius Falco on 2009-05-10
> **MaxVK said:**
> Thanks Didius - lots of helpful information that I would have had to go and find!

One thing: (another one!) If I just install Jaunty on hda as planned but don't edit the fstab on hdb, am I right in thinking that hdb will still be accessible as data on Jaunty? It just wont be able to boot, yes?

I'm just making sure that I understand things correctly, because it might be that I don't even need to edit the old fstab on hdb.

If the old hdb installation is available as data then I am thinking that I should be able to copy any required data across directly (such as emails and config files etc). Is this correct?

If it is, then my next question is: Presumably the new install of GRUB will find the old hdb installation and add it to the startup menu, so is it then possible to remove that item (Old hdb) from the GRUB list so that the machine simply boots without the need for the grub menu at all?

thanks for your patience

regards

Max

Hi Max,

If you do not intend to boot into the old install, and indeed plan on deleting it after you've moved your files across to the new 9.04 install, then you needn't bother with the fstab and menu.lst files of the old install.

You will be able to copy things across at will - just be careful of pulling system level things. Stick to your own data, including email, wallpaper, etc. You shouldn't need to copy things out of anywhere except your /Home folder.

AAMOF, you can just copy your entire Home folder to your new /Home partition. You'll have to reinstall the programs that use that data, but all your settings will be the same.

Here is a guide that is really based on creating a separate /Home partition after the install. The part you may find useful is towards the end, labeled > What If It Doesn't Work.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

you should use the same username and password as in your old install. I always duplicate everything - my name, my username, password and the pc name.

When you boot up for the first time, things will look pretty much the same - menus, wallpaper, etc. Depending on what theme you were using, that will probably be the same as well.

Now, onto the Grub question. Do [COLOR=Red]NOT[/COLOR] delete you menu.lst or fstab in your new install. You can set the amount of time the Grub menu waits before starting the default menu choice in your menu.lst file. You could also deleted the old install information from your menu.lst, but I'd recommend just putting a # at the start of every line of that installation, until you are ready to just delete it from the hard drive. Here is an example:

```
#title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda6)
#root        (hd0,5)
#kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=349b1101-7d7d-4a0a-a364-a024bc2edd64 ro single 
#initrd        /boot/initrd.img-2.6.27-11-generic
#savedefault
#boot
```To set the time before it boots into the default, change the timeout setting. Again here is mine - notice that I have it set to -10. That means it will sit forever at the menu until I make a choice.

You could set it to 5 seconds, or even lower, but I find it's better to give yourself a few seconds of slack in case you need to use Recovery Mode or an older kernel. Still, if you wanted to, you could set it to 0 and the grub menu would go just boot up the default choice.

And if elected, I promise to....oh....that always happens when I prattle on too long. :P

Regards,

Didius

---

### Post by MaxVK on 2009-05-11
Thanks again Didius. Prattle? No way! Its only prattle if its of no use, and I can honestly say that Iv learned more in this thread than I did in three days of Googling.

Having read, re-read, re-considered, and re- read this thread again, it seems that my best course of action is to install Jaunty on hda as planned, but to leave hdb alone entirely.

Once I'm in Jaunty I can then pick and choose which configuration files I will want, and I can leave things like music and video files on my old home partition, which will end up as data storage in any case.

My original intention was to keep the old installation running, kind of like an emergency backup (thats a bit more friendly than the Live CD), but there really is little point, and if I keep the old Home folder in place as is, it just means that my new home folder wont be so cluttered with odds and ends.

I think I'm pretty much ready to go now, so thanks again for all your excellent (and patient) help. Ill post back when I'm running Jaunty!

regards

Max

---

### Post by MaxVK on 2009-05-11
Well, I'm now in Jaunty thanks to your help Didius, so very many thanks to you.

Now Iv just got to try and sort out why my Firefox bookmarks file on the old system don't appear to be the latest up to date ones and how to transfer all my auto login data to the new Firefox, why the restricted drivers manager failed and then refuses to appear again,why searching for available drivers never completes, how to.... :P

Iv just remembered why I hate upgrading!

Anyway, thanks again

Regards

Max

---

### Post by Didius Falco on 2009-05-11
> **MaxVK said:**
> Well, I'm now in Jaunty thanks to your help Didius, so very many thanks to you.

Now Iv just got to try and sort out why my Firefox bookmarks file on the old system don't appear to be the latest up to date ones and how to transfer all my auto login data to the new Firefox, why the restricted drivers manager failed and then refuses to appear again,why searching for available drivers never completes, how to.... :P

Iv just remembered why I hate upgrading!

Anyway, thanks again

Regards

Max

You are very welcome!

I'm glad it all worked well for you. You certainly did your research, and that it's always easier that way - "measure twice, cut once" is soo true.

The way I transferred all my Firefox settings was to navigate to the ~/.mozilla folder (~/ is a shortcut to your username folder) account on your old install, copy and paste it to the ~/ folder on your new account.

I've done the same thing with my Thunderbird Email and account settings and my Pidgin settings.

Firefox = ~/.mozilla
Thunderbird = ~/.mozilla-thunderbird 
Pidgin = ~/.purple

I just paste them in and tell it to merge all and replace all when it asks. Pidgin gave me a bit of a fight, but I got it working fairly quickly - much easier than recreating all that crap by hand. The .mozilla folder will contain your passwords list.

For the bookmarks, have a look through the .mozilla folder and see if you had more than one account. Look for bookmarks.html and see if you have more than one.

To help backup your Firfox settings, there is an extension I use named FeBe that will back everything up. You can set it up to do it at set intervals, set where to back it up, what exactly to back up, etc.

It's easy to use to restore your settings, too.

I'm glad it is all working out - you'll get the little kinks straightened out soon enough, and you can always start a new thread in the forum for help.

Regards,

Didius

---

