---
title: "Setting up my first dual boot Linux/Linux system"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by Dry Lips on 2011-03-10
Hi I'm a noob setting up my first 100% pure Linux dual boot system.
I'll begin with installing Kubuntu alongside Ubuntu 
(yes I know, it's just another flavour), and I need some help:

Ubuntu is currently installed on dev/sda2/5, so I want to install
the root of Kubuntu on dev/sda1 (labelled “root”) and the home
at dev/sda3 (labelled “backhand”). Booting from the LiveCD and
choosing advanced setup, I can choose partitions and select how
to mount them... 

- Is the /boot option where the root goes?
- I suppose the /home option is where the home goes?
- If I don't specify a /swap partition, would Kubuntu then use the 
existing swap partition at dev/sda6.
- Is the grub automatically updated when installing a second linux OS?
- Will the installer touch sda2/5 where Ubuntu is installed, if I don't 
select any option at those partitions?

---

### Post by mikewhatever on 2011-03-10
- Is the /boot option where the root goes? 
**Not sure what you mean, /boot is inside /.**

- I suppose the /home option is where the home goes?
**Yes**

- If I don't specify a /swap partition, would Kubuntu then use the existing swap partition at dev/sda6.
**yes**

- Is the grub automatically updated when installing a second linux OS?
**yes**

- Will the installer touch sda2/5 where Ubuntu is installed, if I don't select any option at those partitions?
**no**

---

### Post by ~Plue on 2011-03-10
/off-topic/ isn't the size of root and swap partitions a little too... extra?

---

### Post by Dry Lips on 2011-03-10
**mikewhatever**:

I though /boot was where the root was installed. How do you select where the root is installed then?

**~Plue**
Could be... What would you recommend?

---

### Post by oldfred on 2011-03-10
If manually installing it will give you the option to install just about any of the / (root) folders as a partition. Old systems, RAID and servers may need a separate /boot. All the other folders may only need a partition for server installs where the server needs certain data isolated.

Standard desktops only need / & swap. Adding /home as a separate partition is usually suggested to make it easier to reinstall, but if you are installing more than one system, I would also keep /home inside / and add a data partition that can have your data easily accessible from both installs. Then /home only has configuration info and is small and easy to backup.

The last installed system will install its grub2 bootloader to the MBR. That system then will be in control and give you the choice to boot all systems.

---

### Post by el_koraco on 2011-03-10
> **Dry Lips said:**
> **mikewhatever**:

I though /boot was where the root was installed. How do you select where the root is installed then?



you select the partition you want to use as root, and set the mountpoint option to /. when you're done selecting the 7 (root) and swap partition, the installer will ask you where you want GRUB (the default ubuntu bootloader-) to be installed. that's /boot.

---

### Post by ~Plue on 2011-03-10
> **Dry Lips said:**
> 
Could be... What would you recommend?
IMO, if you're setting a separate /home, 15 gb for / would be more than plentiful

---

### Post by Dry Lips on 2011-03-10
[B]
Oldfred:[/B]
> The last installed system will install its grub2 bootloader to the MBR.  That system then will be in control and give you the choice to boot all  systems.     I've got a program called StartUp-manager installed that let
me choose which OS to boot first, so I guess I can still choose
Ubuntu as the default OS... Or what?
[B]
el_koraco[/B]:
                                > you select the partition you want to use as root, and set the  mountpoint option to /. when you're done selecting the 7 (root) and swap  partition, the installer will ask you where you want GRUB (the default  ubuntu bootloader-) to be installed. that's /boot.     Okay, I see... I was a bit confused why there wasn't any 
/root option available... That explains it. So the best thing
would probably be to use mark my current Ubuntu partition as /boot?

Let me see if I've got it right:

Dev/sda1 &#8220;/.&#8221;
dev/sda3 /home
dev/sda5 /boot?????

That's all I need, right?
[B]
~Plue[/B]
> IMO, if you're setting a separate /home, 15 gb for / would be more than plentiful     Is program files and such installed in root or in home? 
You don't risk running out of space with 15 GB? [COLOR=#000000][FONT=Verdana,Arial,Tahoma]I was recommended to set[/FONT][/COLOR]
the root to around 30 GB in another thread of mine...[URL="http://ubuntuforums.org/showthread.php?t=1703381"]
[/URL]

---

### Post by ~Plue on 2011-03-10
~4GB is enough for the base system and 8-10GB would be alright for a normal desktop user. but even with plentiful hard disk space, i would still say that 30gb is *way* too much..

/linux programs would be installed in root. and windows games and such you install using wine or cedega would be in your home folder

---

### Post by el_koraco on 2011-03-10
> **Dry Lips said:**
> **el_koraco**:
                                Okay, I see... I was a bit confused why there wasn't any 
/root option available... That explains it. So the best thing
would probably be to use mark my current Ubuntu partition as /boot?

Let me see if I've got it right:

Dev/sda1 “/.”
dev/sda3 /home
dev/sda5 /boot?????

That's all I need, right?
[]("http://ubuntuforums.org/showthread.php?t=1703381")

not dev sda 5 boot. when you specify a / and /home partition and click next on the installer, you'll get a prompt asking you where to install grub. since you're already running ubuntu, you don't need to install grub during the kubuntu installation process. so choose the don't install grub option. after the install, you can simply boot into ubuntu, open a terminal and type in 

sudo update-grub

reboot, and you'll get a prompt asking you which os you wanna load. you can change that order either in ubuntu or kubuntu, using start-up manager. but please make sure you back up before doing the install, that way if something goes wrong, you won't lose any critical data.

---

### Post by el_koraco on 2011-03-10
btw, marking your partitions has no influence on the installation. it is simply a way of reminding yourself what the partitions mean. btw2, since you don't seem fully versed in all the ins and outs of partitioning, i recommend you read this two or three times, it's an excellent tutorial. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Dry Lips on 2011-03-10
Now I've installed Kubuntu, but it seems as if it has done something strange to
my grub. All that shows up are the usual Ubuntu-alternatives, no Kubuntu.
But when I select the option I'd normally use, it is Kubuntu, not Ubuntu that boots up.

I used the default bootloader option, which was dev/sda...


-----
edit:
What confused me was that Kubuntu comes up as **U**buntu in the Grub.
Actually everything works just fine!

---

### Post by Dry Lips on 2011-03-10
el_Korako.

Your advice about don't installing no grub came a little
late I'm afraid... Sorry!

---

### Post by Dry Lips on 2011-03-10
No, wait, I can still boot into Ubuntu... Sorry, I'm getting a bit tired.
(It was a bit further down on the list)

---

### Post by Dry Lips on 2011-03-10
> btw, marking your partitions has no influence on the installation. it is simply a way of reminding yourself what the partitions mean. btw2, since you don't seem fully versed in all the ins and outs of partitioning, i recommend you read this two or three times, it's an excellent tutorial. 

Yeah, I knew that! What I didn't figure out was that / is another way of saying root.
And yes, I'll read that tutorial... tomorrow ;)

---

### Post by el_koraco on 2011-03-11
> **Dry Lips said:**
> Yeah, I knew that! What I didn't figure out was that / is another way of saying root.
And yes, I'll read that tutorial... tomorrow ;)

sorry, i had no desire to offend you, i just remember my first dual boot-partitioning scheme, and how i had no idea what mountpoint and flag were really all about. the tutorial i posted came in pretty handy, in that it describes the whole process in great detail. since you installed kubuntu's grub in the MBR, it simply made kubuntu the first boot option. what you an do now is fire up start up manager in either ubuntu or kubuntu, and choose which *buntu you wanna boot as default.

---

### Post by fabricator4 on 2011-03-11
> **Dry Lips said:**
> Yeah, I knew that! What I didn't figure out was that / is another way of saying root.
And yes, I'll read that tutorial... tomorrow ;)

No, it's the only way of saying root.  /root is something different: the data area for the root user.  To say it another way, the filesystem root (/) is NOT the same things as the root user's 'home' directory (/root).

Yeah, it's a point of confusion if you've never been exposed to linux before, and especially since modern distros won't expose you to the term "root user" until you get into more advanced subjects.

Chris.

---

### Post by Dry Lips on 2011-03-11
> sorry, i had no desire to offend you, i just remember my first dual boot-partitioning scheme, and how i had no idea what mountpoint and flag were really all about. the tutorial i posted came in pretty handy, in that it describes the whole process in great detail. since you installed kubuntu's grub in the MBR, it simply made kubuntu the first boot option. what you an do now is fire up start up manager in either ubuntu or kubuntu, and choose which *buntu you wanna boot as default.

**el_koraco,**
I hope I didn't seem offended! Sorry if I did! What I meant
when I wrote that I would read your tutorial, was that it was
2 o'clock past midnight, and that my eyes were yearning 
for sleep... (I mean, this thread was posted in the Absolute
beginner section, so I'm thankful for any good advice.)
Thanks for your link, I *will* read it :) And yes you're quite
right, the whole concept with mountpoints and logical 
partitions is confusing to a former windows-user. (I've only
been using Ubuntu for 3-4 weeks.) First when I installed Ubuntu,
a few weeks ago I wanted to run a dual boot system with
windows, and had created partitions in windows to be used
for Ubuntu. But I  when I clicked at the advanced setup the
mount-point options seemed like total gibberish to me, 
and I had to resort to letting Ubuntu do all the partitioning automatically.
(For the record: I removed Windows a couple of days ago, 
if I need Windows, I'll use Wine+VirtualBox instead. And I 
almost haven't touched windows since I've got this computer)

> No, it's the only way of saying root. /root is something different: the data area for the root user. To say it another way, the filesystem root (/) is NOT the same things as the root user's 'home' directory (/root).

Yeah, it's a point of confusion if you've never been exposed to linux before, and especially since modern distros won't expose you to the term "root user" until you get into more advanced subjects.
Chris, thank you so much for your clarification. This is exactly
the kind of stuff I need to hear about!

And finally I want to thank **all** you guys have helped
me out in this thread! I've learned a lot, cheers!

---

### Post by Dry Lips on 2011-03-11
Finally I have a last couple of questions:

**1. Removing a dual boot system**:
I'll use Ubuntu for my main OS, but I'll play around with
other distros, so I'll need to know how to safely remove
the dual boot system I've set up. I would suppose it is easy:
Erase the partitions that contain the other OS, and then 
do a “sudo update-grub”. Please correct me if I'm wrong.

**2. Installing non-K/X/Ubuntu OS. **
Is there any significant difference to the process of setting
up a dual bot system, when you use a non-Ubuntu OS alongside
Ubuntu? Any potential problems I should be aware of? (I plan 
checking out at least Mint, Fedora, OpenSuse in the future, 
in order to broaden my experience with Linux.)

---

### Post by el_koraco on 2011-03-11
1. you're right, except for the fact that you don't really need to erase the partitions if you don't want to, you can just format the ones you've already made. format them as ext3 or ext4. you can erase the partitons, and allocate the rest of the space to ubuntu. you don't really need more than 10 GB if you just wanna try out a distro, and you don't need separate / and /home. but it's up to you. 

2. i've personally had no problems so far. however, this is exactly why backup counts. 

have fun experimenting.

---

### Post by Dry Lips on 2011-03-11
> **el_koraco said:**
> 1. you're right, except for the fact that you don't really need to erase the partitions if you don't want to, you can just format the ones you've already made. format them as ext3 or ext4. you can erase the partitons, and allocate the rest of the space to ubuntu. you don't really need more than 10 GB if you just wanna try out a distro, and you don't need separate / and /home. but it's up to you. 

2. i've personally had no problems so far. however, this is exactly why backup counts. 

have fun experimenting.

Ok, I see. Thanks a lot. 
Cheers!

---

### Post by oldfred on 2011-03-11
Most installers give you a choice on where to or whether to install a boot loader.  Ubuntu only gives it if you do manual install/manual partition.

In case another system does install its boot loader you should be able to boot Ubuntu and easily reinstall grub from that. If the install does not give the option to boot Ubuntu you need to have a LiveCD and can easily reinstall grub2's boot loader to the MBR.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
# then run
sudo update-grub

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by el_koraco on 2011-03-11
@oldfred 
+1

---

### Post by Dry Lips on 2011-03-12
**Oldfred**, that is very valuable information! 
When I installed Kubuntu I for a minute thought
 it had messed up my grub. It really hadn't, 
but if it had, I would have been at a loss to find 
out how to to restore the grub. I'll be taking notes 
of this information! You never know,... it could prove 
essential in my future experiments with dual-boot
systems...

---

