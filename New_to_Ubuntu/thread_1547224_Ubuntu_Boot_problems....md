---
title: "Ubuntu Boot problems..."
date: 2010-08-06
forum: New to Ubuntu
---

### Post by McTwitch on 2010-08-06
I have an Ubuntu livedisk that I've been booting off of a relatively new DELL computer, with Windows Vista installed. But, yesterday when I tried to boot it, I got the screen:

         "GNU GRUB version 1.98-1ubuntu7
minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_"

The entire screen looks like a Terminal or Command Prompt. I tried the reboot command, but it simply brought this screen up again. I've used different USB ports, and even different cords, but all the same effect. So...is there anything that I can do?

---

### Post by ranch hand on 2010-08-06
Are you using a CD/DVD or a USB stick?  Is this 10.04 or something else?

---

### Post by McTwitch on 2010-08-06
It's a USB Portable Harddrive, 300 and some gigabytes, I can't remember how many. I don't believe that there was any partition constructed on it before installation.

---

### Post by ranch hand on 2010-08-06
Are your bios set to boot from a usb device?

I use a dual drive usb enclosure with 2 320Gb drives for my test platform.  I am on it now on 10.10-testing.

---

### Post by McTwitch on 2010-08-06
That they are. They are set to first boot from a usb device, and if not found, boot from the regular harddrive.

---

### Post by ranch hand on 2010-08-06
Ah, now we get to the question I hate to ask.  If you remove the usb drive (or turn it off) does your internal boot correctly?

---

### Post by McTwitch on 2010-08-06
Yep. Windows Vista works just fine, everything's there, just like it should be. The only thing that I'm having problems with is the Ubuntu Livedisk, which has my most important files on it. Please tell me there's something I can do.

---

### Post by ranch hand on 2010-08-06
Well that is a relief.  I am not real familiar with the LiveDisk stuff but I would suggest, real strongly, that you go into bios and turn off the internal drive with your MS install on it before doing a lot of fooling with grub.

After doing that it would be a good idea to use a Live CD and run;
```

sudo  fdisk -l

```
(that is a lower case L) so that I (or someone with more experience with the LiveDisk business) will know what we are dealing with.

Why, by the way, did you not install normally on your external?  Or will the fdisk data tell that story?

---

### Post by McTwitch on 2010-08-06
I might be the tech guy of the neighborhood...but there's a lot that you just said that I did not understand. I know how to do the command you said, but the turning off of stuff, and what not...kind of lost me. And it's because it's a family computer, not mine, otherwise I'd have just gone with Ubuntu all the way.

---

### Post by ranch hand on 2010-08-06
You do know how to get into bios so that is not a problem.  Somewhere in there should be an option to turn off or disable the internal drive(s).  I have 2 internals. for instance, and I can turn either off or both off for that matter.

I use the one that is sda if both are on as my main drive and sdb for distros that are stable but that I want to try out.  I also use them for storage of back up data and so forth.  I do not boot to it from the main drive.  If I want to play on there is turn the main drive off, no chance for corruption.

I can boot the external from that second drive and of coarse itself.  It is now seen by Linux as sda as the other drive is off.

Usually when I run my external both internals are off.  Again little chance for corruption.  The external is my test platform and test releases can be toxic.

You could run that command with the internal on.  It will do no harm.  It is just listing the partitions.

It would be nice though to be able to turn off that internal so that grub, due to a bug or operator error, does not mess with the MBR or the MS boot sector.

---

### Post by ranch hand on 2010-08-06
Did you make a persistent Live CD disk or are you just using the Live CD to run off of and store data on the external?

---

### Post by McTwitch on 2010-08-07
Right...if you would be kind enough to walk me through, well...everything, I'd be much obliged. After converting a drive to NTFS by accident, I try not to do things I'm not sure about.

---

### Post by McTwitch on 2010-08-07
And, the live disk is the external, as well as the operating system, etc. There's no CD.

---

### Post by ranch hand on 2010-08-07
OK, I have done my homework on your installation.  I think it would be good if you described how you installed it and where you got the directions.  I want to make sure that we are on the same page.  Was "casper-rw" involved in this process?

Did you check your bios to see if you can disable or turn off the internal HDD?

As this is your family computer I will not suggest opening the case (computer unplugged from wall) and just disconnecting the internal.  The sight of an opened computer and someone fishing around in it tends to freak some people out.

