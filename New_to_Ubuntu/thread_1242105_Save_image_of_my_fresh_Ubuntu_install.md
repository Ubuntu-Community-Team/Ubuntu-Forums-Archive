---
title: "Save image of my fresh Ubuntu install"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-16
Is it possible to save an image of my fresh Ubuntu install?  I have worked very hard to configure everything "just so" and would like to image / snapshot it so that:

a)  I can use it as re-install if my install goes bad at a future date
b)  I can use it as install for a guest OS (virtual box)

Is it possible to kill these 2 birds with 1 stone?

I would like to store the image / snapshot on CD / DVD.

Thanks in advance for your input!

---

### Post by papuccino1 on 2009-08-16
Interested in this as well. I hope someone can answer! :)

---

### Post by Paqman on 2009-08-16
Take a look at Partimage, it's in the repos. It can create backups of individual partitions or whole drives.

---

### Post by bluelamp999 on 2009-08-16
Take a look at this...

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by colau on 2009-08-16
> **cat2005 said:**
> Is it possible to save an image of my fresh Ubuntu install?  I have worked very hard to configure everything "just so" and would like to image / snapshot it so that:

a)  I can use it as re-install if my install goes bad at a future date
b)  I can use it as install for a guest OS (virtual box)

Is it possible to kill these 2 birds with 1 stone?

I would like to store the image / snapshot on CD / DVD.

Thanks in advance for your input!
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by philcamlin on 2009-08-16
or you could use remastersys :popcorn:

---

### Post by cat2005 on 2009-08-17
Using partimage via systemrescue didn't work....most likely I did something incorrectly...but the images didn't go to the destination I stated.  Infact, I still can't find them.

Any thoughts, or alternatives to systemrescue?

---

### Post by colau on 2009-08-17
> **cat2005 said:**
> Using partimage via systemrescue didn't work....most likely I did something incorrectly...but the images didn't go to the destination I stated.  Infact, I still can't find them.

Any thoughts, or alternatives to systemrescue?
Is it ubuntu 9.04 with ext4?

---

### Post by nhasian on 2009-08-17
+1 for Clonezilla

---

### Post by ashwinhgtx on 2009-08-17
Clonezilla. Just make sure that you read the manuals before attempting anything.

---

### Post by mapes12 on 2009-08-17
> **cat2005 said:**
> Using partimage via systemrescue didn't work....most likely I did something incorrectly...but the images didn't go to the destination I stated.  Infact, I still can't find them.

Any thoughts, or alternatives to systemrescue?Yeh, using Partimage can be a bit confusing. Once you have booted your system with the Systemrescue disk it will come to a Terminal prompt with some commentary above it with choices. If you type "wizard" it will load a GUI to help you on your way. Once in the GUI the first thing to do is to create a mount point then mount the drive you want to save to. Let's say you have "/" on sda5 and /home on sda6. You need to mount the partition where you want the image to be _saved_. Let's assume you want to put the image onto the /home partition (you can move it or burn it to CD/DVD later). At the Terminal type ```
mkdir /mnt/mydir
```this creates a directory called "mydir" inside the  root directory for mounting stuff at /mnt. 

Then```
mount /dev/sda6 /mnt/mydir
```This creates a mount point connecting sda6 (your /home partition) to the Linux operating system that's running in memory. In plain English: it tells Linux that a storage device is connected to it and makes it available to be written to via the /mnt/mydir directory.

Minimise the Terminal then select partimage from the GUI menu. _Carefully_, work through the options using your tab key to move around and the space bar to select options. The first option asks which partition you want to save. Select sda5. The next option asks you to input the directory to save the file and give it a name. Type > /mnt/mydir/filenamewhere the file name is one of your choice. (N.B. the filename will automatically have .000 after it so just be aware of that.) F5 to go to the next screen where you have some compression options. I don't use any compression cos sometimes I have restore problems if I use it. However, It's worth trying compression and testing a restore to see if it works for you.

