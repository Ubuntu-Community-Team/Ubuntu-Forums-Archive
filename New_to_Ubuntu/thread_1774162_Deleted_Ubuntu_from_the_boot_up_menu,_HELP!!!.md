---
title: "Deleted Ubuntu from the boot up menu, HELP!!!"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by BlackoutWorm on 2011-06-02
Hey. I am new to linux. I dual boot windows and ubuntu.
The guy who introduced me to this told me about this great software called ubuntu-tweak. I used it to clean up some stuff, and that's probably wherei t went wrong.
When i restarted the pc, I only have "memory test" and "windows 7" on that list ubuntu made for me.
I don't think I have removed ubuntu, since that list is still there.
But I have for some reason removed the ubuntu and the recovery mode links for there.
Can I fix this from the cd or from Windows?
Thanks in advance.

---

### Post by wolfen69 on 2011-06-02
You will need a live cd for this. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jramshu on 2011-06-03
You can reinstall grub from the live cd using terminal. I used Method 3 on mine.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You should also say what version you are running.

---

### Post by BlackoutWorm on 2011-06-03
yes I have the cd. ok so what do I do ?
I am in the live cd now.
I use version 10
Also I didn't understand any of that guide. Sorry, I am new to this.
Now when I'm using the CD, are there any restore method I can use or anything like that?
Or have I simply used a program I shouldn't use, and messed it all up?
The guy who recommended me the program said it was a great tool to clean up files I don't need in the system.

---

### Post by jtarin on 2011-06-03
> **BlackoutWorm said:**
> 
The guy who recommended me the program said it was a great tool to clean up files I don't need in the system.Tell that guy to fix your system.
What don't you understand about the instructions on that page?

---

### Post by jramshu on 2011-06-03
I haven't used the tweaks so I can't say what happened there. 

Was it using the grub bootloader or windows bootloader?

Boot the livecd and click the try button.

Open a terminal and paste the results of this:
```
sudo fdisk -l
```

---

### Post by BlackoutWorm on 2011-06-03
> **jtarin said:**
> Tell that guy to fix your system.
What don't you understand about the instructions on that page?
 
The thing about grub, the lines of commands to type in.
I guess I could ask him to fix the pc, but if I can get the help I need from here it would go faster.

---

### Post by oldfred on 2011-06-03
If you still have memory test &  windows, you still have grub and reinstalling grub will not fix it.

You proably deleted all the kernels. You were only supposed to delete older ones and we normally recommend you keep two version just in case one has problems.

You either have to manually copy kernels, which would not be easy. Or chroot into your system from the liveCD and run a full set of updates including reinstalling the most recent kernel.

These chroot instructions are to reinstall grub which you probably do not have to do. I like kansasnoobs version as he has combined all the chroot commands into  one line which you can copy & paste. But you have to change to your drive & partition for it to work. If the one line version gives any errors then you have to do it line by line to find what is not correct.

then run all of these commands:
#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by alphacrucis2 on 2011-06-03
Ubuntu tweak should not list the running kernel as an option to delete. It never has when I have used it. Could be a bug that ought to be reported to the Ubuntu tweak dev.

---

### Post by jramshu on 2011-06-03
OP may not have deleted the kernel, may have deleted listing it in grub?

---

### Post by BlackoutWorm on 2011-06-03
ok so did I removed the kernel whatever that is?
here's the out put you asked for
 
 
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbc58b91
 
Device Boot Start End Blocks Id System
/dev/sdb1 1 30400 244183040 7 HPFS/NTFS
/dev/sdb2 30400 45601 122101260 7 HPFS/NTFS
/dev/sdb3 45601 60802 122099713 5 Extended
/dev/sdb5 45601 60179 117096448 83 Linux
/dev/sdb6 60179 60802 5002240 82 Linux swap / Solaris
 
Disk /dev/sdc: 34.2 GB, 34246492160 bytes
255 heads, 63 sectors/track, 4163 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b365b
 
Device Boot Start End Blocks Id System
/dev/sdc1 1 4163 33439266 b W95 FAT32
live@live:~$
 
So, what can this text tell you?

---

### Post by jramshu on 2011-06-03
It tells which partition Linux is on, which would be sdb5.
 
_[COLOR=Red]Since I don't know exactly what you did, run this at your own risk[/COLOR]._ It has worked for me when other OS's removed Ubuntu from the grub menu.
  This mounts the partition that ubuntu is installed on.
  ```
sudo mount /dev/sdb5 /mnt
``` This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device. 
 ```
sudo grub-install --root-directory=/mnt /dev/sdb
```Then reboot.
```
sudo reboot
```After it reboots Ubuntu should be listed in grub.
After it starts up run this to get other OS's.
```
sudo update-grub
```Reboot for good measure, and see if windows is listed.