We really need to have the;
```

sudo fdisk -l

```
(lower case L) information.  You can get it running the Live CD.  If you have no CD and you are using 10.04 you can get an up to date version that must go on a DVD (RW is your friend) here;
[http://cdimage.ubuntu.com/lucid/daily-live/current/](http://cdimage.ubuntu.com/lucid/daily-live/current/)
If you have to use a CD get it here;
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
This needs to be burned as slow as possible to get a good image burn and needs to be done with a program that will burn an image.

I assume you have such a critter or you would have trouble installing in the first place.

As far as running the fdisk command you just go to Applications>Addessories>Terminal and copy paste the command from this post.  It will not do anything except give out put describing your partition table.  It will modify nothing.

I would be a little gun shy if I got an accidental format too.  This will not do that.

As far as the bios, as you are on a Dell you should hit f2 when the Dell logo screen is up to get in and scroll down to "drives", hit enter to open that catagory (I just did this on my Dell to get on my external test drive).  There should be several drives listed (maybe 4 HDDs).  If you have one internal (standard Dell set up) only one of them will be "ON" when you high light it.  Remember which one it is (write it down) so you can turn it back on when you are done with this fixing.  All you need to do is hit enter which will then allow you to use the arrow keys to change from On to Off.

Take a look with out doing anything and see if that is correct.  You may have slightly different bios than I do.

Also check to make sure that bios are set to boot in this order CD/DVD, USB, HDD.  If not change it to that.

Get your Live CD(DVD) and put it in your disk drive.  Reboot.  This would be the time to actually turn off the internal.  The CD should then boot and you can use it to get to your files for one thing and you can run the command from there too.

---

### Post by McTwitch on 2010-08-07
I talked to a friend of mine, and he said that all I had to do was manually boot Ubuntu from the Grub terminal that was open, which sounds insanely simpler. How would I do that?

---

### Post by ranch hand on 2010-08-07
Well, I would not know.  I do not know how you are set up.  You need, at minimum, the partition that is / (root) and the kernel version number and perhaps the uuid of the partition.

If you would tell me how the bugger was installed we would know a lot more.  If we had the results of  the fdisk command we would know more.  Maybe you know these things, I do not.

Depending on how it was installed it is possible that just turning off the internal HDD would get it in a bootable condition.  Your error could easily be from not reccognizing the drive.  If this was installed from another box with the internal shut down, or your box with the internal shut down, grub is looking for sda as the drive.  With the internal on, this is likely to be something like sdf.  This will not boot and is a simple fix if you have the info you need.

Turning on/off a drive is not a tough thing to do.  If it was I would not be doing it at least twice a day.

---

### Post by McTwitch on 2010-08-07
I had my friend install it for me, but the way I understand it is that he made the installer disk, then installed it Ubuntu onto the live disk. We then changed the boot order so that it would first scan for the USB device and boot off of that, and if that was not found, it would move to the actual Vista hard drive. If it's relevant, we used ROXIO for the burning.

---

### Post by ranch hand on 2010-08-07
Well that is some information at least.

I thought we had a communication problem and we do.  The "Live Disk" usually refers to the Live CD that is used for, among other things, installing the system.  What you are installed on is a HDD.

I assume that this was installed and that grub was then installed on the MBR of your external.  To do that it had to be installed without doing this during the install or with the internal turned off.  Other wise it would, by default have been installed on the MBR  of the internal and you would be booting Vista from the grub menu.  Or your friend pretty well knows his stuff and directed grub to be installed on the correct drive.

Did he tell you what drive he installed grub on?

Do you still have the "installation" disk?  If you do then you have a Live CD that must work or you would not have gotten an install.  Or he used the Alt Install CD which does not have a live session.

If you have it stick it in the CDrom and try it, see what comes up.  Should be an option to try Ubuntu.
This will not effect your box, it will boot to the Live CD and give you a complete desktop that is pretty slow but works fine.  This is what we need to find out how the thing is really installed.  The fdisk command would be a good place to start. 

You will have access to the net from the live cd and I will give you an address to directions on fixing your grub (you need the fdisk command for those directions too).

I think I have heard of that burning program, hopefully it is on your machine in case you do not have a live CD.  I am not familiar with it as I do not have MS on anything in this house (won't have).  This is why I am happy that your MS works, I really do not like to try fixing something where A>I do not know it well and B>can't try it on my box before sending it to you.

Get the Live CD and boot to it and report from there if you have access for a couple hours.  I will be in and out a bit but will check every time I am in (yard work needs doing and it is hot).  This really should be pretty easy to fix but we need the right information to do the job.  Be glad you are not installed on the same drive as Vista, that requires more information.

Assuming you have the Live CD (install disk), leave the internal HDD on and run the fdisk command.  Let us see what we have.

---

### Post by McTwitch on 2010-08-07
I hate to say it, I don't have the live disk, but I can get it, I just don't know when, I'll try right now. I tried the fdisk command on the screen that I described earlier, and I got the "error: unknown command 'sudo'.
I tried it without sudo, and got "error: unknown command 'fdisk-l'.

---

### Post by ranch hand on 2010-08-07
You are trying it on a grub command prompt.  This will not work as it is  bash command.

Just use the link I gave you for the "daily current" Live CD.  It should work the best.

I say that because I do ISO testing.  10.04 is a Long Term Service (LTS) release.  It therefore gets "point" releases through out its lifetime.  The first tries to cure all the bugs that were discovered after the release.  That release (10.04.1) was due out on the 29th of last month.  Postponed until the 19th of this month.  If you have kept your install up to date this should match it pretty well.

This is not the crappy install disk that MS provides.  This is a tool that is about as handy as a pocket in a shirt.  You do need a DVD for that.  The other link is just 10.04 and, if installed, would need a lot of upgrades but it fits on a CD.  RW really is a great idea for either of those.

We need to have it to run that command.  Then it will be simply a matter of following these directions;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
ignoring the ones about editing files as you do not need that.  You pretty much need the one command to install grub on the MBR.  We have to have precise info as to the disk designation from fdisk to do that.

I actually use a slightly different system for this but you are not set up the way I am and it would be a real pain.  Once set up it is easier but you should not need it again for a long time.  I run testing OS' and it gets used a good bit.  They are not supposed to run right and they don't all the time.  This current one is kind of boring as it does not break enough.

---

### Post by McTwitch on 2010-08-07
I don't have an RW. I doubt it, but will an R work? At this point I'm willing to try almost anything.

---

### Post by McTwitch on 2010-08-07
My friend says that he can fix it, but I'd have to wait until Monday. I'd rather do...whatever it is that I can, and hopefully fix it before then. I might be able to get an RW tomorrow.

---

### Post by ranch hand on 2010-08-07
Most certainly an R will work.  They are just not as useful and you are stuck with what you got.  With an RW if there is, for some reason, a bad burn you can redo it.  If you want to try, say Mandriva (nice RPM instead of Deb based Linux distro {RedHat off shoot like Ubuntu is from Debian}) you can burn their Live DVD (I do not think they use a CD at all anymore).

There is a Live DVD for Ubuntu too.  It has a great rescue broken systems mode.  You can rescue MS stuff with it.

You can also make your own OS or copy your OS (Debian based) using remastersys.  This is a great app that you can make up your system to be a rescue tool for any OS and then have it on a DVD or USB key and be a real live IT guy.

Basically, RW is cheaper in the long run when you really get into playing with Linux.

R will do fine.  If you do not have a DVD use the other link that will fit on the CD.  If you go to the wrong one you will know it as there is a red letter warning that it will not fit on the CD and that you do not have to report it as it is a known bug.

All you need to do is get the right one for your box (32 or 64 bit).  If you do not know use the 32 bit one, it will be fine on either type of box.  I  have a 64 bit box but install 32 bit stuff if there is no 64 bit version available.

Here is a link to one of the Stickies at the top of the ABT forum (this forum).  It is real good.  I think you would enjoy and benefit from it;
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I would recommend ALL the stickies on ABT and General Help, at least the first post of each.  You may even enjoy and learn a bit from the ones where I hang out most of the time;
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)
Those stickies are aimed at folks in testing, particularly those just starting.  We have to deal with stuff that is supposed to break.  These talk about what to do to minimise the breakage and what to do when it does (in our case it is not "if it does").  I highly recommend the one on Update Mangler.  I do not use it on stable releases (could be the root of your problem).

---

### Post by McTwitch on 2010-08-07
Okay, long story, but now I have an Ubuntu CD-RW, burnt and everything. Please tell me that the next part is simply change boot settings to boot off of it immediately, instead of the hard drives, then push my way into the Ubuntu External, and...do something?

---

### Post by McTwitch on 2010-08-07
Okay, on the live disk, at the link ([https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)), and I have done the fdisk command. How do I know which device is the one that I want? There is one for dell, two that say HPFS/NTFS, one that says Linux, one that says Linux Swap/Solaris, and finally one labeled Extended. Which is the one that I want?

---

### Post by ranch hand on 2010-08-07
Do not do anything.  Post the fdisk results here.  I will take a look at it in a few, have to run to the store (5 blocks).

Then we will do this.   Don't gitcher panties in a bunch as we like to say here.

---

### Post by McTwitch on 2010-08-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70811d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       38914   297169240    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e234

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38175   306633728   83  Linux
/dev/sdc2           38175       38914     5935105    5  Extended
/dev/sdc5           38175       38914     5935104   82  Linux swap / Solaris

Oddly enough, we say that here as well. Thanks for the help.

---

### Post by ranch hand on 2010-08-07
OK you are on sdc.  A 320 Gb drive too.  That is the size I have 4 of.  Really like it.  You can put 3 or 4 usable sized OS' on one or one main OS and a usable but small install of another version or distro.

So, I do not really like your partition table.  The extended partition is only your swap partition.  With only 2 partitions you hardly need an extended one.

You can only have 4 "primary partitions on a drive.  An extended partition is a type of primary partition that you can put many "logical" partitions inside of.  I have 13 partitions on the first drive in my external enclosure counting my swap partition, as an example, instead of only 4 under the original DOS rules.

I would have made one 20 to 25Gb primary at the beginning of the drive and formatted it to ext4 and used it for the / (root) partition, made the reat of the drive into one extended partition, put the swap at the end of that and formatted the rest ext4 for the /home partition.

You do not have a /home partition and they are real nice to have.  I learned that as a noob.  You screw your system and have to reinstall you can use the manual option on the installer and just format the / partition (backup still a good idea).  That way you have about a 99.9% probablility of coming out with a new install with all your data intact.

But, the partition you want to mount is sdc1 the * is a boot flag.

So you can use all the commands through the;
```

sudo chroot /mnt

```
just as they are in the directions.

Then skip the rest of that crap and;
```

grub-install /dev/sdc

```
Just copy/paste the commands from the directions and this last one.

Do not update-grub.

If this does not work we may need to be a bit more aggressive but I think this should do it.

Reboot and see what happens.  If you get a failure reboot to the Live CD.  Either way report as soon as possible.  I am a grumpy geezer and can't take the stress.

---

### Post by McTwitch on 2010-08-07
Everything was working, up until I used the "grub-install /dev/sdc". Then I got "cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied". I want to make sure the rest of what I was doing was right, so, the entire sequence was "ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ grub-install /dev/sdc
cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied"

---

### Post by ranch hand on 2010-08-07
Nope you left out that last command that I said you could use "through" meaning that you could use it.  Sorry for not being clear.

Would have been on quicker but ran a short errand and came back to discover my 10.10 Alpha3 had crashed.  Just got it back up.

If you run that;
```

sudo chroot /mnt

```
it will put you in as "root" or if you prefer "god".

Should work.

---

### Post by McTwitch on 2010-08-07
Installation complete, no error reported. Thanks for all of the help! Would you mind if I added you as a contact?

---

### Post by McTwitch on 2010-08-07
When I try to close the terminal, it tells me that there are processes still running, and that closing it would kill these processes. I've encountered this before, but since I wasn't doing anything important, I simply killed them. What should I do in this instance?

---

### Post by ranch hand on 2010-08-07
Try this
```

sudo umount /mnt

```
I am not sure that is the right command but I would just close the thing if it doesn't work.  What it is talking about is that you have chroot priviledges running.  When you reboot they will be gone.

I am sure you should unmount (umount is correct) but I am not sure if you have to do that to all of the stuff you mounted.  I never do.  I have 6 mounted right now in full chroot (internet connection included) so that I can update/upgrade with out leaving this OS.  When I reboot to go ch the 3 that get the upgrades to see if they still work (testing is FUN) they will be unmounted.  Been doing this for about 1.5 years twice a day.  Haven't screwed anything yet.

---

### Post by moxalactama on 2010-08-07
Saludos,

No puedo iniciar ubuntu, kubuntu o xubuntu en mi vieja toshiba satellite a10-sp177.

en días anteriores intenté instalar ubuntu y xubuntu 10.04 desde los live cds pero se estancaba al arrancar.

Creí que quizá era por ser un live cd aunque mi portátil tiene 768 MB de ram, así que instalé xubuntu 8.04 con el alternate cd y luego lo actualicé a 10.04 con otro alternate cd, pero obtengo el mismo problema.

Alguien puede decirme qué está mal?
Gracias...

NOTA: está en un arranque dual con windows 2000 pero el problema de arrancar lo tenía desde antes de instalar windows 2000.

---

### Post by ranch hand on 2010-08-07
> **moxalactama said:**
> Saludos,

No puedo iniciar ubuntu, kubuntu o xubuntu en mi vieja toshiba satellite a10-sp177.

en días anteriores intenté instalar ubuntu y xubuntu 10.04 desde los live cds pero se estancaba al arrancar.

Creí que quizá era por ser un live cd aunque mi portátil tiene 768 MB de ram, así que instalé xubuntu 8.04 con el alternate cd y luego lo actualicé a 10.04 con otro alternate cd, pero obtengo el mismo problema.

Alguien puede decirme qué está mal?
Gracias...

NOTA: está en un arranque dual con windows 2000 pero el problema de arrancar lo tenía desde antes de instalar windows 2000.
I could use a translator on that but I wouldn't trust it to be as good as your english.  Your English may not be real good but it is better than my Spanish (High Sdhool Spanish in 1968 and 1969.  I do not remember much).

---

### Post by McTwitch on 2010-08-07
I killed the processes without doing the umount command that you said, and when I tried to boot from the Ubuntu External drive...the GRUB screen appeared again...what did I do wrong?

---

### Post by ranch hand on 2010-08-07
McTwitch
If you want to have a full chroot handy when you need it you need ot boot to the LiveCD and go to System>Administration>Gparted Partition Editor and pull it up.

Right click on your sdc1 partition and if the option "unmount" is not greyed out click on it.  Right click again and choose "label" (you may be able to do this the first time).  Label the bugger Lounge-root.

You need to click on the apply arrow on the tool bar to finish this.  Don't let the data loss warning worry you.

When you are back on your install paste this to your Desktop or somewhere else that is handy for you.
```

#!/bin/sh

echo "Welcome to Lounge Lizard"

sudo mkdir /mnt/Lounge-root
sudo mount /dev/sdc1 /mnt/Lounge-root/
sudo mount -o bind /proc /mnt/Lounge-root/proc
sudo mount -o bind /dev /mnt/Lounge-root/dev
sudo mount -o bind /dev/pts /mnt/Lounge-root/dev/pts
sudo mount -o bind /sys /mnt/Lounge-root/sys
sudo cp /etc/resolv.conf /mnt/Lounge-root/etc/resolv.conf
sudo chroot /mnt/Lounge-root /bin/bash

```
I know that Ubuntu calls it Lucid Lynx.   I like Lounge Lizard better.

If you need to chroot in for some reason just copy that to the desktop of the Live Session, right click on it and go to Preferences>Permissions and chedk the box allowing it to be used as a program.

Double click on the document and you will get an option to run it in terminal.  Do that.  If it doesn;t work (bash is buggy in 10.04) just copy it one line at a time (the lines below the "echo") and hit enter after each one.

---

### Post by ranch hand on 2010-08-07
> **McTwitch said:**
> I killed the processes without doing the umount command that you said, and when I tried to boot from the Ubuntu External drive...the GRUB screen appeared again...what did I do wrong?
The same error screen?

---

### Post by McTwitch on 2010-08-07
Yep, the exact same.

---

### Post by ranch hand on 2010-08-07
Well, that sucks.

I hope you are on the Live CD.  Rerun the fdisk command and check to be sure the output still lists it as sdc.

Open the terminal and;
```

gksudo nautilus

```
This will open nautilus as root.

You will probably have to open nautilus normally (Places>Home Folder and pull up your install from the left panel to get it on the left panel in the root session of nautilus.

Go to /boot/grub and copy/paste here the grub.cfg file.

Go to /etc/default.grub and edit it to look like this;
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

```
Yours does not have the# probably so the menu is hidden.  This is a real pain.

Do not close the root nautilus I will have something for you to add to another file shortly.

---

### Post by McTwitch on 2010-08-07
copy paste the grub.cfg file? Where do I copy it from?

---

### Post by ranch hand on 2010-08-07
Ah.  Insufficient info again.  That will be in the file system in the boot directory.  The /boot/grub isthe path to where grub.cfg is. The right way to define your path is /boot/grub/grub.cfg.

Right click on the bugger and open with Gedit (may have the option "text editor" that is gedit).  Then you can copy paste to the post.

I can't do it here or the second one would not show up but on the line above where you are going to paste put a set of square brackets [ ].  Inside them put   code   .

On the line below your pasted stuff put another  [ ] with /code inside.  This a good way to shorten the post.

---

### Post by McTwitch on 2010-08-07
I'm finding a grubenv when I go through the file system, boot, and then grub.

---

### Post by ranch hand on 2010-08-07
When you finish that stuff.

Go to /etc/grub.d and double click on the 40_custom file.  You want to select "display".  This will open in gedit (you must use the root nautilus session).

Add this to that file;
```

echo "Adding Lounge on sdc1" >&2 
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Lounge 2 on sdc1" >&2 
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

```
Save the file.

chroot back in and run;
```

update-grub

```
and;
```

grub-mkconfig

```
That last one will out put the new grub.cfg file.  Post that out put.

I think the first entry should work.  If not try the second one.  Those are "symbolic" menu entries and should boot to the newest debian based kernel in the partition defined.  They should be at teh bottom of your menu on the screen.

You may want to read the grub link in my sig for an over view of grub so that you have a clue what is happening (just the first post).

If that does not work come back to the Live Session and get this script and run it.  Directions on the site.  This is a safe, much used, trusted script written by folks on these forums.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Wether you need it or not pass that on to your friend.  If he/she is not familiar with it he/she will like it.  Very nice piece of work for diagnosing boot problems.  Mine runs over 3000 lines but I have an insane number of installs.

Don't do anything until I have a chance to see the current grub.cfg.

---

### Post by McTwitch on 2010-08-07
Um...You kind of left me in the dust. I'm still back on the file.

---

### Post by ranch hand on 2010-08-07
Look at these in order.

---

### Post by ranch hand on 2010-08-07
I know that.  Just thought I would get it in while I had a moment to edit the buggers and post.  No intention of confusion just trying to use time well.

---

### Post by McTwitch on 2010-08-07
That's what I did, except all that I found in this folder is the grubenv.

---

### Post by McTwitch on 2010-08-07
I find a grub.cfg when I go through the file system on the external, is that what I was looking for? Sorry, I'm really new to the whole, digging around in the file system stuff.

---

### Post by ranch hand on 2010-08-07
Well that explains the problem.  This is a good thing.

Go back and click on that /boot/grub file (just grub not the boot directory) and delete the SOB. 

Do the gparted thing from;
[http://ubuntuforums.org/showpost.php?p=9691848&postcount=37](http://ubuntuforums.org/showpost.php?p=9691848&postcount=37)

I posted a chroot script there too but just use this one line at a time;
```

  sudo mkdir /mnt/Lounge-root
sudo mount /dev/sdc1 /mnt/Lounge-root/
sudo mount -o bind /proc /mnt/Lounge-root/proc
sudo mount -o bind /dev /mnt/Lounge-root/dev
sudo mount -o bind /dev/pts /mnt/Lounge-root/dev/pts
sudo mount -o bind /sys /mnt/Lounge-root/sys
sudo cp /etc/resolv.conf /mnt/Lounge-root/etc/resolv.conf
sudo chroot /mnt/Lounge-root /bin/bash

```
Hit enter after each line.

When you have the root prompt run;
```

apt-get purge grub-pc grub-common
[code]
then;
[code]
apt-get install grub-pc grub-common

```
This is where I would really like the internal HDD turned off.  You should get a screen asking where to install grub.  Space bar selects. sdc ONLY.


Use it the manual way, one line at a time star

---

### Post by ranch hand on 2010-08-07
Posted that by accident.  Sorry.

If you do not get that screen it will go on the internal and really screw things up.

You should alos be asked about the modified /etc/default/grub file.  Keep the one you have.

There will be a question about the command line in that same file with a blank input box.  Do not put any thing in there just hit enter and get past it.

---

### Post by McTwitch on 2010-08-07
Wait, delete the grub.cgf thinger?

---

### Post by ranch hand on 2010-08-07
I thought you said all you had was grubenv in the /boot/grub file.  Grub.cfg should be right next to it along with about 194 other files.

If all you have is that one, grub is corrupted and we will rip it out and then put it back.

We would have known this had I had you run the bot info script it the first place.  I am a moron.

---

### Post by McTwitch on 2010-08-07
On the portable hard drive I have all that, with the grubenv, I was just looking under filesystem. But when I looked at the external, I found the grub.cfg or what ever the label is for it, along with what would appear to be a hundred of audio files.

---

### Post by ranch hand on 2010-08-07
Ah, that is different.  Don't do that stuff.  It would be silly.  Post the grub.cfg file first and then just add the menu items to the 40_custom file, save it, chroot in however you want and run update-grub.

i hope you get the selection screen.  I think they fixed that bug.

Your friend had to do it that way so we will just hope for the best.  I just do not trust 10.04 as far as I can spit.

---

### Post by McTwitch on 2010-08-07
I'm sorry, but can you explain that a little bit more in depth?

---

### Post by ranch hand on 2010-08-07
Ok, too much conflicting data.

I will have a post for you in a little bit.  Bathroom break time.

---

### Post by McTwitch on 2010-08-07
Awesome, time for some food, take all the time you need, I've got all night.

---

### Post by ranch hand on 2010-08-07
First this stuff;
[http://ubuntuforums.org/showpost.php?p=9691868&postcount=40](http://ubuntuforums.org/showpost.php?p=9691868&postcount=40)

Then the stuff on the nest page (5) starting with 42 and then 44.

Making sure to post the current grub.cfg before running update-grub and grub-mkconfig.

Then post the grub-mkconfig out put so I can compare them.  We may want to modify some more before you try this out.

---

### Post by McTwitch on 2010-08-07
So...you want me to post the grub.cfg file? Here it is...

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


I hope that's what you wanted me to do.

---

### Post by McTwitch on 2010-08-07
And I changed the part of the code in the etc file to be 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

---

### Post by ranch hand on 2010-08-07
That is great.  Note that all the entries are for (hd1,1).  I do not think that is right.  (hdo,1) should be sda1.  (hd1.1) should be sdb1.  So I think that it really should be (hd2,1).

Your windows recovery partition is listed as (hdo,3).  I am concerned that there is not an entry for vista.  but it wouldn't boot from the sdc MBR anyway so we won't worry about that.

---

### Post by ranch hand on 2010-08-07
You really ought to learn to use the [ ] code and /code stuff before and after big posts like that cfg file.

Would then be in a box with elevators about 4 or 5 inches square.

---

### Post by McTwitch on 2010-08-07
Okay, I'll get on that, and so...what should I do?

---

### Post by ranch hand on 2010-08-07
[http://ubuntuforums.org/showpost.php?p=9691954&postcount=44](http://ubuntuforums.org/showpost.php?p=9691954&postcount=44)

When you finish that post the out put from grub-mkconfig (will be the grub.cfg file again).  Let me compare that to the last one before we reboot.

When you do anything in grub you have to run update grub for it to get written to the grub.cfg file.  That is the file that supplies the screen menu.

When you reboot I want you to use the entries I sent that are at the bottom of your menu.  Use the top one of them first and then the on labeled Lounge 2 only if the first doesn't work.

Notice that I do not have "ro quiet splash" on there.  The boot manager, plymouth, is buggy.  The graphics part of it is not good on a lot of hardware and it seems that it is getting worse.  Leaving "splash" off helps in some cases.  So you will, hopefully, have a black screen with some messages  and then the gdm if you use password login or your desk top if not.

---

### Post by McTwitch on 2010-08-07
I can't remember how to chroot, care to do a quick run through, or show me where it was? Thanks a million for going through all this trouble.

---

### Post by McTwitch on 2010-08-07
Alright, I chroot'ed, if that's a verb, and ran the "update-grub", but it says alot of things about failures, and what not. I didn't know whether or not you wanted me to post the results of that command.

---

### Post by McTwitch on 2010-08-07
Alright, I'm going to stop what I'm doing, and confess some stuff. I started mounting all the stuff on [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) again, and then chrooted in. Then I chrooted out, and started to mount them again, because I stopped half way through, and the thing that's screwing up is something that I hadn't mounted the second time, which was the proc stuff...but the third time I accidentally put sda1 instead of sdc1, then I tried to over ride this by instantly mounting sdc1. I realized that I should try to unmount sda1, just in case, but it said that sdc1 was mounted on a point right above it...and I'm afraid I might have screwed something up...

---

### Post by ranch hand on 2010-08-07
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

is what you are looking for.

I had a lot of folks help me when  I got here.  Take a long time to to pay that back to the community.

If you stick to using Ubuntu instead of that off brand on the internal, you will get to where you too will start feeling the need to pay it back.  I am pretty good at grub and partitioning.  My son (the youngster {in his 30s}) is on here occasionally Tunin.  It is his fault that I use Ubuntu.

Vista was one insult from MS too many.  I thank the good folks there in Redmond for that fine OS.  If not for it I would still be using some MS OS.

This is much more FUN.

---

### Post by ranch hand on 2010-08-07
> **McTwitch said:**
> Alright, I'm going to stop what I'm doing, and confess some stuff. I started mounting all the stuff on [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) again, and then chrooted in. Then I chrooted out, and started to mount them again, because I stopped half way through, and the thing that's screwing up is something that I hadn't mounted the second time, which was the proc stuff...but the third time I accidentally put sda1 instead of sdc1, then I tried to over ride this by instantly mounting sdc1. I realized that I should try to unmount sda1, just in case, but it said that sdc1 was mounted on a point right above it...and I'm afraid I might have screwed something up...
I doubt that you could screw up MS with these commands.  First off the things you were mounting, except the partition do not exist there.

I would, just to be safe, reboot and start over on the chroot.  As long as you just do it all again nothing should be screwed up.

On the other hand, I don't know how good you are at screwing up.  I will bet that I am better at it than you are.

---

### Post by McTwitch on 2010-08-07
With all of the help that you've given me, I already feel the need to pay it back.

---

### Post by McTwitch on 2010-08-07
Sorry for multiple posts like this, my though process is insanely odd. Anyway...if you think it's safe, I'll just go without the reboot, and keep going. The Livedisk takes forever to load.

---

### Post by McTwitch on 2010-08-07
Okay, I went through mounting everything again, this time I made sure to go through all of the steps. When I got to the update-grub part, I got this [root@ubuntu:/# update-grub
Generating grub.cfg ...
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
done]

---

### Post by ranch hand on 2010-08-07
Nah, let it build up for a while.  Get more adventurous in your destruction through ignorance.  it is a great way to learn if you have the stomach for it.  Break it, fix it.

Try that on MS.  Can't be down gracefully.  And it is not FUN at all.

I took up duel booting very fast, not with MS, but with Ubuntu.  I was running Hardy and broke it a lot.  Duel booted with Hardy.  Tried every thing on that second install first.  Update/upgrades.  New apps, stupid ideas, anything I came up with went on there  first.  Still have the Original Hardy install on here.  Still works.  That second one is gone but I have no idea how many times I absolutely ruined it before I got a little knowledge of what I was doing.

That beginners guide did not exist (or I didn't know about it) at the time.  It would have been nice to have.

---

### Post by McTwitch on 2010-08-07
Right, so...with the 


root@ubuntu:/# update-grub
Generating grub.cfg ...
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
done

output of update-grub, do you still want me to use grub-mkconfig?

---

### Post by ranch hand on 2010-08-07
Did you mount sdc1?

I think I would check that and maybe try it again.

---

### Post by McTwitch on 2010-08-07
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
mount: /dev/sdc1 already mounted or /mnt busy
mount: according to mtab, /dev/sdc1 is already mounted on /mnt

---

### Post by ranch hand on 2010-08-07
Good, go through them all, very carefully and rerun the command after you do the sudo chroot /mnt.

---

### Post by ranch hand on 2010-08-07
I have a few things to do.  Will be checking here every 15 to 20 minutes.

---

### Post by McTwitch on 2010-08-07
I did, and I still got the exact same thing. I mounted everything again, then chroot. It still says media/OS thing.

---

### Post by ranch hand on 2010-08-08
You might look in the /media directory of the Live CD.  All that stuff is supposed to be mounted in /mnt not /media.

If that doesn't tell you any thing and rebooting doesn't help you could use gparted to label your sdc1 and use the commands I gave you in some post.  You just want the sudo lines and use them one at a time bash is not quite right in 10.04 for some reason.  Works as a script in 9.04, 9.10 and 10.10 but not in 10.04.  The commands work one at a time in 10.04 just fine and that would just attack it from another angle.

You might also recheck fdisk to make sure the thing is still sdc.

---

### Post by McTwitch on 2010-08-08
Right, I did fdisk, it's still sdc1, I don't want to reboot, unless necessary, which I know could turn into a hindrance. So, could you explain how to do the gparted option?

---

### Post by McTwitch on 2010-08-08
Alright, never mind, I'm going to try to reboot.

---

### Post by McTwitch on 2010-08-08
Awesome, I rebooted, ran the mounting sequence again, and this time when I chrooted in, and did the update-grub I got "root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows Recovery Environment (loader) on /dev/sda3
done" I'm going to wait for the go ahead before I run grub-mkconfig

---

### Post by ranch hand on 2010-08-08
Sounds good, anytime  you want to run it.  Just don't try booting untill I check that.  There may be some thing else that we should do.

Probably think better in the morning.

---

### Post by McTwitch on 2010-08-08
Alright, good morning! I redid the mounting and everything this morning, just in case, did the update, install, etc. Chrooted in, did all that fun stuff. And then the grub-mkconfig. 

```
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Recovery Environment (loader) on /dev/sda3
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Lounge on sdc1" >&2
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Lounge 2 on sdc1" >&2
cat <<EOF
menuentry "Lounge on sdc1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF
### END /etc/grub.d/40_custom ###
done

```

---

### Post by McTwitch on 2010-08-08
Awaiting for your reply, but don't rush yourself.

---

### Post by QLee on 2010-08-08
Don't want to intrude here as I am well aware that too many cooks spoil the broth.
However, Ranch Hand, you failed to notice something from post 29:
[QUOTE=McTwitch...]I want to make sure the rest of what I was doing was right, so, the  entire sequence was
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/boot...[/QUOTE]

The second mount command means that the chroot you led him through isn't operating on the system as expected because the actual /boot from the installation is covered up. He somehow misinterpreted it to be as if there was a separate boot partition, which there doesn't appear to be on this system. 

No fault, no foul, as McTwitch still seems to be having fun and you can help him, now that you have the hint to where the procedure went wrong.

---

### Post by ranch hand on 2010-08-08
> **QLee said:**
> Don't want to intrude here as I am well aware that too many cooks spoil the broth.
However, Ranch Hand, you failed to notice something from post 29:


The second mount command means that the chroot you led him through isn't operating on the system as expected because the actual /boot from the installation is covered up. He somehow misinterpreted it to be as if there was a separate boot partition, which there doesn't appear to be on this system. 

No fault, no foul, as McTwitch still seems to be having fun and you can help him, now that you have the hint to where the procedure went wrong.
He got it straight later.

Thanks for pointing that out though, I surely did miss that.

---

### Post by McTwitch on 2010-08-08
I got it straight? I don't understand, I've been mounting it as sdc1 the entire time..

---

### Post by ranch hand on 2010-08-08
> **McTwitch said:**
> Awaiting for your reply, but don't rush yourself.
Just got back in and booted into the test platform.
If you are still chrooted in run;
```

grub-install /dev/sda

```
again.

I think you better go and have a look, as root, at /etc/grub.d/10_linux.  It is there as it gets mention in the grub.cfg, but there is no output there.  This is the script that looks for 
and generates the menu entry for the OS it is on (30_os-prober does the others).  Right click on the bugger and check to make sure that it is executable.

If it is or not try rebooting and try the first entry I sent.  If it does not work try the second.

Take note of any error messages.

I am still not convinced we do not have a corrupt grub installation.  The lack of 10_linux out put is not right at all.

---

### Post by QLee on 2010-08-08
[QUOTE=ranch hand]Thanks for pointing that out though, I surely did miss that.[/QUOTE]
No problem, when we all work together we have the power of ubuntu and that is awesome indeed.

---

### Post by McTwitch on 2010-08-08
do you want me to run it as sda then, or swap sda for sdc again?

---

### Post by ranch hand on 2010-08-08
> **McTwitch said:**
> do you want me to run it as sda then, or swap sda for sdc again?
Hell no.  Good thing you caught that, sdc it is.

---

### Post by McTwitch on 2010-08-08
"Installation finished. No error reported." Alright, so what now?

---

### Post by ranch hand on 2010-08-08
Try update-grub again and see if that 10_linux is doing anything.

Then I would reboot and see if it works.  Try the "Lounge" entry I sent first, then Lounge 2, and see if you have a generated menu entry and try it if it is there.

Watch the messages and make a note if you can.

---

### Post by McTwitch on 2010-08-08
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows Recovery Environment (loader) on /dev/sda3
done

---

### Post by McTwitch on 2010-08-08
I've got the 10_linux open, but I don't know what to look for, or what to do with it.

---

### Post by ranch hand on 2010-08-08
You do not need to open it all you need to do is right click on it in grub.d and choose Preferences>permissions (that is a tab) and make sure that the box is checked to make it executable. 

While you have it open, though, how about posting it so I can check it against mine.

---

### Post by McTwitch on 2010-08-08
Alright, it is executable (Thank God, it wasn't allowing me to change permissions). The contents of it follow.

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initrd.img-${alt_version}" \
       "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

---

### Post by McTwitch on 2010-08-08
Now do you want me to reboot?

---

### Post by ranch hand on 2010-08-08
You must not have been in as root or you would be able to do that.

If it is enabled, why are we not getting any action.  Run update-grub and grub-mkconfig again and post the grub-mkconfig output again.

Gotta go eat.

---

### Post by McTwitch on 2010-08-08
```
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Recovery Environment (loader) on /dev/sda3
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Lounge on sdc1" >&2
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Lounge 2 on sdc1" >&2
cat <<EOF
menuentry "Lounge on sdc1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF
### END /etc/grub.d/40_custom ###
done
root@ubuntu:/# grub-install /dev/sdc
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows Recovery Environment (loader) on /dev/sda3
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows Recovery Environment (loader) on /dev/sda3
done
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows Recovery Environment (loader) on /dev/sda3
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 4028b7c928b7bbea
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Lounge on sdc1" >&2
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Lounge 2 on sdc1" >&2
cat <<EOF
menuentry "Lounge on sdc1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF
### END /etc/grub.d/40_custom ###
done

```

Still think that it's a corrupted grub?

---

### Post by ranch hand on 2010-08-08
Well I do not know.  I do know that sometimes the commands work when used in the OS but not from outside.

Lets try to boot the sucker.  With the entries you have.  If they do not work we can try the old generated ones in the 40_custom file.  They are in this thread and in a file on my desktop.

---

### Post by ranch hand on 2010-08-08
I need to log out for a few so that I can get at a 10.04 10-linux file.  Be right back.

---

### Post by McTwitch on 2010-08-08
Alright, take your time. I rebooted again, without the livedisk, and with the external plugged in, but I got the same GRUB screen.

---

### Post by ranch hand on 2010-08-08
This is not good.

We know that /etc/grub.d/10_linux does not work.  Not sure why.  I do have the 2 files, yours and one from a 10.04 install of mine.

Took a while.  10.04 just does not work well on my box at all as far as booting and shutting down.  Plymouth sucks.

I am going to take a look at it.  Be back in a few.

---

### Post by McTwitch on 2010-08-08
alright, take your time.

---

### Post by ranch hand on 2010-08-08
I see no difference in the files at all.  So, why doesn't yours do its job?

Did you try all three of those entries?  Were the results exactly the same if you did?

---

### Post by McTwitch on 2010-08-08
All three of what entries? All I did was turn off the entire system, taking the Live Disk out, plugged in the USB, and turned it back on. Because of the boot order, it should have booted off that, right? Unless I'm not understanding something, the screen asking me of this choice doesn't exist...at least not yet.

---

### Post by ranch hand on 2010-08-08
Now hold on.

Your external was plugged while we were doing these things right?

---

### Post by McTwitch on 2010-08-08
Yessir. I should have explained that a bit more...I simply shutdown, took out the disk, then turned the system back on. The USB was plugged in the entire time.

---

### Post by ranch hand on 2010-08-08
OK, that is good to know.  It is also kind of a drag.

You got no menu in view when you rebooted, just the message screen, is that correct?

---

### Post by McTwitch on 2010-08-08
Correct. Just that message, just ask if you need a repeat, and then the "Grub>_" Input thinger.

---

### Post by ranch hand on 2010-08-08
I do not like it.  Not at all.

I have gotten that message a few time and have never really used the prompt there as chrooting in and reinstalling grub on the MBR has always fixed the problem.  There fore I assume the command prompt does the same thing.

I could well be wrong on that  because I have never fooled with it.

I do not want to reinstall grub, at least not the version you are using.  Why?

I just went to my second internal drive to retrieve the 10_linux file.  It has been a while since the last time I was on that drive, let alone 10.04.  I went to 9.10 to install that grub on the MBR as it has the menu for this drive too.  Installed grub from there on the MBR and corrected the out of date menu for this drive.

Went to 10.04 using that menu and ran apt-get update and apt-get upgrade.  Needed a bunch of stuff so I ran it.  Grub-pc and grub-common were upgraded.  Never got a screen asking were to install it at all.  Finished the upgrade and sent the file here and rebooted.

To use that menu I must hit F12 and sellect the internal sata drive instead of the usb device.  I do that and the 10.04 menu comes up as it installed itself on sda where I had just installed the 9.10 menu.

Let me go do some research on the command/grub-rescue prompt.  I will be back soon.

---

### Post by McTwitch on 2010-08-08
Um...alright. I am willing to format the External, and just reinstall, though that is the last option.

---

### Post by McTwitch on 2010-08-08
Have to go make a run with the family. Be back in at least an hour, probably more.

---

### Post by ranch hand on 2010-08-08
That is not needed.  Reinstalling grub may be though.  One thing you could do is go to bios and see what it takes to turn off that internal.  It should be as simple as just switching on to off.

I would try it and then hit exit and you will get options to stay in setup, exit and save, exirt without saving.  Just use that last one.

I think you were luckier than you know not to install grub on the MBR of sda (like some clown on this thread tried to get you to do).

Another thing you could do is look at subject number 15 on the first post of this thread;
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I do not think there is anything there that will help us.  It does look like you can reinstall grub pretty easily on the MBR using  "set root=(hdx,y) where x is the drive and y the partition that is supplying the menu.

This does not seem to be the problem here.

That is a good thread to know about, that first post and the links at the bottom of it are the best documentation you will find on grub2.  drs305 really did it up right with all the things we all came up with in 9.10 testing and his own, intense, experimenting (and from the foundation laid down by herman of coarse).

---

### Post by ranch hand on 2010-08-08
> **McTwitch said:**
> Have to go make a run with the family. Be back in at least an hour, probably more.
Glad you are gone you little bugger.  Gives me a chance to think and do some stuff here too.

---

### Post by QLee on 2010-08-08
[QUOTE=ranch hand]
...
I have gotten that message a few time and have never really used the prompt there as chrooting in and reinstalling grub on the MBR has always fixed the problem.  There fore I assume the command prompt does the same thing.
...[/QUOTE]

Don't forget Ranch Hand, he had that incorrect mount when he chrooted, the second mount (mount /dev/sdc1 /mnt/boot) that mounted his ubuntu partition again over top of the actual /boot of his system. That's what I meant with my previous reply.

Maybe you should lead him again through the chroot.

---

### Post by QLee on 2010-08-08
[QUOTE=ranch hand]
...
I think you were luckier than you know not to install grub on the MBR of sda (like some clown on this thread tried to get you to do).
[/QUOTE]

I'm trying to figure out if I am the "clown" to whom you are referring as there are only three of us participating in this thread, you me and McTwitch, other than the one in Spanish that you didn't understand. The thing is, I never suggested installing to sda, in fact I never stated any advice except to inform you that you had missed a detail from one of McTwitch's posts.

So, huh, eh?

---

### Post by yetiman64 on 2010-08-08
> I'm trying to figure out if I am the "clown" to whom you are referring  as there are only three of us participating in this thread, you me and  McTwitch, other than the one in Spanish that you didn't understand. The  thing is, I never suggested installing to sda, in fact I never stated  any advice except to inform you that you had missed a detail from one of  McTwitch's posts.

So, huh, eh?@ QLee, check out the code in post 91 by ranch hand and the replies in posts 93 by McTwitch and 94 by ranch hand.
I'm pretty sure ranch hand is actually having a go at himself there, for giving the wrong code earlier and not at you. Hope this helps. yetiman64 (been watching the thread for a while and have read it all ;))

Edit: on page 10

---

### Post by ranch hand on 2010-08-08
> **QLee said:**
> Don't forget Ranch Hand, he had that incorrect mount when he chrooted, the second mount (mount /dev/sdc1 /mnt/boot) that mounted his ubuntu partition again over top of the actual /boot of his system. That's what I meant with my previous reply.

Maybe you should lead him again through the chroot.
I believe we will.

---

### Post by ranch hand on 2010-08-08
> **yetiman64 said:**
> @ QLee, check out the code in post 91 by ranch hand and the replies in posts 93 by McTwitch and 94 by ranch hand.
I'm pretty sure ranch hand is actually having a go at himself there, for giving the wrong code earlier and not at you. Hope this helps. yetiman64 (been watching the thread for a while and have read it all ;))

Edit: on page 10
I am, indeed, that clown.  I told him, this morning to run grub-install and listed sda as where to put it.

Luckily he did not do that.  He asked if it was right.  Good thing.

---

### Post by QLee on 2010-08-08
@yetiman64 

Well, we had a bit of time to play as the OP was away for an extended period. I've joked with Ranch Hand before, during the testing phase of 10.04, he always likes to test the release alphas and betas. 

Now I know you're lurking I'll clean up my act!

---

### Post by ranch hand on 2010-08-08
I have just been experimenting with 10.04 and grub.  I really think his grub is toast.

We are going to have one more whack at it though with a different chroot all together.  If that doesn't do it for him we will install 20100722-1ubuntu1 (current in 10.10).  I looked up the package and it is a much improved version.  Along with a purge of his current grub this should fix him up.

---

### Post by McTwitch on 2010-08-08
I read through all of the stuff that was posted while I was gone, and...yeah, I barely followed any of it. So, slow down please? And what's up next on the agenda?

---

### Post by McTwitch on 2010-08-08
If at all possible, I'd like to get this done tonight, because my friend is supposed to come by tomorrow to try and fix it, and I'd like to impress him with having done it without his help. Which, by the way, the help of all three of you is better than his.

---

### Post by ranch hand on 2010-08-08
Go to System>Administration>Gparted Partition Editor and pull it up.

Right click on your sdc1 partition and if the option "unmount" is not greyed out click on it.
Right click again and choose "label" (you may be able to do this the first time).
Label the bugger Lounge-root.

You need to click on the apply arrow on the tool bar to finish this. Don't let the data loss warning worry you.

Use the lined bellow, one at a time in terminal

```

sudo mkdir /mnt/Lounge-root
sudo mount /dev/sdc1 /mnt/Lounge-root/
sudo mount -o bind /proc /mnt/Lounge-root/proc
sudo mount -o bind /dev /mnt/Lounge-root/dev
sudo mount -o bind /dev/pts /mnt/Lounge-root/dev/pts
sudo mount -o bind /sys /mnt/Lounge-root/sys
sudo cp /etc/resolv.conf /mnt/Lounge-root/etc/resolv.conf
sudo chroot /mnt/Lounge-root /bin/bash

```

Run, in this order
```

update-grub

```
```

grub-mkconfig

```
```

grub-install /dev/sdc

```
Reboot to the external and see what happens.  You should get a menu.  The first generated entry should work if it is there.
The Lounge menu entry that I sent for your 40_custom file should work.
If it does not the Lounge 2 entry should.
If it is showing the menu try all of those.

If you can boot, post from there, share the joy.

If you just get the same old crap, boot back to the Live CD.
Pull up the terminal and use this chroot list of commands again.

Open another terminal and run;
```

gksudo nautilus

```

Report when ready and we will nuke the sucker.

---

### Post by McTwitch on 2010-08-08
My SDC isn't showing up in GPARTED.

---

### Post by McTwitch on 2010-08-08
Nevermind. Found it.

---

### Post by McTwitch on 2010-08-08
I got up to the update-grub again.

```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
done

```

---

### Post by ranch hand on 2010-08-08
It is going to have trouble doing that here to.  I do not have such a file but I can update-grub.

So what does grub-mkconfig come up with?

---

### Post by McTwitch on 2010-08-08
grub-mkconfig:

```
root@ubuntu:/# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=132d26d5-9531-4f5b-a04c-5dd1f6e5db93 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 132d26d5-9531-4f5b-a04c-5dd1f6e5db93
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Adding Lounge on sdc1" >&2
cat << EOF
menuentry "Lounge on sdc1" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Lounge 2 on sdc1" >&2
cat <<EOF
menuentry "Lounge on sdc1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet
        initrd /initrd.img
}
EOF
### END /etc/grub.d/40_custom ###
done

```

---

### Post by ranch hand on 2010-08-08
So, the /media/OS stuff is coming from 30_os-prober.  Interesting.

Do you still have gparted open?  If so close it and try both commands again.  If it is not open let us know.

---

### Post by McTwitch on 2010-08-08
It was open. I ran update-grub, and received:

```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
ls: cannot access /media/OS: No such file or directory
done

```

do you want the results of the second mkconfig?

---

### Post by ranch hand on 2010-08-08
Nope  I am tired of this all together.

Try this stuff.  Take your time and report any problems before going on.  If no problems just finish it out and we will go from there.

I have tried this on an install of 10.04 here to be sure it is OK.  This is a better version 
but has not been backported to 10.04.

I have a couple 9.10 installs that run this version too.

In root nautilus go to /etc/apt/sources list.  Right click on it and open with text editor.

About line 5 you will find some thing like this what we want is the "main restricted parts there;
```

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted

``````

change that last part to look like this;
deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted

```Go to your chroot terminal and run;
```

apt-get update

```
```

apt-get install grub-pc grub-common

```It will claim it is updating grub which is exactly right.  Do not install anything else.

You should get a screen on where you can say where to install it.

Arrow keys to get to sdc.

Space bar to mark.

There will be some other questions, just keep what you have in answer to them.

When it is finished, run;
```

grub-mkconfig

```Post it.
Go back to root nautilus and change that maverick back to lucid and run;
```

apt-get update

```

---

### Post by McTwitch on 2010-08-08
alright, and how do I go about the root nautilus again? Sorry.

---

### Post by ranch hand on 2010-08-08
Whoa up there.

There is a typo.

I am editing the post so that the first command is correct.

---

### Post by ranch hand on 2010-08-08
That is better, try it now.

---

### Post by McTwitch on 2010-08-08
I still don't remember how to get into nautilus though. I'm feel stupid because of it, but I guess I'll learn.

---

### Post by ranch hand on 2010-08-08
You need to open a terminal and;
```

gksudo nautilus

```

---

### Post by McTwitch on 2010-08-08
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted

there's my first five lines. 2 and 3 look closer to the one that you posted than 5 does.

---

### Post by ranch hand on 2010-08-08
You are looking in the Live CDs sources.list.

If your installed OS is on in the left panel open the regular nautilus also and click on your install there (Places>Home Folder).  Then go back to the root nautilus and it should be there too.

---

### Post by McTwitch on 2010-08-08
I'm sorry, I know I sound like a noob saying this...and in fact I am, but, if you could, go a little slower?

---

### Post by ranch hand on 2010-08-08
Go to Places and click on Home Folder.  Your installed OS should show up in the left panel.  Click on it and it will open.

Then go back to the root nautilus and it ought to be in the left panel there too.

---

### Post by McTwitch on 2010-08-08
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

That's what I'm looking for then?

---

### Post by ranch hand on 2010-08-08
Yup that is the one.  Change lucid to maverick.  Save the file.

---

### Post by McTwitch on 2010-08-08
What about this one?

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

or the myriad of other places that lucid appears?

---

### Post by McTwitch on 2010-08-08
And I save and exit the file when done, correct?

---

### Post by ranch hand on 2010-08-08
Save it.  You can leave it open as we need to change it back shortly.

---

### Post by McTwitch on 2010-08-08
Alright, I closed the chrooted window, and when trying to chroot back in, I get 
```
ubuntu@ubuntu:~$ sudo chroot /mnt/Lounge-root /bin/bash
chroot: cannot run command `/bin/bash': No such file or directory

```

Do I have to go through that entire process again?

---

### Post by ranch hand on 2010-08-08
You had better try it again.  Do not close these things.

If you look in the lower left corner of you screen there are some boxes (2 or 4, not sure on the 10.04 Live CD).  If  you right click on that you can have as many as you want.  Nice clean work stations you can have one or two things on.

Makes life easier.

---

### Post by McTwitch on 2010-08-08
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/Lounge-root/proc
mount: special device /dev/sdc1 does not exist

I think I literally screwed something over.

---

### Post by ranch hand on 2010-08-08
I think you need to reboot and start over.

If the file saved then you do not need to do that part.  But we need to be chrooted in  to do anything.

This chroot has more commands to get you there because you can screw with more stuff and have a net connection which we need.

---

### Post by McTwitch on 2010-08-08
Alright, be right back then. I'm saving links in this post that I need. 

[http://ubuntuforums.org/showpost.php?p=9695452&postcount=129](http://ubuntuforums.org/showpost.php?p=9695452&postcount=129)
[http://ubuntuforums.org/showpost.php?p=9695555&postcount=137](http://ubuntuforums.org/showpost.php?p=9695555&postcount=137)

I'll be right on this.

---

### Post by McTwitch on 2010-08-08
Right, I ran through everything, including the update-grub. This time, I got something different.
```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda3
done

```

---

### Post by McTwitch on 2010-08-08
Alright, moved onto the apt-get update, that seems to be working.

---

### Post by ranch hand on 2010-08-08
That is an improvement.  How about the grub-mkconfig output?

---

### Post by McTwitch on 2010-08-08
This was at the end of the apt-get update, though.

```
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

---

### Post by ranch hand on 2010-08-08
Couldn't care less.  It would be good to get the key but it does not have anything to do with the job here.

While getting that would not hurt anything I do not want to be using apt to get anything but grub before we change it back to the right repository.

Just run;
[code]
apt-get install grub-pc grub-common
[[code]
It should say that it is wanting to upgrade those 2 packages.

---

### Post by McTwitch on 2010-08-08
Um..the entire thing changed, this is what it looks like now.

```
Package configuration


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; A new version of configuration file /etc/default/grub is available, but   &#9474; 
 &#9474; the version installed currently has been locally modified.                &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; What do you want to do about modified configuration file grub?            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;        install the package maintainer's version                           &#9474; 
 &#9474;        keep the local version currently installed                         &#9474; 
 &#9474;        show the differences between the versions                          &#9474; 
 &#9474;        show a side-by-side difference between the versions                &#9474; 
 &#9474;        show a 3-way difference between available versions                 &#9474; 
 &#9474;        do a 3-way merge between available versions (experimental)         &#9474; 
 &#9474;        start a new shell to examine the situation                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>  
``` It would appear that I should go with the second choice.

---

### Post by ranch hand on 2010-08-08
That should be the default.  Just stick with what you have on any of them.  I sure hope you get the choice of where it installs.

---

### Post by ranch hand on 2010-08-08
keep it

---

### Post by McTwitch on 2010-08-08
alright, the one it started on was  "Keep the local version currently installed" Do I hit space or enter?

---

### Post by ranch hand on 2010-08-08
enter

---

### Post by McTwitch on 2010-08-08
Awesome. What now?

---

### Post by ranch hand on 2010-08-08
Did you get a screen asking where you want it installed?

---

### Post by McTwitch on 2010-08-08
Other than what I showed you, I hit enter, and it seemed to do it all by itself.

---

### Post by ranch hand on 2010-08-08
Well I hope that Vista has a way to boot.  We may be lucky.

If the install window did come up and you hit enter it would not have installed anywhere.  That would be fine as it would leave sda alone.

You better run;
```

grub-install /dev.sdc

```
to be on the safe side so that something will boot.

---

### Post by McTwitch on 2010-08-08
```
root@ubuntu:/# grub-install /dev.sdc
/usr/sbin/grub-probe: error: cannot stat `/dev.sdc'.
```

---

### Post by ranch hand on 2010-08-08
Of coarse not.  I not only can't type, I can't see after I type.

Try /dev/sdc

---

### Post by McTwitch on 2010-08-08
Don't worry about it, we all have moments like that. This one worked, thanks. So, what now, good sir?

---

### Post by ranch hand on 2010-08-08
Now we really need to get back to that /etc/apt/sources.list file and change maverick back to lucid.  This will stop you from ruining your OS by have a mix of packages that do not work together at all.

You need to be root on nautilus to get there and do that.

---

### Post by McTwitch on 2010-08-08
Done. I want to take the moment to thank you for all of the work that you put into helping me.

---

### Post by ranch hand on 2010-08-08
You are welcome but let us see if it works.

First you need to run;
```

update-grub

```
again.  This updates the package list for your box.  That is an update.  Upgrade installs programs that have changed for your box.  You need a new update so that you are not trying to upgrade to 10.10 packages (things like kernels and such).

When that has worked it is time to see if the bugger boots.

---

### Post by McTwitch on 2010-08-08
Thank you so much, good sir. I am reporting this from the comfort of my little black box. I didn't get a chance to use the Lounge options, my head was turned when that screen came up. What do I need to do on them?

---

### Post by ranch hand on 2010-08-08
Well, that is good.  You really need to try and boot Vista.  I am a little nervous about that.

When you come back from doing and the menu comes up hit  e  that will let you see the menu entry.  Note the partition defined (hd?,1).
Hit escape.
Go down to those entries and hit e on each one.  If one matchs the partition definition hit escap and then hit enter and see if it works.

---

### Post by McTwitch on 2010-08-08
A little more in depth, please?

---

### Post by ranch hand on 2010-08-08
Just try booting to Vista and come back and let us know if we still have access there.

---

### Post by McTwitch on 2010-08-08
Alright, I am now reporting to you from a joke. It had to revert to a restore point, but that's it. Everything else seems to be working just fine.

---

### Post by ranch hand on 2010-08-08
Well,  I don't think that we had anything to do with that.  You have no idea how happy that makes me, a feller that will not allow MS products to pollute our house.  This is just great.

When you get back on Ubuntu let me know and we will get you the public key for medibuntu.  That is the repo for things that are not able to be included in the Ubuntu repos due to restrictive licensing or legal problems in some countries, etc.  The key verifies that they are from there.  Easy to install.

---

### Post by McTwitch on 2010-08-08
Alright, back on the highly customized home field Ranch. What now? And I have a problem for next weekend, if your game.

---

### Post by McTwitch on 2010-08-08
Actually I have one for right now, if you're ready for it.

---

### Post by ranch hand on 2010-08-08
Lets finish this first.

Open a terminal.  If you go to the menu with the terminal in it and right click on the terminal entry you have the option of putting a launcher on your panel.  You can move it where you wnat it after it is up there.  Kind of handy for apps you use a lot (I like the terminal to be handy).

Run this:
```

wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add -

```

---

### Post by McTwitch on 2010-08-08
```
steve@steve-desktop:~$ wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -0- | sudo apt-key add -
[sudo] password for steve: wget: invalid option -- '0'

gpg: no valid OpenPGP data found.
steve@steve-desktop:~$ 


```

what did I do wrong?

---

### Post by McTwitch on 2010-08-08
Never mind, I see it.

---

### Post by McTwitch on 2010-08-08
Alright, what I thought I saw didn't change anything, so...what happened?

---

### Post by ranch hand on 2010-08-08
Did it say OK?  If so you now have the key.  If not anytime you try to get something fro mthat repo you will have to approve getting things from an untrusted source.  Kind of like downloading things for MS.

I suspect you now have the key.

What is your other problem?

---

### Post by McTwitch on 2010-08-08
My MSN chat, "KMESS" isn't allowing me to use it. It will load, sign me in, and bring up my contact list, but it will not allow me to IM anyone. Care to help? This is not the weekend problem.

---

### Post by KROwen1959 on 2010-08-08
My hat off to you Ranch Hand. You have a great deal of patience. I am a newbie and I have been following you 2 for the last day. I have mine on disk and partitioned off my hard drive. Mine is a 64 bit and the only issue I had was Java and Adobe. Java is solved and no hope for adobe on 64 bit. I do have 1 thing I can't seem to find in any threads. In terminal it would ask me for my password and when I typed it in everything worked fine, 1 time it ask for root password and my passwod was rejected. Why

---

### Post by ranch hand on 2010-08-08
> **McTwitch said:**
> My MSN chat, "KMESS" isn't allowing me to use it. It will load, sign me in, and bring up my contact list, but it will not allow me to IM anyone. Care to help? This is not the weekend problem.
I have t orun to the store, be right back.

---

### Post by ranch hand on 2010-08-08
I am back.  Got some beer to celebrate with.  Kidding, did need beer bread bacon milk (the perfect food for mammals).  Store is now closed so I had to get there pretty quick.

Have you tried signing in trough "pidgin"?
```

sudo apt-get install pidgin

```
I really know nothing about chat.  I do get on some freenode irc channels but that is all xchat.

Probably a new thread in ABT would get more answers than you could ever use.

Send me a PM on the weekend thing.

---

### Post by ranch hand on 2010-08-08
> **KROwen1959 said:**
> My hat off to you Ranch Hand. You have a great deal of patience. I am a newbie and I have been following you 2 for the last day. I have mine on disk and partitioned off my hard drive. Mine is a 64 bit and the only issue I had was Java and Adobe. Java is solved and no hope for adobe on 64 bit. I do have 1 thing I can't seem to find in any threads. In terminal it would ask me for my password and when I typed it in everything worked fine, 1 time it ask for root password and my passwod was rejected. Why
A new thread for a new topic is a good thing.  Makes it so you can use the forum search function to find posts on your problem possible.

I would say check your pass word settings  maybe System>preferences>encryption and keyrings or System>Administration>Users and Groups.

I have never had this problem but Debian does use a root password separate from the normal password so it should be easy to get things screwed up here to require it too.  Wonder why I haven't had that?  I am good at screwing things up.

I would post that on this forum or over in General Help.  Someone know all about it I am sure.  Be sure to try the Search this Forum tool first.  i have had luck finding things on the forums with a search engine search on a subject too.

I am on a 64 bit system too.  Love it.

---

### Post by QLee on 2010-08-09
[QUOTE=ranch hand]A new thread for a new topic is a good thing....[/QUOTE]

+1

[QUOTE=ranch hand]...Be sure to try the Search this Forum tool first.  i have had luck finding things on the forums with a search engine search on a subject too.[/QUOTE]

+1

Excellent advice and often the way to get the help one needs in the fastest way.

---