Then you have an option to check the partition before saving. I always have this selected. To the right of that you have some options for what you want your machine to do when the operation is complete. Make a selection.

Underneath the Options section you then have to make some choices about splitting up the file. I always select the first one. i.e only split the file if the operation runs out of space (it never does cos I always make sure there's plenty of space on the partition I'm saving to).

If all looks OK F5 again will bring up a summary of the operation about to commence. It might take a few seconds to come up. If everything looks good to go then OK that and off it goes.

Once the Systemrescue CD is removed and your system boots in the normal way your image file will be waiting for you in the /home directory for you to move it or whatever. 

If you have a second HDD hooked up when running partimage you could just change the device name e.g. sdb5 for the first logical partition in the second HDD. If you don't know the partition names then when in the Terminal from the Systemrescue CD ```
fdisk -l
``` I would recommend doing this anyway because some live CD's change the names of your partitions e.g. the name might change from sda5 to hda5. So worth a check.

To restore follow through the above but change the options to restore instead of save.

Partimage completely images everything inc Grub. So when you restore an image just reboot your system and everything works. No need to fiddle around with any other settings.

An alternative to using the Systemrescue disk is to use [PING]("http://ping.windowsdream.com/") (Partimage Is Not Ghost). It has a simpler interface to get partimage working and I found some tutorials on Youtube. But the Live CD can be problematic with some machines.

Mark

---

### Post by Cheesemill on 2009-08-17
+1 for [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")
 
It will do everything you need and it's easy to use.

---

### Post by cat2005 on 2009-08-18
[
colau, et al


No, it is ext3 but yes, it is 9.04.

I didn't get a chance to try it yesterday - maybe I can try it again today or tomorrow.   Knowing me, I probably missed some small detail.  I will take a look at the suggestions given by others too.  Thanks a bunch!

---

### Post by cat2005 on 2009-08-19
mapes12, et al:

If I create an image via partimage, then could I load that same image into virtualbox?  Thus, my virtual Ubuntu would be a direct image of my real Ubuntu.

If yes, then which of these would I need to image:

a)  /
b)  swap
c)  home
d)  combination of the above.

I would assume all 3 but I don't know for sure.  For example, swap is typically empty, isn't it?  How would image an empty partition?

Thanks.

---

### Post by LewRockwell on 2009-08-19
just throwing in another vote for that stand-alone utility that, once you've worked past the learning curve(true of everything in life, especially the good stuff), will work no matter what data you're trying to clone/copy...


[http://clonezilla.org/](http://clonezilla.org/)

.

---

### Post by cat2005 on 2009-08-19
> **LewRockwell said:**
> just throwing in another vote for that stand-alone utility that, once you've worked past the learning curve(true of everything in life, especially the good stuff), will work no matter what data you're trying to clone/copy...


[http://clonezilla.org/](http://clonezilla.org/)

.


So many clonezilla votes....I'll give it whirl....

---

### Post by mapes12 on 2009-08-20
> **cat2005 said:**
> mapes12, et al:

If I create an image via partimage, then could I load that same image into virtualbox?  Thus, my virtual Ubuntu would be a direct image of my real Ubuntu.

If yes, then which of these would I need to image:

a)  /
b)  swap
c)  home
d)  combination of the above.

I would assume all 3 but I don't know for sure.  For example, swap is typically empty, isn't it?  How would image an empty partition?

Thanks.Hi cat2005

Unfortunately, I've never used virtualbox so can't help with that question. Sorry.

Maybe someone else can pick it up.

Mark

---

### Post by longtom on 2009-08-20
> **Cheesemill said:**
> +1 for [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")
 
It will do everything you need and it's easy to use.

Had some trouble with it - and as soon as I did I was [on my own.](http://ubuntuforums.org/showthread.php?t=1242557)  

But if it works the way they describe it it would be really easy to use.

My next try is clonezilla - watch this space....:P

---

### Post by mapes12 on 2009-08-20
> **longtom said:**
> Had some trouble with it - and as soon as I did I was [on my own.](http://ubuntuforums.org/showthread.php?t=1242557)  

But if it works the way they describe it it would be really easy to use.

My next try is clonezilla - watch this space....:PI also had trouble with Remastersys.

I tried Clonezilla but couldn't figure it out. If you find out how to use it would you be kind enough to post back a step by step please?

TIA

Mark

---

### Post by longtom on 2009-08-20
> **mapes12 said:**
> I also had trouble with Remastersys.

I tried Clonezilla but couldn't figure it out. If you find out how to use it would you be kind enough to post back a step by step please?

TIA

Mark

I will.  There is a step by step [ here](http://clonezilla.org/clonezilla-live/doc/).

However - I still had some questions [here](http://ubuntuforums.org/showthread.php?p=7816540#post7816540) and hope I find somebody who can assist us.

---

### Post by robert shearer on 2009-08-20
> Had some trouble with it - and as soon as I did I was on my own. 

Did you try posting to the remastersys forum  ??

[http://www.geekconnection.org/remastersys/forums/index.php](http://www.geekconnection.org/remastersys/forums/index.php)

(scroll down to the Ubuntu sub-forum when you get there.)

---

### Post by slakkie on 2009-08-20
> **lewrockwell said:**
> just throwing in another vote for that stand-alone utility that, once you've worked past the learning curve(true of everything in life, especially the good stuff), will work no matter what data you're trying to clone/copy...


[http://clonezilla.org/](http://clonezilla.org/)

.+1

---

### Post by longtom on 2009-08-20
> **robert shearer said:**
> Did you try posting to the remastersys forum  ??

[http://www.geekconnection.org/remastersys/forums/index.php](http://www.geekconnection.org/remastersys/forums/index.php)

(scroll down to the Ubuntu sub-forum when you get there.)

Somebody else did before me.  I found his post there through google. He/she didn't get any meaningful help.  It's a strange one...

---

### Post by mapes12 on 2009-08-20
Hi longtom

I've had another go with Clonezilla and found out where I was going wrong last time. The learning for me came from experimenting with Partimage where I managed to get my head round creating then mounting a virtual directory. With the Systemrescue CD you have to do this manually. I learnt how to do this from a tutorial on Youtube. With Clonezilla it does this bit for you. I had to tell it what to mount and then Clonezilla automatically mounted it at /home/partimag

The other thing that confused me last time was I didn't realise that the partition I had to mount was the partition where I wanted the image saved _to_ or restored _from_. Previously, I was selecting the partition I wanted to create _from_ and that's why I couldn't figure it out.

Coming back to Clonezilla, it has many features that could be useful. To highlight just a few:

- As I said above it automatically creates its own mount point. I had to do this manually with Partimage

- It has more applications to carry out the cloning like ntfsclone, partimage, dd. It selects the most appropriate one depending what it finds on the partition

- It will clone an enter disk even where there are separate partitions on it. With partimage I had to make separate images of each partition

- When the operation is complete and you select the option to reboot, it automatically ejects the CD tray. With partimage I had to press the eject button manually just at the right time between the kill process and reboot.

There are many other things it can do but my configuration is not appropriate to test them just yet.

I successfully made an image of "/" partition and restored it. The only thing was that when I rebooted from the successfully restored image the Ubuntu loading logo came up with the orange progress line but after a few seconds it disappeared to a screen of scrolling text as Ubu booted. I think this is only cosmetic (but annoying :mad:) as once loaded up everything seems to work fine.

Just need a fix for that scrolling text issue now............

---

### Post by longtom on 2009-08-20
Great that you got it going.  Some nice tips as well.

I also have that scrolling text on some machines - on others I don't.

In the meantime I found remastersys working quite nicely on a Ubuntu in a virtual machine.  Did an iso and restored it in another virtual machine without a hitch.

Haven't tested with a DVD on another real machine yet - but that is encouraging nevertheless, as I want to have one standard, customised 
Ubuntu for all.
I was hoping I could use my present working one - but alas, I couldn't.  Since the group 'vboxuser' appears to be the culprit, I will not install VB on my standard edition of Ubuntu and have high hopes that all will be just fine.

If not - you'll be the first one to know. :P

---

### Post by cjv8888 on 2009-08-20
> **cat2005 said:**
> mapes12, et al:

If I create an image via partimage, then could I load that same image into virtualbox?  Thus, my virtual Ubuntu would be a direct image of my real Ubuntu.

If yes, then which of these would I need to image:

a)  /
b)  swap
c)  home
d)  combination of the above.

I would assume all 3 but I don't know for sure.  For example, swap is typically empty, isn't it?  How would image an empty partition?

Thanks.

I do not think you can use the image for VirtualBox as that is a guest OS in a different environment with many different parameters.

---

### Post by cat2005 on 2009-08-20
mapes12 (and anyone else who can answer):

When you write:

[B]Let's say you have "/" on sda5 and /home on sda6. You need to mount the partition where you want the image to be _saved_. Let's assume you want to put the image onto the /home partition (you can move it or burn it to CD/DVD later). At the Terminal type      Code:
     mkdir /mnt/mydir 
this creates a directory called "mydir" inside the  root directory for mounting stuff at /mnt. 

Then     Code:
     mount /dev/sda6 /mnt/mydir 
This creates a mount point connecting sda6 (your /home partition) to the Linux operating system that's running in memory. In plain English: it tells Linux that a storage device is connected to it and makes it available to be written to via the /mnt/mydir directory.[/B] 


Do I do those commands in terminal before using partimage?  Or, do I do them in terminal while I have the partimage cd (sysrescueCD) mounted and running (sysrescueCD has a terminal I can use)?

Or does it not matter?

Thanks.

---

### Post by sumeshgupta on 2009-08-21
You can make a Live CD of your Ubuntu Box which can be then carried around . It also has an option to install. The install will be with your configuration. Please check this out at :
[PHP]http://www.geekconnection.org/remastersys/capink.html
[/PHP]
I have made one. Now I dont have to reconfigure my Ubuntu Box whenever I install in a new PC.:guitar:

---

### Post by robert shearer on 2009-08-21
> In the meantime I found remastersys working quite nicely on a Ubuntu in a virtual machine. Did an iso and restored it in another virtual machine without a hitch.

Can you share how you overcame your initial setback ??

Great to hear you have it working. :)

---

### Post by longtom on 2009-08-21
> **robert shearer said:**
> Can you share how you overcame your initial setback ??

Well - I didn't.  It still doesn't work for my real machine - the one I am typing from now.  This is the setup I would have used for future setups.

Since this wasn't working, as described, and I don't think clonezilla or partimage lend themselves to this job, I tested an install on a virtual setup.

All I do now is installing an Ubuntu setup the way I like it in VirtualBox and remaster it from there.  I will not install VirtualBox on my virtual system, since this appears to be the culprit for my initial failure on my live system.

I am busy making an iso as I write.  I will test it in a virtual setup and afterwards on a real machine.

Since this isn't my thread I might not find it again - so keep asking if you are interested and I'll be happy to keep you posted.

---

### Post by howefield on 2009-08-21
> **mapes12 said:**
> ...The only thing was that when I rebooted from the successfully restored image the Ubuntu loading logo came up with the orange progress line but after a few seconds it disappeared to a screen of scrolling text as Ubu booted. I think this is only cosmetic....

Clonezilla replaces the Ubuntu grub with its own, but as you say it is pretty much cosmetic. The scrolling text is still happening in the Ubuntu grub, just that you do not see it.

I don't think there is a fix as such, but you could, if it really annoys you reinstall grub from a live cd.

---

### Post by robert shearer on 2009-08-21
> Since this isn't my thread I might not find it again - so keep asking if you are interested and I'll be happy to keep you posted.

Oops, I came in late so apologies to the O/P for the cross-posts :oops:

---

### Post by longtom on 2009-08-21
> **robert shearer said:**
> Oops, I came in late so apologies to the O/P for the cross-posts :oops:

I am sure he will forgive you.

I have successfully installed my customised Ubuntu on a virtual machine from a DVD.

I run a setup on a different machine just to confirm this will work as well.  It appears that login screen, wallpapers and themes are not part of the iso.  A small price to pay....

---

### Post by pawhtiobo on 2009-08-21
Hi :)

Another way to do it...

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

Download and burn de CD, boot and use the last version of Norton Ghost :), do a image to a external HD :)

It works for me...

see ya...

---

### Post by longtom on 2009-08-21
> **pawhtiobo said:**
> Hi :)

Another way to do it...

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

Download and burn de CD, boot and use the last version of Norton Ghost :), do a image to a external HD :)

It works for me...

see ya...
 Thanks for the link...

---

### Post by pawhtiobo on 2009-08-21
Glad i could help :)

see ya...

---

### Post by longtom on 2009-08-21
@ robert shearer

I have installed my custom Ubuntu successfully on a different PC (different MB, CPU, screen, HD and ram)  and all worked well.

This is too easy really.  I will, in future, customise the Ubuntus I am giving away in VirtualBox according to the needs and likings of those receiving it.

---

### Post by mapes12 on 2009-08-21
> **cat2005 said:**
> mapes12 (and anyone else who can answer):

When you write:

[B]Let's say you have "/" on sda5 and /home on sda6. You need to mount the partition where you want the image to be _saved_. Let's assume you want to put the image onto the /home partition (you can move it or burn it to CD/DVD later). At the Terminal type      Code:
     mkdir /mnt/mydir 
this creates a directory called "mydir" inside the  root directory for mounting stuff at /mnt. 

Then     Code:
     mount /dev/sda6 /mnt/mydir 
This creates a mount point connecting sda6 (your /home partition) to the Linux operating system that's running in memory. In plain English: it tells Linux that a storage device is connected to it and makes it available to be written to via the /mnt/mydir directory.[/B] 


Do I do those commands in terminal before using partimage?  Or, do I do them in terminal while I have the partimage cd (sysrescueCD) mounted and running (sysrescueCD has a terminal I can use)?

Or does it not matter?

Thanks.Hi cat2005

Have another read of post #11.

You enter those commands in the Terminal that the Systemrescue CD provides.

1. Boot your machine using the System rescue CD

2. Let it load its linux kernel (I think it asks you what country keyboard you have - just enter the number and press Enter)

3. Once everything has loaded up you will see Terminal prompt with a flashing cursor.

4. Type "wizard" and press enter

5. You will now be in a GUI that you can navigate with your mouse

6. A Termianl window will automatically appear within the GUI window 

7. It is at the Terminal prompt at point 6. where you enter the commands.

8. Then minimise the Terminal window

9. Click the icon in lower left that looks like a CD and a menu will pop up

10. Find Partimage and click it

11. Then follow the rest of my post #11

Hope that helps.

---

### Post by wizard10000 on 2009-08-21
Okay, so I'm gonna offer a different solution than everybody else  :D

I think partition imaging is overkill if all you're trying to do is save your settings.  Here's what I do for backup and restore - I posted this a week ago but am gonna inflict it on folks again  ;)

1.  Copy the contents of /home and /etc to an external drive.

2.  I get a list of all my installed packages like this -

```
dpkg --get-selections > package-list.txt
```

2a.  If you're not changing architecture you can also back up /var/cache/apt/archives so you don't have to download the packages over the internet.  If you're changing from 32-bit to 64-bit architecture or vice versa you can skip this step.

3.  Clean install the new version of Linux.  This time put /home on its own partition so you can do the next upgrade without blowing away your /home partition.

4.  You can restore your home directory but don't restore /etc - just keep it around for awhile so you can replace any configuration files for packages you install.

5a.  Get ready to reinstall your packages.  If you're not changing architectures then just restore your backup of /var/cache/apt/archives and run

```
sudo apt-get update
```

5b.  Reset your selections and reinstall packages like this

```
dpkg --set-selections < package-list.txt