---

### Post by BlackoutWorm on 2011-06-03
Okay so this grub thing got removed or the kernel thing? I'm comfused.
But that doesn't matter really.
I did the commands and rebootet. it didn't work.
And where did windows go.
The update grub command worked, but still no ubuntu.
 
Okay so maybe this can help.
Earlier today I started up ubuntu, changed some stuff on the panel, background and checked out ubuntu tweak.
In ubuntu teak I cleaned packages. That's the only time I had to type in the password. So that's why I think it must have happened there.
 
Now I think I understand this. Kernel is linux, and grub is the list to start windows or linux, is that right?
Ok so if that's the case. I have probably removed linux??? DAMN. Is it posible to fix it?

---

### Post by jramshu on 2011-06-03
Your going to have to do like oldfred suggested and try and reinstall the kernel using chroot to mount the partition.

Or reinstall the OS on the same partition.

EDIT: update-grub from the livecd? Got windows back?

---

### Post by BlackoutWorm on 2011-06-03
> **jramshu said:**
> EDIT: update-grub from the livecd? Got windows back?
I don't know, but iit's back. if it was the command or what it was I don't know, but that command was all I did before I rebooted.
 
Ok so kernel is not linux. Then I guess the files are still there. So how do I install the kernel?
And please use normal words. I have no idea what all the things you said are:)

---

### Post by jramshu on 2011-06-03
Never had to do this, but this is what I have found. 
_[COLOR=Red]Do this at your own risk.[/COLOR]_ 

Start the livecd, click try. Open terminal.

```
sudo mount /dev/sdb5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
```Then these if mount is successful.

```
sudo apt-get autoclean
``````
sudo apt-get clean
``````
sudo apt-get install -f
``````
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get dist-upgrade
``````
sudo apt-get install linux-image
``````
sudo apt-get update-grub
```Exit *chroot*: **CTRL-D** on keyboard

```

for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
``````
sudo umount /mnt/usr
``````
sudo umount /mnt
``````
sudo reboot
```

---

### Post by BlackoutWorm on 2011-06-03
What does this mea

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Seems like I did something wrong.

---

### Post by jramshu on 2011-06-03
Something missing from last update.

```
sudo apt-get update --fix-missing
```

---

### Post by jtarin on 2011-06-03
> **BlackoutWorm said:**
> What does this mea

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Seems like I did something wrong. Not everything you see is explosive.:P It just means it could not connect to the server and fetch some packages for some reason. If you would copy and paste the message we could tell you better.

---

### Post by BlackoutWorm on 2011-06-03
Okay I typed in the command. It gave me this


E: Some index files failed to download, they have been ignored, or old ones used instead.

And btw I can still not run the sudo apt-get install linux-image code without getting the message

---

### Post by jtarin on 2011-06-03
> **BlackoutWorm said:**
> Okay I typed in the command. It gave me this


E: Some index files failed to download, they have been ignored, or old ones used instead.

And btw I can still not run the sudo apt-get install linux-image code without getting the message In a terminal issue the command ```
gksudo gedit /etc/atp/sources.list

```and post the results. What version of Ubuntu are you running? You should always post that or have it in your signature.

---

### Post by BlackoutWorm on 2011-06-03
here\s the output


No protocol specified

(gksudo:5231): Gtk-WARNING **: cannot open display: :0.0
root@live:/#

---

### Post by jtarin on 2011-06-03
> **BlackoutWorm said:**
> here\s the output


No protocol specified

(gksudo:5231): Gtk-WARNING **: cannot open display: :0.0
root@live:/#
I misspelled.
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by BlackoutWorm on 2011-06-03
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
# deb [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu) maverick main
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) maverick main

---

### Post by jtarin on 2011-06-03
This is mine as an example....yours is OK, but as you go along you might want to trim it down when you learn what you need and don't need.```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://ru.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-proposed main restricted universe multiverse 
deb http://ru.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
######deb http://archive.canonical.com/ubuntu maverick partner

#####Third-Party Repos
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main



