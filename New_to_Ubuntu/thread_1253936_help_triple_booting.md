---
title: "help triple booting"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by delukard on 2009-08-30
Hi. i'm new to these forums and to linux.
i have been a microsoft OS user since the dos days.
i have never used linux.
but i have been wondering about linux lately.
I have been using xp64 since 2005 and then dual boot with vista 64 since it got released.
(i only use x32 versions of windows in virtual pc)
i want to learn ubuntu, and wanted to do a triple boot with the following.
xp64,win7x64 and ubuntu 32(the 64 version doesn't support 32bit software does it?)
Here are my main pc specs.

Amd64x2 5400 am2
4gb ddr2 800
gforce 9600gt
Gigabyte GA-MA78G-DS3H v1.0
audigy2 value
belkin wireless N usb f5d8053

my question is ( i'm reinstalling all my software OS included)

.-I already have xp64 installed and going to install windows7, but before i do this
what is the best procedure to install this triple boot?
windows  OS's first then ubuntu?
or ubuntu first then windows OS's

.- will i run into driver problems in ubuntu? since no one of the manufacturers doesn't have ubuntu drivers.

thank's for the help and advice!!

---

### Post by earthpigg on 2009-08-30
> 
.- will i run into driver problems in ubuntu? since no one of the manufacturers doesn't have ubuntu drivers.

check the ubuntu hardware compatibility wiki. 95% of the time, there is no need for a driver as the Linux kernel will support it directly... the way windows does with keyboards? Linux attempts (and usually does a good job at) with all hardware.

install however many versions of windows you want first, and get them all playing well with each other.

_then_ install Ubuntu.

generally speaking, whatever operating system you install _last_ is the one that will be in charge of the Master Boot Record (MBR).

Ubuntu will see Windows(s) and play nice, adding it/them as an option(s) on the boot menu.

Windows will see Linux and "LOL GTFO" and ignore it (or worse).

so, get everything with Windows set up exactly how you want it... then install Ubuntu.

ideally, with this complex setup you should be doing all partitions manually.

the best tools to create/resize/modify any Windows partition(s) are Windows tools.

the best tools to create/resize/modify any Linux partition(s) is whatever tools you feel like using.

while you are setting up and configuring your Windows(s) install(s), make a 2gb partition and leave it unused in addition to whatever you want as your primary Ubuntu partition.

when its time to install ubuntu and you are in the manual partition setup phase: designate the 2gb partition as 'linux-swap'.

then, you have two options:
1. toss all of linux on one partition with '/' as the mount point and with the bootable flag.
2. make a 15gb '/' partition with the bootable flag, and use the rest as a partition with /home as the 'mount point'. /home = 'my documents and settings'. there are some great reasons to do this (google it), but you dont have to if you dont like. i didn't on my first ubuntu install, it wont break anything _not_ to do it, and plenty of people dont.


if you have ever looked at a graphical partition editor, then the linux-specific one that is part of an ubuntu install will make sense to you when you see it. use ext4 as filesystem.

---

### Post by magicmax0 on 2009-08-30
Install your windows OS's first. Then install ubuntu, in the partitioning portion of the install process you can manually resize your windows partitions.

---

### Post by raymondh on 2009-08-30
- Remember your 4 partition limit (4 primary or 3 primary + 1 extended). 
- Defrag windows prior to shrinking it to create space for Ubuntu.

This is dual boot but may help you:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by theozzlives on 2009-08-30
As you may know, Windows DOES give the option to specify your partition size if you have ALL unpartitioned space. Make your Windows partitions and save about 10 GB for root (/), at least your amount of RAM for swap and the rest for /home.

You probably want your 2 Windows and / as primary and /home and swap as logical. Mind you Windows only likes one primary so the previous scenario may not work, you may need one Windows and / as logical also.

EDIT: Note my Dual boot setup on a small 40 GB HD (it's my test/fax machine).

---

### Post by delukard on 2009-08-30
thank's for the help. i downloaded the ubuntu pocket guide and intend to read it over nigth.
yes i forgot to add my partition info. so here it is.
 i have 3 sata II hd's
1x250
1x320
1x500

the WINDOWS os'e are install in the 250hd's wich have 3 partitions already(this is where i want my triple setup)
1x60gb(windows xp64. primary)
1x125gb(software,isos etc.)
1x60gb unallocated (this is where i would like to install windows 7 on 30gb and ubuntu on the remaining space)
so it will be 4 partitions on 1 250gb hd, 3 for os installs and 1 for my isos etc.

I don't want to resize anything. can it be done like i describe it above

---

### Post by JC Cheloven on 2009-08-30
> **delukard said:**
> ...
the WINDOWS os'e are install in the 250hd's wich have 3 partitions already(this is where i want my triple setup)
1x60gb(windows xp64. primary)
1x125gb(software,isos etc.)
1x60gb unallocated (this is where i would like to install windows 7 on 30gb and ubuntu on the remaining space)
so it will be 4 partitions on 1 250gb hd, 3 for os installs and 1 for my isos etc.

I don't want to resize anything. can it be done like
As previously said:
- It is very advisable to have a swap partition.
- There is a limit of 4 primary partitions for hard disk. 
So you need these partitions (for example):
- 60Gb ntfs primary
- 125Gb ntfs primary
- 30Gb ntfs primary
- 30Gb extended, and inside it:
-- 29Gb ext3 (or ext4 if installing jaunty) 
--  1Gb swap

It's not difficult to setup, but you probably had better to run gparted from live cd to prepare the extended partition.

---

### Post by delukard on 2009-08-30
ok so i just installed my first ubuntu.
a friend game me the disk so i don't even know what version it is.(it's a live version with the option to be installed)
i'm going to be using it to use the web and the form there see what happens.
Thank's for the help.

btw.
i created a swap partition and an extended system, mounted as /
was it ok?

---

### Post by raymondh on 2009-08-30
> **delukard said:**
> 
i created a swap partition and an extended system, mounted as /
was it ok?

Congratulations.

Yes.  Ubuntu does not care whether it be in a primary partition or a logical partition inside an extended.  '/' is known as ROOT ... where everything your OS grows/comes from.

happy Ubuntu-ing.

---

### Post by oboedad55 on 2009-08-30
> **haoyunz9 said:**
> [PFA lined ball valve](http://www.corrosion-resistant-valves.com/corrosion-resistant-pipe-fitting.html) of PFA is very similar in composition to the fluoropolymers PTFE and FEP (fluorinated ethylene-propylene). PFA and FEP both share PTFE's useful properties of low coefficient of friction and non-reactivity, but are more easily formable. FEP is softer than PTFE and melts at 260 °C; it is highly transparent and resistant to sunlight.

Fantastic! Thanks for sharing. :o

---

### Post by delukard on 2009-08-31
i'm having a problem with the nvidia drivers.
ubuntu automatically  downloaded the drivers but i can't choose 1440(my monitor native res) it only goes to 1360x768 and it gives me 24bit only(wich looks to blurry)
this is the info on the NVIDIA X SERVER SETTINGS
server version number 11.0
the X.org foundation
180.44
nv control version 1.17

i'm going to be googling this.
btw. i didn't knew that i was installing an ubuntu server.(a friend gave me the disk, i didn't what version was it LOL)

---

### Post by jms1989 on 2009-08-31
Indeed, if it is a ubuntu server install, you can run sudo apt-get install ubuntu-desktop to install the gnome desktop. 

You can get your nvidia drivers at the nvidia website. Just choose the card type, series, and if you are using a 23bit or 64bit install, then download. Once finished, do Ctrl+Alt+F1, login as standard user and run sudo /etc/init.d/gdm stop to kill the graphical environment. Next run the downloaded file by doing "sh /path/to/file/file.bin". I like using the tab key for auto-complete. Follow the on-screen instructions to install the drivers and once done do "sudo /etc/init.d/gdm start". You should be using the new drivers and you should be able to specify the resolution for your display.

---

### Post by Grifulkin on 2009-08-31
Well I might be a little too late, but a swap partition is NOT necessary.  Nice if you like to Hibernate, but definitely not Necessary.  I finally did my first dual boot today without a swap partition.  I have 4 gigs of ram, I don't think I'm going to use that up doing what I do.  So you NEED a seperate swap parition if:

A. Run over your 4 gigs of RAM
B. Hibernate the computer
C. Just because

---

### Post by delukard on 2009-08-31
tbh. i don't like swap partitions and unless i'm mistaken, i don't even see the point why linux creates a swap partition on the same hd.
that's why i leaved x32 versions of windows, because they were to dum to use the ram.
why would i like to have a 500mb of page file when i have 3gb of free ram?(windows xp32LOL)
i'm only a lowly hardware tech that knows only how to build pc's and optimize windows.(so i'm no software tech)
in the old days i did understod the necesity of the pafe file(ram was so expensive) but bot today.

i'm going to see if i can reinstall linux (desktop version x64)

and about the nvidia drivers, i'm sorry i have to say that i didn't searched on nvidia site.

---

### Post by louieb on 2009-08-31
> **delukard said:**
> tbh. i don't like swap partitions and unless i'm mistaken...why would i like to have a 500mb of page file when i have 3gb of free ram?

Holdover from the days when 256MB was a lot - lol.  Also a swap partition is required for those that want to hibernate their PC. (need to be a least as large as the amount of ram). 
 
> i don't even see the point why linux creates a swap partition on the same hdKISS - But just like you can force windows to put its page file on a different hard drive. You can use manual partitioning during the install to put swap on another drive.    

>  and about the nvidia drivers, i'm sorry i have to say that i didn't searched on nvidia site.More that likely the install did not detect your display correctly. So it just defaulted to a resolution it thought would work.  The drivers install through hardware drivers are usually new enough.  Getting it to use  higher resolution is still one of biggest pains left.

---

### Post by JC Cheloven on 2009-08-31
> **delukard said:**
> tbh. i don't like swap partitions and unless i'm mistaken, i don't even see the point why linux creates a swap partition on the same hd. 
...
It is said that swap is much like condoms: Better having it and don't need it, than needing it and don't have it :lolflag:

---