sudo apt-get dselect-upgrade
```

All done  ;)

---

### Post by mapes12 on 2009-08-21
> **wizard10000 said:**
> Okay, so I'm gonna offer a different solution than everybody else  :D

I think partition imaging is overkill if all you're trying to do is save your settings.  Here's what I do for backup and restore - I posted this a week ago but am gonna inflict it on folks again  ;)

1.  Copy the contents of /home and /etc to an external drive.

2.  I get a list of all my installed packages like this -

```
dpkg --get-selections > package-list.txt
```

2a.  If you're not changing architecture you can also back up /var/cache/apt/archives so you don't have to download the packages over the internet.  If you're changing from 32-bit to 64-bit architecture or vice versa you can skip this step.

3.  Clean install the new version of Linux.  This time put /home on its own partition so you can do the next upgrade without blowing away your /home partition.

4.  You can restore your home directory but don't restore /etc - just keep it around for awhile so you can replace any configuration files for packages you install.

5a.  Get ready to reinstall your packages.  If you're not changing architectures then just restore your backup of /var/cache/apt/archives and run

```
sudo apt-get update
```

5b.  Reset your selections and reinstall packages like this

```
dpkg --set-selections < package-list.txt

sudo apt-get dselect-upgrade
```

All done  ;)Nice guide.

What do you do to make sure you get your Software Sources back the way they were from /etc/apt/sources.list or does one of those Terminal commands restore it from somewhere?

---

### Post by longtom on 2009-08-21
> **wizard10000 said:**
> Okay, so I'm gonna offer a different solution than everybody else  :D

I think partition imaging is overkill if all you're trying to do is save your settings.  Here's what I do for backup and restore - I posted this a week ago but am gonna inflict it on folks again  ;)

1.  Copy the contents of /home and /etc to an external drive.

2.  I get a list of all my installed packages like this -

```
dpkg --get-selections > package-list.txt
```

2a.  If you're not changing architecture you can also back up /var/cache/apt/archives so you don't have to download the packages over the internet.  If you're changing from 32-bit to 64-bit architecture or vice versa you can skip this step.

3.  Clean install the new version of Linux.  This time put /home on its own partition so you can do the next upgrade without blowing away your /home partition.

4.  You can restore your home directory but don't restore /etc - just keep it around for awhile so you can replace any configuration files for packages you install.

5a.  Get ready to reinstall your packages.  If you're not changing architectures then just restore your backup of /var/cache/apt/archives and run

```
sudo apt-get update
```

5b.  Reset your selections and reinstall packages like this

```
dpkg --set-selections < package-list.txt