```Go into Synaptic>Settins>Repositories and try to find another server to use. Download from:<choose other from the dropdown menu>. Sometimes a faster server will let you connect without too much interference.

---

### Post by BlackoutWorm on 2011-06-03
Synaptic. Im still on the live cd.
Will synaptic install things to the ubuntu I have installed

To be honest. I dont think this is something for me.
I really hate computer stuff. but I decided to try this thing out since my friend recommended it to me.
Now I see how he likes it. You see. Computer things is a hobby to him. Ow well. Thanks anyway. guys.
How do I get windows back to normal_

---

### Post by jramshu on 2011-06-03
If you followed the directions on chroot-ing the system everything you have been doing was on the filesystem you are trying to recover.

If it was me I would just reinstall it. This is a good lesson about what not to do with tweaks.

---

### Post by BlackoutWorm on 2011-06-04
What lesson?
I used a program called Ubuntu Tweak, but only because my friend told me it was a great program to use for software and organizing and such. I didn't actually tweak much.
I have no idea what happened or why. But if I have to reinstall this thing every nor or then because it's too easy to mess it all up, I'll just stick with Windows.
I use my computer for too important things, and I'm not interested in messing up stuff.
I'm just happy I didn't lose any important data.
But I'm back on my Windows now finally. That thing was scary really.
Thank you all for your help and support.

---

### Post by jtarin on 2011-06-04
> **BlackoutWorm said:**
> What lesson?
I used a program called Ubuntu Tweak, but only because my friend told me it was a great program to use for software and organizing and such. I didn't actually tweak much.
I have no idea what happened or why. But if I have to reinstall this thing every nor or then because it's too easy to mess it all up, I'll just stick with Windows.
I use my computer for too important things, and I'm not interested in messing up stuff.
I'm just happy I didn't lose any important data.
But I'm back on my Windows now finally. That thing was scary really.
Thank you all for your help and support.The lesson of....If your not certain of a thing to do.....all you need to do is ask before proceeding.That is why the forum is here.I can remember reinstalling Windows many times because I didn't ask before I tried something new. Don't blame the operating system for your mistakes. Ubuntu Tweaks does not come with the standard official Ubuntu download. That should tell you something. Windows had an application called "Power Toys", which you could have done some serious damage to your Windows installation, so just because something is there to download doesn't mean you don't have to accept responsibility for it hosing your system.

---

### Post by BlackoutWorm on 2011-06-05
I'm not the guy who asks every time I do something.
I mean. When does cleaning the system mess up Windows?
At least I have never had a problem like that in windows.
No matter what program I use in windows, nothing scary have aver happened to me.

The latest kernel should be invisible within the ubuntu system.
And there should be a restore feature added to grub where you can fix things like this.
It would also help if the livecd could install all system related files that aren't in the system already.

All I'm saying is, I had a horrible first impression with Linux yesterday. And if this is not a usual thing that happens and it's not suppose to happen, I really hope the ubuntu people will do something about it.
Most people would probably give up linux after something like that. I will maybe give ubuntu a new chance.
I have to do some research on my own and see if there is something more newbie friendly.

---

### Post by jtarin on 2011-06-05
> **BlackoutWorm said:**
> I'm not the guy who asks every time I do something.Then you have to be the one that accepts responsibility for any wrong action on your part.

> **BlackoutWorm said:**
> The latest kernel should be invisible within the ubuntu system.It is to Ubuntu Tweak. I think you messed up your system some other unorthodox way.

> **BlackoutWorm said:**
> And there should be a restore feature added to grub where you can fix things like this.There is called Grub -update or Grub -install.

> **BlackoutWorm said:**
> All I'm saying is, I had a horrible first impression with Linux yesterday. And if this is not a usual thing that happens and it's not suppose to happen, I really hope the ubuntu people will do something about it.Most people would learn a little about their system before mucking about with it.

> **BlackoutWorm said:**
> Most people would probably give up linux after something like that. I will maybe give ubuntu a new chance.
I have to do some research on my own and see if there is something more newbie friendly.Most people persevere a little more than that. You would be surprised at how many people look at it as a challenge rather than defeat.

---

### Post by BlackoutWorm on 2011-06-05
Wait, grub update and grub install? Will they restore these commands restore the system? Okay, so grub is Linux?
I'm confused now.
If you say grub -update will restore the system.
Okay so I lost my kernel now, if this happens again how can I used grub -update to get that kernel back?
And yes, i know it must have been ubuntu tweak. As I said before, that's the only thing I tried.
But okay. It's too late now anyway.

---

### Post by alphacrucis2 on 2011-06-05
GRUB is a boot loader. It gets invoked by the boot process of your system BIOS. Windows has it's own boot loader but grub is able to invoke the Windows boot loader to start windows. Grub can also boot linux kernels. When GRUB is installed, the master boot record is overwritten by GRUBs master boot record, the rest of GRUB and its' config files are written to /boot. When you run update-grub, it tries to determine what OS's exist on the system and updates the GRUB boot menu to reflect the OS's that GRUB can boot.

[http://www.gnu.org/software/grub/]("http://www.gnu.org/software/grub/")

---