sudo apt-get dselect-upgrade
```

All done  ;)

That is pretty clever and all...

But....

Most PCs I install on don't have access to the internet or dial-up only...

---

### Post by wizard10000 on 2009-08-21
> **mapes12 said:**
> Nice guide.

What do you do to make sure you get your Software Sources back the way they were from /etc/apt/sources.list or does one of those Terminal commands restore it from somewhere?

I wrote that for a distribution upgrade and you'd have a new sources.list but if you wanted to restore the old one you've got it since we backed up /etc  ;)

---

### Post by wizard10000 on 2009-08-21
> **longtom said:**
> That is pretty clever and all...

But....

Most PCs I install on don't have access to the internet or dial-up only...

That's why you back up the apt cache  :)

---

### Post by longtom on 2009-08-21
> **wizard10000 said:**
> That's why you back up the apt cache  :)

Didn't see that - you did think of that.  I bookmarked that page.  Thank you!:)

---

### Post by mapes12 on 2009-08-21
Here's another idea I've been working on. It's based on the infamous post by Heliode a while back but following other research I have changed it quite considerably.

The objective is to create a backup that can be quickly reinstalled to bring your system back to the way it was inc all the packages and updates installed. In other words I have 8.04 on this machine and the backup is intended to restore 8.04. It's not meant to be used as part of an upgrade migration

This method backs up all your important settings of the "/" file system and bundles everything up into a single, compressed tar file. I have two HDD's in my machine. One is sda and has Ubu installed. The other is sdb and is used purely for backups. They are both formatted with ext3. You should be able to adapt this to your own configuration.

When following this close down all applications except Terminal

It goes like this:

Terminal -
```
sudo mkdir /HDD2
```# creates a folder in the filesystem folder called HDD2

```
sudo mount /dev/sdb1 /HDD2
```# mounts the 2nd HDD Linux partition to the file system via the above directory

To create the tar file called **bkp-root.tgz** and store it on the second HDD -
```
sudo tar cvpzf /HDD2/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /
```# The first two excludes are so that we don't make a backup of /home. (That gets done using another method - Grsync). And we don't want to backup the second hard drive where we are making the backup to. The rest of the excludes get recreated when restoring.

At the end of the process you might get a message along the lines of 'tar: Error exit delayed from previous errors' or something, but in most cases you can just ignore that.


SYSTEM DAMAGE!!!!

Reinstall Ubuntu 8.04 from the CD

Then, to restore the system the way it was before it crashed, messed up, whatever:-

Terminal -
```
sudo mkdir /HDD2
```# creates a folder in the filesystem folder called HDD2 again

```
sudo mount /dev/sdb1 /HDD2
```# mounts the 2nd HDD Linux partition to the file system via the above directory again

```
sudo mv /HDD2/bkp-root.tgz /
```# The above will move the tarfile called **bkp-root.tar** from the second HDD back into the root file system

```
sudo tar xvpfz bkp-root.tgz -C /

```# Unpacks the tar file and restores your system to the way it was before it screwed up.

Restart the PC and you should be as your were.

---

### Post by longtom on 2009-08-21
That is quite neat as a safety backup.  Would work with a USB drive as well...hmmm...

But I wouldn't fancy it as a custom install.

---

### Post by cat2005 on 2009-08-22
> **sumeshgupta said:**
> You can make a Live CD of your Ubuntu Box which can be then carried around . It also has an option to install. The install will be with your configuration. Please check this out at :
[php]http://www.geekconnection.org/remastersys/capink.html
[/php]I have made one. Now I dont have to reconfigure my Ubuntu Box whenever I install in a new PC.:guitar:


My install has somehow become 4.3 GB.  Do you know how I could slim it down so I could fit it on 1 CD or DVD?

Thanks.

*UPDATE:  Ahhh....nevermind, it fits on a DVD.   *

---

### Post by cat2005 on 2009-08-22
mapes12, et all

I followed the steps given (post # 11), including the terminal instructions.

I found the image but it has an emblem next to it.  According to the "properties" menu, the emblem means "no read".   Is that ok?  Did I do something wrong?

Thanks again for your tutorial.  It was easy to follow!

---

### Post by cat2005 on 2009-08-24
> **mapes12 said:**
> 
 
". . .Type where the file name is one of your choice. (N.B. the filename will automatically have .000 after it so just be aware of that.) . . ." 
Mark
 
 
If I wanted to burn this .000 file to DVD, then would I burn it as a data file?  I changed ".000" to ".iso" and tried to burn it as an iso file but K3B stated "not an image file".  
 
What is its file type and how should I burn it?  The partimage webpage did not clarify this issue.
 
Thank you again.

---

### Post by deserthowler on 2009-08-25
I volunteer for a charity, World Care, in Tucson, AZ, USA.

I need a quick and easy way to install an operating system on computers we sell in our thrift store to raise operating funds.  Most of the computers are PIII or Celeron 1-1.2 GHZ with 384 MB memory.

I have a version of Ubuntu 8.04 set up with Cairo-doc, Google Gadgets, and Mozilla Prism installed.  I tried remastersys on a Dell Optiplex GX150 with 384 MB memory and a 1.2 GHz Celeron processor.

My first try resulted in a failed DVD.  For my second attempt I ran remastersys from the desktop using the applications menu.  I did a reboot and closed down cairo-dock and google gadgets and disconnected from the network.  I got a working Live DVD.  I didn't, however, get the desk top to boot up with dairo-dock and google gadgets running on the live DVD.  It seems I still have some experimenting to do but the live DVD did work on 3 computers with different hardware.

I have more work to do but I was able to recapture my desktop with very little work and no updates.  Not quite what I wanted but a good start.

Earl

---

### Post by mapes12 on 2009-08-25
> **cat2005 said:**
> If I wanted to burn this .000 file to DVD, then would I burn it as a data file?  I changed ".000" to ".iso" and tried to burn it as an iso file but K3B stated "not an image file".  
 
What is its file type and how should I burn it?  The partimage webpage did not clarify this issue.
 
Thank you again.Unlike windoze you can't just change an extension. The image file Partimage creates can't be burned as an iso. You have to burn it just as it is. 

To restore the image file you just load up the Systemrescue disc as in post #11 but select the option to restore then do all the rest the same including mounting the drive where the image is saved _to_. I've tested this at least half a dozen times now and it works for me.

---

### Post by cat2005 on 2009-08-25
> **deserthowler said:**
> I volunteer for a charity, World Care, in Tucson, AZ, USA.
 
I need a quick and easy way to install an operating system on computers we sell in our thrift store to raise operating funds. Most of the computers are PIII or Celeron 1-1.2 GHZ with 384 MB memory.
 
I have a version of Ubuntu 8.04 set up with Cairo-doc, Google Gadgets, and Mozilla Prism installed. I tried remastersys on a Dell Optiplex GX150 with 384 MB memory and a 1.2 GHz Celeron processor.
 
My first try resulted in a failed DVD. For my second attempt I ran remastersys from the desktop using the applications menu. I did a reboot and closed down cairo-dock and google gadgets and disconnected from the network. I got a working Live DVD. I didn't, however, get the desk top to boot up with dairo-dock and google gadgets running on the live DVD. It seems I still have some experimenting to do but the live DVD did work on 3 computers with different hardware.
 
I have more work to do but I was able to recapture my desktop with very little work and no updates. Not quite what I wanted but a good start.
 
Earl
 
 
You might want to try clonezilla or partimage.  I am not very experienced with linux and other advanced computer usage, but people always recommend those 2 programs.  So far, they work for me, though my needs seem less demanding than your needs.

---

### Post by cat2005 on 2009-08-25
[quote=mapes12;7842816]*Unlike windoze you can't just change an extension. The image file Partimage creates can't be burned as an iso. You have to burn it just as it is.* 
 quote]
 
Would you suggest I burn it as a simple "data" file?  If I can not burn it as an "iso" then "data" is the only other format of which I know.
 
How do you burn them?  
 
Thank you again.

---

### Post by deserthowler on 2009-08-27
> **deserthowler said:**
> I volunteer for a charity, World Care, in Tucson, AZ, USA.

I need a quick and easy way to install an operating system on computers we sell in our thrift store to raise operating funds.  Most of the computers are PIII or Celeron 1-1.2 GHZ with 384 MB memory.

I have a version of Ubuntu 8.04 set up with Cairo-doc, Google Gadgets, and Mozilla Prism installed.  I tried remastersys on a Dell Optiplex GX150 with 384 MB memory and a 1.2 GHz Celeron processor.

My first try resulted in a failed DVD.  For my second attempt I ran remastersys from the desktop using the applications menu.  I did a reboot and closed down cairo-dock and google gadgets and disconnected from the network.  I got a working Live DVD.  I didn't, however, get the desk top to boot up with dairo-dock and google gadgets running on the live DVD.  It seems I still have some experimenting to do but the live DVD did work on 3 computers with different hardware.

I have more work to do but I was able to recapture my desktop with very little work and no updates.  Not quite what I wanted but a good start.

Earl

My desktop installed completely as far as I can tell.  It found everything and worked fine.  All I needed to do was restart the network connection.

BTW, I couldn't get the network to boot at all from the live CD at first ... changed the network card.  It works.  I'm happy.

Earl

---

