---
title: "Stuck in Limbo"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-06-20
Originally Posted by **JASONFUSARO** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10961343#post10961343") 				
 				OK I am back running Ubuntu Live CD

With Regards to the Question of what I am trying to accomplish here is a list




1. Get back to being able to dual boot Vista and UbuntuStudio32 bit

2. Get rid of UbuntuStudio64 bit of my drive

3. Get UbuntuStudio32 running with all my apps and setup options intact

4. Remove Fedora from the drive

5. Remove Fluxbox from the drive, which is actually squished

6. Learn the easiest and most efficient backup routine and software to use

7. Download a quick loading and basic distro to run as a live  environment with the ability to more administrative tasks than Ubuntu as  a backup system in case corrections need to be done on the original  system when it won't boot. 



 why does fie manager recognize my directory structure and hardware  attachments yet Gparted can't  and disk utility can see it also. See  attached Screenshots

---

### Post by jtarin on 2011-06-20
OK first.....can you boot and get to the desktop with an Ubuntu Live CD?

---

### Post by idoitprone on 2011-06-20
hmmmmm there a second thread for the cd command problem


like i  said in the other thread Linux is case-sensitive

you need to type
 
```
cd /media/sdb1/DOSEMU

```
lets take a look of the partition table

```
sudo fdisk -l

sudo blkid
```

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and maybe with boot info script

---

### Post by jtarin on 2011-06-20
> **idoitprone said:**
> hmmmmm there a second thread for the cd command problem


like i  said in the other thread Linux is case-sensitive

you need to type
 
```
cd /media/sdb1/DOSEMU

```
lets take a look of the partition table

```
sudo fdisk -l

sudo blkid
```

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and maybe with boot info script
@idoitprone.....too much info at one time.....you trying to overload the guy. Read his post again.....he really needs step by step instructions or so it seems.:p

---

### Post by mfstutz on 2011-06-20
I've been in your position a dozen times.  I use this tool most of the time to bail me out:  Acronis Disk Director 11 Home.  It has an OS tool you can use.  I usually do the following:

-- backup the drive I want to recover (clone disk)
-- use the Windows Recovery Tool of the most recent Windows release I'm trying to include in a multi-boot (use the original CD & during install choose the "recover" option.
-- Install a new Ubuntu telling it to dualboot
-- Then when the "recovered" windows is dual booting with the new "Ubuntu" I replace the "new" Ubuntu with the "old" Ubuntu by copying the partition without tampering with the boot records.

This has worked for me a few times . . . it might give you some ideas with your current issues.

---

### Post by JASONFUSARO on 2011-06-20
Thanks again for the assistance


here is the  partition info you asked for


Welcome - Parted Magic (Linux 2.6.38.4-pmagic)

fdisk hmmm what does that mean ? fix, format,  find,float him let me google it

ok found it

[http://linux.about.com/od/commands/l/blcmdl8_fdisk.htm](http://linux.about.com/od/commands/l/blcmdl8_fdisk.htm)

just like a DOS command

root@PartedMagic:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x532e7c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0           0           0    0  Empty
/dev/sda2          411648   183967743    91778048    7  HPFS/NTFS/exFAT
/dev/sda3       183969792   250667007    33348608   83  Linux
/dev/sda4       250667046   976784129   363058542    f  W95 Ext'd (LBA)
/dev/sda5       250669056   341999615    45665280   83  Linux
/dev/sda6       342001664   393201663    25600000   83  Linux
/dev/sda7       393207003   416372650    11582824   82  Linux swap

Disk /dev/sdb: 7969 MB, 7969177600 bytes
126 heads, 10 sectors/track, 12353 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192    15564799     7778304    7  HPFS/NTFS/exFAT
root@PartedMagic:~# 



and 

oh wait let me google this

[http://linux.die.net/man/8/blkid](http://linux.die.net/man/8/blkid)

**Name**

 blkid - command-line utility to locate/print block device attributes **Synopsis**

 **blkid** [ **-hlv** ] [ [ **-c** *cachefile* ] **-w** *writecachefile* ] [ **-o** *format* ] [ **-s** *tag* ] [ **-t** *NAME*=*value* ] [ *device* ... ] 



OK

root@PartedMagic:~# blkid
/dev/sda2: LABEL="WindowsVista" UUID="0E5A6700395DFEEF" TYPE="ntfs" 
/dev/sda3: LABEL="UbuntuStu64Bit" UUID="03cf3622-a18f-47c4-94d0-9b7c887f0411" TYPE="ext4" 
/dev/sda5: LABEL="UbuntuStudio32" UUID="234cd951-aed4-4866-b85a-c28ae4020598" TYPE="ext4" 
/dev/sda6: LABEL="_Fedora-15-i686-" UUID="b06bbdc9-7a7f-47a4-8fc7-9e09f9960319" TYPE="ext4" 
/dev/sdb1: LABEL="SoftwareDesign" UUID="426C23CB6C23B895" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/loop1: TYPE="squashfs" 
/dev/sda7: UUID="c5a5b515-db58-4706-b2d4-53379a5a27e7" TYPE="swap" 


HEY where is that Fluxbox install?? whats up with the squash stuff???



hey I never asked it to compress anything as far as I can recall,  although it was pretty late when I did the instal, and you know how it  is, after staring at error messages all day you get kinda trigger happy  with the mouse button, I may have clicked something somewhere along the  line.

and don't ask me to delete that ubuntustudio32bit I was on that for a few hours and it's packed with everything a guy could wan't and someday I would like to get it back!!!




now it would be nice if I could block all static interception from other helpers, it seems much easier if I was only following your assistance.


If others see that you are the guy with the answers why would others want to try and top you by making this a difficult thread to track. I mean if your assistance is working why do I need to have everybody elses help, does everyone understand this concept??


Now I can make a cup of coffee, hope you see this soon and as I said before

many thanks

---

### Post by JASONFUSARO on 2011-06-20
Why in the world does Gparted come up and show me /dev/sda1 as being unallocated when everyone else can see it is allocated, it has everything??


Boy I hate when that happens!!


Why in the world can it not recognize what file manager can and fdisk and blkid can, is it the version I am running, is it from a different time zone, what gives, its crap like this that slows your learning down to a snail on a Quaalude  pace!

---

### Post by JASONFUSARO on 2011-06-20
root@PartedMagic:~# sudo bash [path/to/the/download_folder]/boot_info_script.sh
sh: sudo: command not found
root@PartedMagic:~# 

now you must remember I am running Parted Magic, because that is all I can get to work, I am running of the CD because I can't get my system going!!


So I am like I said in LIMBO


So some commands might not work as if I was back home on my hard drive, instead of being here!

So take note of where I am and post help tidbits accordingly so I can find my way back and not get further away than I already am!!

so if I was back home I guess boot info script would be able to maybe help but not here where I am.[COLOR=Red][B] running off a Gparted CD

[COLOR=Black]This is the only place that works somewhat, I can access this forum, maybe check on a few things, run some system commands but I am not actually sitting in my office!! So answering the phone is a bit difficult right now.



root@PartedMagic:~# bash ~/Desktop/boot_info_script.sh
bash: /root/Desktop/boot_info_script.sh: No such file or directory
root@PartedMagic:~# 


see this doesn't work either

arghhhhhhhhhhhhhhhhh!!!!!


I hate it where I am, nothing works!!!!!!!!!!!!





[/COLOR][/B][/COLOR]
thanks

---

### Post by JASONFUSARO on 2011-06-20
When I run my windows recovery it comes up with no drives listed!!!!!!!!

and I can't load the drivers, I tried just about every one listed in my WD driver directory and gave up!!!!

So I can't even get windows back

---

### Post by JASONFUSARO on 2011-06-20
I already tried this read my post, all of it, I have UbuntuStudio32,64 , Fedora, now two sqaushed FluxBox's a backup copy of UbuntuStudio32 which isn't showing up in my output there



Remember to post according to where I am at, IN LIMBO

thanks

---

### Post by JASONFUSARO on 2011-06-20
I also have a 160Gib,500Gib and 260Gib External USB drives not hooked up the sdb1 is a flash card which came in handy from my camera, I have another 8Gib and 4Gib so I put this one to use to hold downloads and stuff but it isn't recognized when I run of another Gparted version like the one that is on the Linux rescue CD. It is a good thing I made those ISO's when things were working. If I hadn't I would really be stuck, at least I can do some things!!!

Like I said in my original post I have tried using UBCD utilities, I have a CD of that also but nothing seems to work. I also made a CD of easyclone but when I ran that it said I needed the full version to run some options so since it was a CD-R I have another Frisbee to play with.

Or a coffee cup coaster,  windchime, I think if you put them in a fire you see amazing things, or what would happen if it was microwaved.

I think it's useless but I could be wrong, I usually am you know.

---

### Post by JASONFUSARO on 2011-06-20
(\ /)(O.o)(> <) when I try and modify my signature this is all that shows up?? It isn't converted to whatever it should be what am I doing wrong there?

Remeber I am like a newborn baby, fresh out of the womb, goo in my nose, clogged eys with that white stuff everything is dark, can't even see any shadows yet. The umbilical cord is still attached and sometimes I feel like it would have been better if it was wrapped around my neck:)

---

### Post by JASONFUSARO on 2011-06-20
simplified explanation as long as one can distinuish right from left, knows what an arm,foot,leg

A) Put right foot forward ie right foot is the one just under the right arm
B) Place all your weight on that foot ie. weight is what occurs when mass comes under some force such as gravity
C) Start to move the left leg forward to put weight on Left foot ie. Those are just opposite right
D) then keep repeating and this is called  walking
E) now we can 1) keep walking or 2) stop walking

detailed explanation would be kinda

do you know what right and left are

A) if yes then go here
B) if no then go here and this will explain them to you when you understand the difference come back here and proceed to step B ie. not the step you would be taking with a foot but a point in a process, not a point like a pencil or dart or period. If you need further clarification please advise

A) Put right foot forward ie right foot is the one just under the right arm
B) Place all your weight on that foot ie. weight is what occurs when mass comes under some force such as gravity
C) Start to move the left leg forward to put weight on Left foot ie. Those are just opposite right
D) then keep repeating and this is called  walking
E) now we can 1) keep walking or 2) stop walking

---

### Post by nothingspecial on 2011-06-20
Jason, I've read this thread, and then I read it again.........

.....and I still have absolutely no idea what you are trying to achieve.

What's the actual problem.

---

### Post by JASONFUSARO on 2011-06-20
aren't the boot records in the overwritten partition?

If I could get gparted to work right now I would give a detail of it but I have to reboot and put that CD in and then I don't have access to the internet and I can't post what I am doing, I will have to reboot and then boot with this CD and then I am back in the same boat!!!!!!!!!!
without paddles, motor, sail, water is flowing in the holes, all I have is to hands to cup together to scoop out the water which will take a bit longer to get the water out and I think I might be swimming before I get it out, it meaning the water that's flowing in
 back in the same boat!!!!!!!!!!
without paddles, motor, sail, water is flowing in the holes, all I have  is to hands to cup together to scoop out the water which will take a bit  longer to get the water out and I think I might be swimming before I  get it out, it meaning the water that's flowing in
kinda like some infinite loop

I can't find a job cause I don't have a car
I don't have a car because I don't have a job

---

### Post by nothingspecial on 2011-06-20
Are you trying to repartition your drive, but the partition editor on your ubuntu cd isn't working?

What is your ultimate goal.

Is grub broken?

---

### Post by JASONFUSARO on 2011-06-20
Hi
I am running of  a Gparted CD and I can't get my system to boot! Gparted won't list what file manager sees. I can't accomplish tasks that might work if I could boot into UbuntuStudio.

---

### Post by owiknowi on 2011-06-20
does your computer perhaps have in nice friendly letters written on its cover:
'don't panic!' ?

if so it's probably best to return it to it's manufacturer in order to replace the cpu with a cup of hot tea.

meanwhile you can stop time and thus wait without shorten your lifespan.

hope to be of help and if not i apologize for the inconvenience.

p.s. if possible try to wipe the hdd with killdisk, then boot gparted/partmagic, create a msdos partition table and partition the hdd.
i know it's a hassle but this is a way to make sure the hdd doesn't have any weird stuff installed on it or a corrupted partition table.

---

### Post by JASONFUSARO on 2011-06-20
I think, I tried running that but it appears to have made matters worse. Like I said I am running a on Gparted CD not a UbuntuLiveCD, should I be running that in order to be more capable of fixing my drive problems to get a good boot going. In other words will Ubuntu Live have better access to commands that don't appear to be working off Gparted CD?

---

### Post by JASONFUSARO on 2011-06-20
I guess that's the main problem I have absolutely no idea what I am doing and each thing I do seems to worsen my situation here.

That is why I chose those emoticons that fit me perfectly

Should I run the UbuntuStudio32 live and be using that as opposed to running this Gparted CD, would I be able to accomplish the same stuff yet more. I am really baffled by the fact that every time I enter some command I get some error message and things don't seem to work as planned I have no idea how to solve my problem.
Or even express it better than I have in my first thread post?

---

### Post by nothingspecial on 2011-06-20
> **JASONFUSARO said:**
> I think, I tried running that but it appears to have made matters worse. Like I said I am running a on Gparted CD not a UbuntuLiveCD, should I be running that in order to be more capable of fixing my drive problems to get a good boot going. In other words will Ubuntu Live have better access to commands that don't appear to be working off Gparted CD?

I'm not sure what shell the gparted cd uses.....

.....but you seem logged in to the root account, which is probably the default, so it will not have sudo (because it doesn't have any other accounts)

You keep getting "command not found" because of sudo.

Try doing whatever it is you are trying to do (I still don't know what) without sudo

---

### Post by nothingspecial on 2011-06-20
I've never used this, but I trust the website it was recommended on.

Boot your ubuntu cd, then type this

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```

Then in the menu you will find it under System > Administration

---

### Post by JASONFUSARO on 2011-06-20
I am going to try this route, I am going to reboot with th UbuntuStudioLive CD, maybe this has been my problem from the start ie. trying to do things of a Gparted CD????

does it care whether it is Ubuntu or UbuntuStudio or any version specific????
 Rebooting see you in a bit, I hope??

---

### Post by idoitprone on 2011-06-20
nothingspecial commands only works, if it on an ubuntu based distro.


[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you have a booting problem, use the bootscript, so forum member can diagnosis. We are getting lost in the details.

strange, you say cannot boot with live cd ubuntu? this is out of my knowledge, but there are other problem. If you boot to commandline that is a different story, as your have a graphic card problem

maybe the tool that you used for partition sda1 did it badly. how should i know. fdisk usually print those stuff out unless its a gpt parition table, which give other errors

About the DOSEMU problem...

next time tray using tab

example
$pwd
<enter>
home/user
$ls
<enter>
Pictures
$cd Pi<tab>
$cd Pictures
<enter>

---

### Post by JASONFUSARO on 2011-06-20
> **nothingspecial said:**
> Jason, I've read this thread, and then I read it again.........

.....and I still have absolutely no idea what you are trying to achieve.

What's the actual problem.



OK I am back running Ubuntu Live CD

With Regards to the Question of what I am trying to accomplish here is a list




1. Get back to being able to dual boot Vista and UbuntuStudio32 bit

2. Get rid of UbuntuStudio64 bit of my drive

3. Get UbuntuStudio32 running with all my apps and setup options intact

4. Remove Fedora from the drive

5. Remove Fluxbox from the drive, which is actually squished

6. Learn the easiest and most efficient backup routine and software to use

7. Download a quick loading and basic distro to run as a live environment with the ability to more administrative tasks than Ubuntu as a backup system in case corrections need to be done on the original system when it won't boot. 




I first tried to run the UbuntuStudio CD but all those options were useless, like the Install GRUB to the boot loader or rescue a broken system



Now why does the install of one package line the UbuntuStudio32 run into problems when it gets to detect network hardware and yet this install of Ubuntu had no problems at all?

Second why does fie manager recognize my directory structure and hardware attachments yet Gparted can't  and disk utility can see it also. See attached Screenshots



now I was working on a reply went back a page and lost it! this is somewhat of a duplicate

I ran this commands based on a thread reply```


ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg [198 B]                      
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,742 B]                       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg [198 B]              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release [39.8 kB]                        
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,732 B]                    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [14.8 kB]         
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,380 B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [42.3 kB]  
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release [27.2 kB]               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources [862 kB]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources [4,104 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages [1,550 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources [47.1 kB]          
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources [14 B]       
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages [148 kB]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en          
Fetched 2,786 kB in 8s (322 kB/s)                                              
Reading package lists... Done





ubuntu@ubuntu:~$ sudo apt-get install boot-repair-ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-repair clean-ubiquity-common
Suggested packages:
  clean-ubiquity os-uninstaller
The following NEW packages will be installed:
  boot-repair boot-repair-ubuntu clean-ubiquity-common
0 upgraded, 3 newly installed, 0 to remove and 169 not upgraded.
Need to get 130 kB of archives.
After this operation, 700 kB of additional disk space will be used.
Do you want to continue [Y/n]? y




Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main clean-ubiquity-common all 2.0-0ppa1~natty [37.0 kB]
Get:2 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main boot-repair all 2.001-0ppa3~natty [74.2 kB]
Get:3 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main boot-repair-ubuntu all 2-0ppa1~natty [19.1 kB]
Fetched 130 kB in 1s (112 kB/s)            
Selecting previously deselected package clean-ubiquity-common.
(Reading database ... 136428 files and directories currently installed.)
Unpacking clean-ubiquity-common (from .../clean-ubiquity-common_2.0-0ppa1~natty_all.deb) ...
Selecting previously deselected package boot-repair.
Unpacking boot-repair (from .../boot-repair_2.001-0ppa3~natty_all.deb) ...
Selecting previously deselected package boot-repair-ubuntu.
Unpacking boot-repair-ubuntu (from .../boot-repair-ubuntu_2-0ppa1~natty_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up clean-ubiquity-common (2.0-0ppa1~natty) ...
Setting up boot-repair (2.001-0ppa3~natty) ...
Setting up boot-repair-ubuntu (2-0ppa1~natty) ...
Processing triggers for python-support ...



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x532e7c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       11452    91778048    7  HPFS/NTFS
/dev/sda3           11452       15604    33348608   83  Linux
/dev/sda4           15604       60802   363058542    f  W95 Ext'd (LBA)
/dev/sda5           15604       21289    45665280   83  Linux
/dev/sda6           21289       24476    25600000   83  Linux
/dev/sda7           24477       25918    11582824   82  Linux swap / Solaris

Disk /dev/sdb: 7969 MB, 7969177600 bytes
126 heads, 10 sectors/track, 12353 cylinders
Units = cylinders of 1260 * 512 = 645120 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5517

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               7       12354     7778304    7  HPFS/NTFS




ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: LABEL="WindowsVista" UUID="0E5A6700395DFEEF" TYPE="ntfs" 
/dev/sda3: LABEL="UbuntuStu64Bit" UUID="03cf3622-a18f-47c4-94d0-9b7c887f0411" TYPE="ext4" 
/dev/sda5: LABEL="UbuntuStudio32" UUID="234cd951-aed4-4866-b85a-c28ae4020598" TYPE="ext4" 
/dev/sda6: LABEL="_Fedora-15-i686-" UUID="b06bbdc9-7a7f-47a4-8fc7-9e09f9960319" TYPE="ext4" 
/dev/sda7: UUID="c5a5b515-db58-4706-b2d4-53379a5a27e7" TYPE="swap" 
/dev/sdb1: LABEL="SoftwareDesign" UUID="426C23CB6C23B895" TYPE="ntfs" 
ubuntu@ubuntu:~$ 
```


I have a copy of UbuntuStudio32 somewhere out there I don't know why its not showing up, when I did the fedora install and I pasrtitioned the disks I copied it to the end of the drive and there is supposed to be a 200MiB partition right up front at the beginniing that is not being displayed, I created it before I installed Vista way back when.


that squashfs is Fluxbox which gave me about a hundred errors when I started the install of packages to download option and I never selected an option to compress, which is what that squashfs is I think?


Did that install update I ran replace all my options and packages?

---

### Post by JASONFUSARO on 2011-06-20
> **idoitprone said:**
> nothingspecial commands only works, if it on an ubuntu based distro.


[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you have a booting problem, use the bootscript, so forum member can diagnosis. We are getting lost in the details.

strange, you say cannot boot with live cd ubuntu? this is out of my knowledge, but there are other problem. If you boot to commandline that is a different story, as your have a graphic card problem

maybe the tool that you used for partition sda1 did it badly. how should i know. fdisk usually print those stuff out unless its a gpt parition table, which give other errors

About the DOSEMU problem...

next time tray using tab

example
$pwd
<enter>
home/user
$ls
<enter>
Pictures
$cd Pi<tab>
$cd Pictures
<enter>




I downloaded that script and unzipped it, do I run it from the terminal, do I have to place it in a special directory, should I run it now or run it after I reboot to see if the updates worked??

---

### Post by nothingspecial on 2011-06-20
> **JASONFUSARO said:**
> OK I am back running Ubuntu Live CD

With Regards to the Question of what I am trying to accomplish here is a list




1. Get back to being able to dual boot Vista and UbuntuStudio32 bit

2. Get rid of UbuntuStudio64 bit of my drive

3. Get UbuntuStudio32 running with all my apps and setup options intact

4. Remove Fedora from the drive

5. Remove Fluxbox from the drive, which is actually squished

6. Learn the easiest and most efficient backup routine and software to use

7. Download a quick loading and basic distro to run as a live environment with the ability to more administrative tasks than Ubuntu as a backup system in case corrections need to be done on the original system when it won't boot. 



 why does fie manager recognize my directory structure and hardware attachments yet Gparted can't  and disk utility can see it also. See attached Screenshots




 
Number one - I suggest you go and edit your first post. Delete it and replace it with the above or something similar.

Your original post is too long and makes little sense and therefore will get less help.

English is my first language and I can't understand it. (I'm not being rude :) )

Number two - did you go (in the menu in your live cd) system > administration > 

and find the fix grub utility?

---

### Post by JASONFUSARO on 2011-06-20
> **nothingspecial said:**
> Number one - I suggest you go and edit your first post. Delete it and replace it with the above or something similar.

Your original post is too long and makes little sense and therefore will get less help.

English is my first language and I can't understand it. (I'm not being rude :) )

Number two - did you go (in the menu in your live cd) system > administration > 

and find the fix grub utility?










Point well taken


Now I ran those updates and just rebooted, and absolutely nothing. I get a Blank Screen with a flashing cursor and I don't think it is waiting for my input:)





Number two - did you go (in the menu in your live cd) system > administration > 

and find the fix grub utility?     


where is this, under tools, bookmarks, edit preferences???


I just changed my initial thread like you suggested I do, and I tried running grub but keep coming up with errors. I am going do a search for it right now

---

### Post by JASONFUSARO on 2011-06-20
> **JASONFUSARO said:**
> Point well taken


Now I ran those updates and just rebooted, and absolutely nothing. I get a Blank Screen with a flashing cursor and I don't think it is waiting for my input:)





Number two - did you go (in the menu in your live cd) system > administration > 

and find the fix grub utility?     


where is this, under tools, bookmarks, edit preferences???


I just changed my initial thread like you suggested I do, and I tried running grub but keep coming up with errors. I am going do a search for it right now



As I stated in that initial thread I just got rid of I have Super Grub on one of my CD's Ultimate Boot CD I think and I had no luck at all, might have been doing something wrong??
 I have tried bcdedit, bootrec /fixmbr, diskpart you name it I believe I tried it. I must be missing something crutial, where I am writing it to /dev/sda or /dev/sda1 ???





this is whats happening when I run it 

grub> find /boot/grub/stage1

Error 15: File not found


grub> find /boot/grub       

Error 15: File not found

grub> find /boot/grub/stage2

Error 15: File not found



If I am running off a live CD are the commands I enter actually having any effect on my physical drives, or do I have to install Ubuntu to my hard drive again?

Now if the answer to that is yes I need to reinstall Ubuntu, then which partition should I install it to? Should I overwrite sda3 which is my UbuntuStudio64 and I really don't want it anyway or do I install it to available free space, or if in the course of the install when I have the ability to modify my partitions and I see that my backup of UbuntuStudio32 is still there do I delete every partition except for Vista and the first 200MiB in front of the Vista partition and install it to available free space or create an extended partition and make seperate partitions for home, boot, usr, etc, so I can move my copy of it later on. Is that 200MiB partition supposed to be set as bootable if in fact it is needed at all or does Vista have to be right at the beginning as partition #1. If you look at my screenshot from the past post it is not showing up, but on an install Gparted shows it, or if I run my Gpated CD it is there. Another thing is when I run my windows system recovery it can't even see it anymore, comes up blank, nothing in the list.

---

### Post by idoitprone on 2011-06-20
that script i made you ran created a file called

it can be any directory and be able to run

RESULTS.txt

put it under [CODE] tages
I suggest you put all command line output under code tags

One of the best back up software is clonezilla, its algorium only copies files that exist and not the whole entire partition


these are the steps to reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2)

nothingspecial is suggesting something else

---

### Post by JASONFUSARO on 2011-06-20
> **idoitprone said:**
> that script i made you ran created a file called

it can be any directory and be able to run

RESULTS.txt

put it under [CODE] tages
I suggest you put all command line output under code tags

One of the best back up software is clonezilla, its algorium only copies files that exist and not the whole entire partition


these are the steps to reinstall grub
[url]https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2[\url]

nothingspecial is suggesting something else




I have clonezilla on CD, but it tells me the option I want to run is only available on the purchased version??

I did not run it, I downloaded it and have it stored, don't have a clue as to where to run it from, terminal, like a batch file at boot up, or some other way


and I ran those other commands but I still come up to a black screen at reboot. I don't believe these command are having any effect at all when I am running of a live CD??

---

### Post by JASONFUSARO on 2011-06-20
> **idoitprone said:**
> that script i made you ran created a file called

it can be any directory and be able to run

RESULTS.txt

put it under [CODE] tages
I suggest you put all command line output under code tags

One of the best back up software is clonezilla, its algorium only copies files that exist and not the whole entire partition


these are the steps to reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

nothingspecial is suggesting something else



read my post #29 man

---

### Post by idoitprone on 2011-06-20
[http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

well that is strange. It is **[SIZE="2"]free[/SIZE]** and opensource

about the bootscript?

I want to know which bootloader is in the mbr. So i can tell your options

you may want to see this link 

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2)

---

### Post by idoitprone on 2011-06-20
> **JASONFUSARO said:**
> read my post #29 man

the bootscript is a diagonsis tool. 

sample script

my computer info


 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       204800 sectors.. But according to the info from the 
                       partition table, it has 58587006 sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
 Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 318360105.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    58,589,054    58,587,007  39 Plan 9
/dev/sda2          58,589,055   318,360,104   259,771,050   5 Extended
/dev/sda5          58,589,118    64,452,779     5,863,662  82 Linux swap / Solaris
/dev/sda6          64,452,843   298,825,064   234,372,222  83 Linux
/dev/sda7         298,825,128   318,360,104    19,534,977  83 Linux
/dev/sda3         318,360,105   400,291,604    81,931,500   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0000-0992                              vfat       CYLINDRICAL
/dev/sda3        EDBE-ED61                              vfat       
/dev/sda5        c7017b07-3b32-44d1-ab61-dc62d81d630a   swap       
/dev/sda6        27266813-f3ae-49c9-a883-a3bbae6c8ef4   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,commit=600)


=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title Arch Linux
root (hd0,5)
kernel /boot/vmlinuz26-ck root=/dev/sda6 ro init=/bin/systemd
initrd /boot/kernel26-ck.img


# (0) Arch Linux
title Arch Linux
root (hd0,5)
kernel /boot/vmlinuz26-ck root=/dev/sda6 ro
initrd /boot/kernel26-ck.img

# (0) Arch Linux
title  Arch Linux
root   (hd0,5)
kernel /boot/vmlinuz26 root=/dev/sda6 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,5)
kernel /boot/vmlinuz26 root=/dev/sda6 ro
initrd /boot/kernel26-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

# (3) Plan9
title Plan9
rootnoverify (hd0,0)
makeactive
chainloader +1
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda5 swap swap defaults 0 0
/dev/sda6 / ext4 defaults 0 1
--------------------------------------------------------------------------------

======================= sda6/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
        MENU LABEL Arch Linux
        LINUX ../vmlinuz26
        APPEND root=/dev/sda3 ro
        INITRD ../kernel26.img

LABEL archfallback
        MENU LABEL Arch Linux Fallback
        LINUX ../vmlinuz26
        APPEND root=/dev/sda3 ro
        INITRD ../kernel26-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 118.968163967 = 127.741093376  boot/grub/menu.lst                             1
  54.861417294 = 58.906998272   boot/grub/stage2                               1
  31.546330929 = 33.872614912   boot/kernel26-ck-fallback.img                  1
  33.612096310 = 36.090713600   boot/kernel26-ck.img                           1
  72.073812008 = 77.388666368   boot/kernel26-fallback.img                     1
  72.006635189 = 77.316535808   boot/kernel26.img                              1
  54.860600948 = 58.906121728   boot/vmlinuz26                                 1
  54.869462490 = 58.915636736   boot/vmlinuz26-ck                              1

================= sda6: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

  54.915261745 = 58.964813312   boot/syslinux/syslinux.cfg                     1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 3c 90 50 6c 61 6e 39  2e 30 30 00 02 04 02 00  |.<.Plan9.00.....|
00000010  02 00 02 00 00 f8 c8 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 80 00 29 92  09 00 00 43 59 4c 49 4e  |. ....)....CYLIN|
00000030  44 52 49 43 41 4c 46 41  54 31 36 20 20 20 fa 31  |DRICALFAT16   .1|
00000040  c0 8e d0 8e d8 8e c0 bc  ec 7b 89 e5 88 56 12 50  |.........{...V.P|
00000050  b8 55 7c 50 cb fb be e7  7d bf 96 7d ff d7 bf 88  |.U|P....}..}....|
00000060  7d ff d7 8b 06 27 7c 8b  16 29 7c bb 00 7e bf 32  |}....'|..)|..~.2|
00000070  7d ff d7 bb 10 00 bf 00  7e 57 be db 7d b9 0b 00  |}.......~W..}...|
00000080  f3 a6 5f 74 0e 4b 74 06  81 c7 20 00 eb eb bf 14  |.._t.Kt... .....|
00000090  7d ff d7 31 db 8b 06 11  7c b9 20 00 f7 e1 8b 0e  |}..1....|. .....|
000000a0  0b 7c 51 49 01 c8 11 da  59 f7 f1 50 8b 85 1a 00  |.|QI....Y..P....|
000000b0  48 48 8a 0e 0d 7c 30 ed  f7 e1 8b 0e 27 7c 01 c8  |HH...|0.....'|..|
000000c0  8b 0e 29 7c 11 ca 59 01  c8 11 da 50 52 8b 85 1c  |..)|..Y....PR...|
000000d0  00 8b 95 1e 00 8b 0e 0b  7c 51 49 01 c8 11 da 59  |........|QI....Y|
000000e0  f7 f1 89 c1 5a 58 bb 00  10 8e c3 bb 00 00 bf 32  |....ZX.........2|
000000f0  7d ff d7 8b 3e 0b 7c 01  fb 73 08 8c c7 81 c7 00  |}...>.|..s......|
00000100  10 8e c7 31 ff 40 11 fa  e2 e4 bf 00 10 8e df ea  |...1.@..........|
00000110  00 00 00 10 be a9 7d bf  96 7d ff d7 31 c0 cd 16  |......}..}..1...|
00000120  31 db 8e c3 bb 72 04 b8  34 12 26 89 07 ea 00 00  |1....r..4.&.....|
00000130  ff ff bf 05 00 60 53 8b  1e 18 7c 8b 3e 1a 7c 0f  |.....`S...|.>.|.|
00000140  af df 09 db 74 36 f7 f3  89 c1 c1 c1 08 c0 e1 06  |....t6..........|
00000150  89 d0 31 d2 8b 1e 18 7c  f7 f3 42 81 e2 3f 00 09  |..1....|..B..?..|
00000160  d1 89 c2 c1 e2 08 8a 56  12 5b b8 01 02 cd 13 73  |.......V.[.....s|
00000170  15 61 4f 74 07 bf 88 7d  ff d7 eb b9 be b7 7d bf  |.aOt...}......}.|
00000180  96 7d ff d7 eb 96 61 c3  60 31 c0 8a 56 12 cd 13  |.}....a.`1..V...|
00000190  08 e4 61 75 e7 c3 60 31  db ac 08 c0 74 09 b4 0e  |..au..`1....t...|
000001a0  cd 10 ac 08 c0 75 f7 61  c3 42 61 64 20 66 6f 72  |.....u.a.Bad for|
000001b0  6d 61 74 20 6f 72 20 49  2f 4f 20 65 72 72 6f 72  |mat or I/O error|
000001c0  0d 0a 50 72 65 73 73 20  61 20 6b 65 79 20 74 6f  |..Press a key to|
000001d0  20 72 65 62 6f 6f 74 2e  2e 2e 00 39 4c 4f 41 44  | reboot....9LOAD|
000001e0  20 20 20 20 20 20 00 50  42 53 31 2e 2e 2e 00 04  |      .PBS1.....|
000001f0  24 b8 02 00 00 00 89 44  24 04 e8 bb f3 f7 55 aa  |$......D$.....U.|
00000200

Unknown BootLoader on sda7

00000000  fc 97 fe c0 66 fd eb 73  68 e4 20 c8 b6 6a d4 1e  |....f..sh. ..j..|
00000010  e6 16 4d fe ce d2 94 97  e8 b9 77 7d 00 c1 25 eb  |..M.......w}..%.|
00000020  a4 94 bf 1b 6e d5 e3 66  39 fd 5d 09 14 1e 3e 50  |....n..f9.]...>P|
00000030  e8 0f 51 cf 97 43 f3 e2  d7 c0 66 b7 9d 3f 2c 48  |..Q..C....f..?,H|
00000040  cc 47 b1 0c 87 59 c4 76  75 f5 b9 36 0e a3 40 6a  |.G...Y.vu..6..@j|
00000050  69 87 82 ea 92 c2 b9 74  cf d5 d8 74 c2 f6 5e de  |i......t...t..^.|
00000060  70 8f db c8 32 28 d7 19  a2 33 c2 41 d0 7a b8 fa  |p...2(...3.A.z..|
00000070  94 45 68 02 8d 94 83 b3  19 ba 33 23 1d 3a 9b e3  |.Eh.......3#.:..|
00000080  ac ae 91 57 ba 3d 82 c9  71 3b 2a c0 db fa 26 ca  |...W.=..q;*...&.|
00000090  08 ef e6 c5 54 a9 5e 05  27 c5 4d ca d3 88 dc 52  |....T.^.'.M....R|
000000a0  c8 72 dc 43 ca e2 e3 fd  85 59 a6 d6 53 af 3e 31  |.r.C.....Y..S.>1|
000000b0  96 4b 03 58 7b ba 12 27  cc 27 95 a6 26 ac 08 84  |.K.X{..'.'..&...|
000000c0  f3 27 d8 80 de 59 e4 98  d1 19 2d df d0 c3 5a 04  |.'...Y....-...Z.|
000000d0  56 66 fd 1c c4 fa 20 19  c4 59 01 fe b4 63 0a 7c  |Vf.... ..Y...c.||
000000e0  a7 fd 9b 45 fc c7 35 e4  d5 4e 3a 15 4f 9a 2f 48  |...E..5..N:.O./H|
000000f0  75 08 1c 13 3d 65 83 f0  36 d0 96 ac d8 c2 19 d7  |u...=e..6.......|
00000100  e2 20 a4 09 d4 d3 d3 d3  40 5c 7e 76 fb 53 1d f1  |. ......@\~v.S..|
00000110  90 71 a4 29 b3 7c 87 6e  23 84 06 08 f6 2c 8f 50  |.q.).|.n#....,.P|
00000120  2f 35 31 4b e6 ba dd 32  ab 3c 2a b3 09 c6 a0 28  |/51K...2.<*....(|
00000130  eb f1 3d bc 13 db f2 fe  d0 a4 fc 79 6b 9a 59 b2  |..=........yk.Y.|
00000140  f1 aa 14 ec e1 e4 66 ea  c5 01 9a 33 c1 fe 00 df  |......f....3....|
00000150  f4 39 8f 07 63 4a bf 8b  b0 d5 3d f0 75 1d 18 1f  |.9..cJ....=.u...|
00000160  2b 70 57 b6 34 44 09 83  62 20 c5 2e 07 c2 1c 55  |+pW.4D..b .....U|
00000170  e5 b5 60 6f 4b b5 75 89  04 56 0d 61 5e b3 ae 2c  |..`oK.u..V.a^..,|
00000180  74 ef 89 ad 4f 4f a6 4d  65 b0 0f 81 ec df 5b 03  |t...OO.Me.....[.|
00000190  dd 98 fb 39 2f 9c 35 14  aa 61 2b a5 90 df d3 27  |...9/.5..a+....'|
000001a0  c4 3d 38 24 f8 f6 14 22  3c a9 ac 9d 43 27 e8 7f  |.=8$..."<...C'..|
000001b0  a8 93 e9 d9 f7 86 9f 83  d0 80 4d 58 ee d7 1d 9a  |..........MX....|
000001c0  26 50 02 03 57 46 53 c0  7f 11 85 88 6e 73 af fe  |&P..WFS.....ns..|
000001d0  28 d6 88 1c 9a db 8e 60  0a fc 77 c5 ef bd 46 8c  |(......`..w...F.|
000001e0  fa e0 ca 97 aa 8b 2d 9c  f9 5a 47 1c c5 e0 eb 28  |......-..ZG....(|
000001f0  80 f5 bf 3f 97 e2 3a ad  32 90 e4 ff 59 02 ea 24  |...?..:.2...Y..$|
00000200


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda3: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
  No volume groups found
mdadm: No arrays found in config file or automatically

```

this is what i want

---

### Post by JASONFUSARO on 2011-06-20
> **JASONFUSARO said:**
> read my post #29 man



That boot info script appears mighty useful but I don't know if it will even run because I am not booting from my hard drive.

this is the output from fdisk and I am at that site right now. It gets kinda confusing when I am trying stuff and I come back and your onto somtething else it is not systematic and I am getting a little confused because I don't know if you are getting all my replys??? in the order I am replying??


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x532e7c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       11452    91778048    7  HPFS/NTFS
/dev/sda3           11452       15604    33348608   83  Linux
/dev/sda4           15604       60802   363058542    f  W95 Ext'd (LBA)
/dev/sda5           15604       21289    45665280   83  Linux
/dev/sda6           21289       24476    25600000   83  Linux
/dev/sda7           24477       25918    11582824   82  Linux swap / Solaris


ubuntu@ubuntu:~$ df -th
df: no file systems processed



should I be trying to modify my sda1 partition or sda2?? Where does it have to go, does grub have to be there along with an MBR when I get one there?? I am confused, sda2 has windows sda 3 etc have Linux and sda1 is that small space up front which appears to be screwed up?? Where am I trying to fix it that is what I need to understand from what I have read I am still confused, I guess because of the dual boot option.


ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt


ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/boot


ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

so far so good and just when I think hey success!

ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: failed to run command `/bin/bash': Exec format error

this crap happens!!!!!!!!!!!

now what that page does not assume it might not work and now I am back in the dark, and what has happened since the other commands worked and this didn't has it thrown my system into deeper chaos???  This ain't fun anymore.


Those first couple of days I was really liking Linux, but now ?????


what the hell
I figure one more command can't do any more damage 

ubuntu@ubuntu:~$ update-grub
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
/usr/sbin/grub-set-default: 124: cannot create /boot/grub/default: Permission denied
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
/usr/sbin/update-grub: line 1094: /boot/grub/menu.lst: Permission denied


Now what does all this mean, like I said in that first Thread post I deleted, this crap has been happening without fail one thing after another, something ain't right, is this why all that software is for free, repayment for the pain and agony of commands that don't work, I mean windows was bad but I don't know how much more of this I can endure???


Please help!!!!!!

---

### Post by JASONFUSARO on 2011-06-20
ubuntu@ubuntu:~$ sudo apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
/dev/sda1: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda2
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda3
Could not find device for /boot: Not found or not a block device.

---

### Post by idoitprone on 2011-06-20
the reason why the boot script is so dawm useful is that you dont have to run it from your harddrive. An live usb will do.

You have to mount the partition to install grub.

Please refrain from posting random commands, since you are diluting my efforts.

---

### Post by JASONFUSARO on 2011-06-20
ubuntu@ubuntu:~$ sudo apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
/dev/sda1: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda2
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda3
Could not find device for /boot: Not found or not a block device.





ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: special device /dev/sda1 does not exist
ubuntu@ubuntu:~$ sudo apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
/dev/sda1: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda2
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda3
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
mkdir: cannot create directory `/mnt/root': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda5 /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda6 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/rot/dev
mount: mount point /mnt/rot/dev does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
bash-4.2# sudo grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97-71.fc15  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]



again everything apppears to have run pretty smooth and then



grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find stage1
find stage1

Error 15: File not found
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> root (hd0,5)
root (hd0,5)

Error 21: Selected disk does not exist
grub> root (hd0,6)
root (hd0,6)

Error 21: Selected disk does not exist
grub> root (hd0,7)
root (hd0,7)

Error 21: Selected disk does not exist
grub>

---

### Post by JASONFUSARO on 2011-06-20
Well I think I'll try a reboot, see if any of those commands have helped me out. Then I think I'll run Gparted and wipe out some stuff on my drive if I can't boot, then I'll take it from there, I am getting pretty close to a reinstall, which I really don't wan't to do

---

### Post by idoitprone on 2011-06-20
oh well, i guess i have to do it blind. I am not sure if this will work, since i am unable to verify that ubuntustudio32 has grub2
```
sudo mount /dev/sda5 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```

when you boot into ubuntu studio

do yourself a favor

```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by jtarin on 2011-06-20
If I may.....is this all being done from a LiveCD?

---

### Post by idoitprone on 2011-06-20
> **jtarin said:**
> If I may.....is this all being done from a LiveCD?

i dont know what is going on with the op. Apperently, he was doing this from a gparted live cd and ubuntu cd does not work. I know it baffles me, since he was able to install a system. His tendency on giving uneeded information, while not disclosing the required information is a little difficult to manage.

---

### Post by jtarin on 2011-06-20
I don't want to butt in and derail diagnostics but this thread has gone on for several pages with little coherency...to my mind, so I thought maybe a fresh perspective might make a little difference. To the OP....your input is greatly appreciated and you have done an excellent job of providing info, but it would help us to help you if you could stay on track and as confusing as it might seem at times try to acknowledge with a response of some kind when a question is directed at you. I for one am busy helping many other people as I am sure these other responders are....so time is valuable to all concerned here.

---

### Post by JASONFUSARO on 2011-06-21
> **jtarin said:**
> If I may.....is this all being done from a LiveCD?

Lets try and start over.

 
Yes it is being done from a live CD. I cannot boot my PC. When I boot my PC all I get is a black screen and a flashing cursor. 

The only way I can access the internet and logon here and post is to  run off a CD, be it Fedora, Ultimate boot CD, which I am using now running PartedMagic Linux Kernel: version 2.6.32.11-pmagic. I also have another CD which is another version that is newer. I have Fedora on CD, Ubuntu 11.04 on CD, UbuntuStudio on CD, MBRtool on CD.

Problem 1

When I view Gparted it shows me an unallocated drive (GpartedSS1.png) yet my documents window manager clearly can see partition data my directories are in fact there and intact (FilemanagerSS2.png).

I have run TestDisk numerous times and write the Partition and MBR information to the hard drive but this appears to do nothing to correct the problem?

(TestDiskSS3.png - TestDiskSS6.png)

Partition Image (PartImage.png) I have no clue as to those loop1 and loop2??


DAMN!!! Max 5 uploads


Problem 2

When I run my Windows Vista it tells me it corrected the Partition problem but the next time I reboot same Black screen and flashing cursor.


Problem 3


When I run any of the suggested terminal commands that are posted most of them end up not working or working partially, which tends to complicate the problem because then I have no clue as to whether or not those commands have deepened the chaos on my system? Why they crap out or do not run as explained in the help posts I have no idea. Is it because I am not actually on my hard drive and the commands are modifying the live environment???

Trying to figure out in what order and which help posts to try gets rather confusing, in which order do I run them? Help is coming from multiple people, which thread do I follow? 

It would be much simpler if one person took over, looked at my current situation, asked me to do something, looked at the result of that and then proceed from there, this would be more systematic. I believe I am just complicating the problem by trying all sorts of things in a haphazard manner. 

Another problem is that I am not sure if I am supposed to post what I do with regards to someones help in that particular post as a quote or as a separate entry and this is just confusing everyone even more. I have posted my results of entering terminal commands but I think that is not working to well.

Second it would be better if the person helping was actually online as if we were talking on the phone so it would be a walkt-hrough but this i not always possible.


I would rather have someone give me a list to try and determine where my system stands so I can try something in list fashion.

That is what I was trying to get across in my apparent previous ramblings which now I realize I should not have done.

No one responded to post#38 and explained why that did not work or other posts. I f I try a command and it doesn't work why hasn't anyone taken a look at it and tried to figure out what's going on. Should I start the post in a more informative manner and give an account like I ran this command as per instructions given in post#xx so it would make more sense in following the thread. Please bear with me and I apologize greatly I have only recently started online postings, and don't quite have the correct protocol down.

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> Lets try and start over.

 No one responded to post#38 and explained why that did not work or other posts. I f I try a command and it doesn't work why hasn't anyone taken a look at it and tried to figure out what's going on. Should I start the post in a more informative manner and give an account like I ran this command as per instructions given in post#xx so it would make more sense in following the thread. Please bear with me and I apologize greatly I have only recently started online postings, and don't quite have the correct protocol down.


i did take a look. You are doing the commands wrong. You have either mount the incorrect drive, or used the wrong commands. grub needs a host partition and sda1 or 2 are not host partition, since they do not contain grub or grub2. I am doing it blind and assume that ubuntu studio has grub2 because i never saw the boot script. I can tell you how to tell but using  commands individually is longer than the bootscript

Did you try the commands I gave you @ post 40? That should link to the Ubuntustudio partion.
I try to make the steps simple, but apparently near copy paste commands are not enough.


all the commands i gave are not harmful, they are diagonsis tools except post 40 which is meant to fix the problem. The commands that you had used with consulting me.... thats a different story

---

### Post by JASONFUSARO on 2011-06-21
> **jtarin said:**
> I don't want to butt in and derail diagnostics but this thread has gone on for several pages with little coherency...to my mind, so I thought maybe a fresh perspective might make a little difference. To the OP....your input is greatly appreciated and you have done an excellent job of providing info, but it would help us to help you if you could stay on track and as confusing as it might seem at times try to acknowledge with a response of some kind when a question is directed at you. I for one am busy helping many other people as I am sure these other responders are....so time is valuable to all concerned here.




I apologize for appearing as somewhat of a nitwit, but do I post my response to a question in that question as a quote (ie. selecting quote like I have just done) or as another post? Is this what I have been doing wrong and is causing confusion? I am failing to understand why the directed questions posed by helpers to try something, at which point I try it, and post the output from what was done and then I seem to get no response as to why the command that was asked to try has not worked, and believe me 9 times out of ten they don't, this is really starting to drive me nuts I have been at this for a couple of days and I am just on the verge of starting all over, and reinstalling everything, which if I would have done a couple of days ago would and I would have already been back in business, instead of trying to salvage all my Vista updates that got me up to Sp2 which took some time and all my downloads in UbuntuStudio32 which was set up pretty good, I had Virtualbox running again with Vista and a couple of other packages, I had my camera working, scanner working, printer working. It sucks thinking I have to do it all over again. They are they on my hard drive, but I can't boot into it. I can copy them to my other 500GiB USB but have no clue as to moving them back after a reinstall, I have been reading and Google Linux directory structure, /Home appears to be able to be saved and copied back but I am not understanding whether or not information in /usr or some other directory is tied into this and also has to be saved along with it in order to allow it to function when copied back into another Distro or if the /Home/Jason only will do the trick?  Another thing that I have been trying to read up on is whether or not there in fact needs to be a small Primary partition created at the start of the drive for storing the MBR and then Vista and then Linux Swap then Extended Partition with my  Linux Distros. Does that first partition have to be primary bootable I have made it so and when I try to restore Vista it comes up on as X: and not C: and if I make the Vista partition bootable Vista restore can't recognize any drives they come up empty? So I figure it's some sort of MBR problem, but when I run Testdisk and write the partition and MBR to disk and reboot it solves nothing. I  can't get GRUB to work off the Ultimate Boot CD I select either Grub1 or Grub2 and I get error messages Gparted shows my Hard Drive as being unallocated yet file manager shows my drive structure and I can access them from it. The other drive software which for some reason isn't working in this version of parted magic  also shows the setup and has them all there in the extended partition, but when I select them it can't access them to give me any information I can't recall it's name but it's not in this version of parted magic's system tools or accessories list and it is in the other version which I should have run instead.

Again I appologize
Jason

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> i did take a look. You are doing the commands wrong. You have either mount the incorrect drive, or used the wrong commands. grub needs a host partition and sda1 or 2 are not host partition, since they do not contain grub or grub2. I am doing it blind and assume that ubuntu studio has grub2 because i never saw the boot script. I can tell you how to tell but using  commands individually is longer than the bootscript

Did you try the commands I gave you @ post 40? That should link to the Ubuntustudio partion.
I try to make the steps simple, but apparently near copy paste commands are not enough.


all the commands i gave are not harmful, they are diagonsis tools except post 40 which is meant to fix the problem. The commands that you had used with consulting me.... thats a different story


Hello,

Sorry for driving you nuts

I just ran it and this is what I got

Welcome - Parted Magic (Linux 2.6.32.11-pmagic)
Most of the filesystem tools and partition programs featured by Parted Magic
include man pages.  To read a manual page,  simply type man and
the name of the tool. (Examples: 'man ntfsprogs' or 'man fdisk')

root@PartedMagic:~# mount /dev/sda5 /mnt
root@PartedMagic:~# grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-install: line 291: grub-mkdevicemap: command not found
sed: can't read /mnt/boot/grub/device.map: No such file or directory
grub-probe: error: Cannot open `/mnt/boot/grub/device.map'
root@PartedMagic:~# 


I tried it with su and sudo but it failed to run

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
>  I  can't get GRUB to work off the Ultimate Boot CD I select either Grub1 or Grub2 and I get error messages Gparted shows my Hard Drive as being unallocated yet file manager shows my drive structure and I can access them from it. The other drive software which for some reason isn't working in this version of parted magic  also shows the setup and has them all there in the extended partition, but when I select them it can't access them to give me any information I can't recall it's name but it's not in this version of parted magic's system tools or accessories list and it is in the other version which I should have run instead.

Again I appologize
Jason

Like I said there is software that will tell you why, boot script. Since grub is already messed try the commands in post40, if you had used an up to date version of ubuntu studio

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> Like I said there is software that will tell you why, boot script. Since grub is already messed try the commands in post40, if you had used an up to date version of ubuntu studio





First of all. What should I be working from UbuntuStudio Live or anywhere? I am running Gparted because I was trying TestDisk again to see if I can get my MBR back in order for the umpteenth time. Should I get out of this and run UbuntuStudio ??

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> Hello,

Sorry for driving you nuts

I just ran it and this is what I got

Welcome - Parted Magic (Linux 2.6.32.11-pmagic)
Most of the filesystem tools and partition programs featured by Parted Magic
include man pages.  To read a manual page,  simply type man and
the name of the tool. (Examples: 'man ntfsprogs' or 'man fdisk')

root@PartedMagic:~# mount /dev/sda5 /mnt
root@PartedMagic:~# grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-install: line 291: grub-mkdevicemap: command not found
sed: can't read /mnt/boot/grub/device.map: No such file or directory
grub-probe: error: Cannot open `/mnt/boot/grub/device.map'
root@PartedMagic:~# 

let me see the version of grub did you use,

```
grub-install --version
```

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> let me see the version of grub did you use,

```
grub-install --version
```



Again thank you for being patient with me and thanks for the help

root@PartedMagic:~# grub-install --version
grub-install (GNU GRUB 0.97)


what is the reasoning behind Quote, Multi Quote and quick reply, Stupid Question #1

Is it possible to have this screen update or is there some button somewhere or do I have to keep going to page 5 then back to this page to check if it has been updated   Stupid Question #2

---

### Post by idoitprone on 2011-06-21
Awww dawm it, no wonder it did not work. you have grub legacy. Assuming you did not change grub on fedora, I am tell you how to boot there and fix things from there ok

I going to take time to write a post

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> Awww dawm it, no wonder it did not work. you have grub legacy. Assuming you did not change grub on fedora, I am tell you how to boot there and fix things from there ok

I going to take time to write a post


Should I Be running of another CD ?????? Should I reboot and do that?????

There are two copies one on sda6 and another sda8 look at the screenshot why I could not start to tell you I have tried so many different things already

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> Should I Be running of another CD ?????? Should I reboot and do that?????
No that cd is fine. You have fedora that still uses grub legacy. I am going to use that information to fix your grub. If that does not work, I will consider using another cd


```
sudo -s

grub

find /boot/grub/stage1

root (hd0,1) ## note change to the corresponding output to the find stage 1 command

setup (hd0)

quit
```and boot to fedora if it still exist. From there i will tell you commands to make ubuntu studio the primary partition

method 2
at grub rescue
```
root  (hd0,5)
chainloader +1
boot
```I am going in blind and assuming fedora is on sda6

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> No that cd is fine. You have fedora that still uses grub legacy. I am going to use that information to fix your grub. If that does not work, I will consider using another cd


```
sudo -s

grub

find /boot/grub/stage1

root (hd0,1) ## note change to the corresponding output to the find stage 1 command

setup (hd0)

quit
```and boot to fedora if it still exist. From there i will tell you commands to make ubuntu studio the primary partition

method 2
at grub rescue
```
root  (hd0,5)
chainloader +1
boot
```I am going in blind and assuming fedora is on sda6








root@PartedMagic:~# grub-install --version
grub-install (GNU GRUB 0.97)
root@PartedMagic:~# -s
sh: -s: command not found
root@PartedMagic:~# sudo -s
sh: sudo: command not found
root@PartedMagic:~# su -s
su: option requires an argument -- 's'
BusyBox v1.16.1 (2010-04-03 12:59:14 CDT) multi-call binary.

Usage: su [OPTIONS] [-] [USERNAME]

Change user id or become root

Options:
	-p,-m	Preserve environment
	-c CMD	Command to pass to 'sh -c'
	-s SH	Shell to use instead of default shell

root@PartedMagic:~# 


can't even get past the first point


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub>


I can't boot remember, do you mean put the fedora CD in and go from there or run Ultimate Boot CD and select boot from sda6 or sda8?????




grub> root (hd0,5)
 Filesystem type is ext2fs, partition type 0x83


One other thing, I have a habit of going back into posts and adding to them have you noticed if not just letting you know I may have added something in between our posts   Stupid Addition #1



it is on sda6 I took a screenshot, take a look

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> root@PartedMagic:~# grub-install --version
grub-install (GNU GRUB 0.97)
root@PartedMagic:~# -s
sh: -s: command not found
root@PartedMagic:~# sudo -s
sh: sudo: command not found
root@PartedMagic:~# su -s
su: option requires an argument -- 's'
BusyBox v1.16.1 (2010-04-03 12:59:14 CDT) multi-call binary.

Usage: su [OPTIONS] [-] [USERNAME]

Change user id or become root

Options:
    -p,-m    Preserve environment
    -c CMD    Command to pass to 'sh -c'
    -s SH    Shell to use instead of default shell

root@PartedMagic:~# 


can't even get past the first point

skip the first command

you are already root

---

### Post by idoitprone on 2011-06-21
```
wget http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download

unzip boot_info_script060.zip 

chmod u+x boot_info_script.sh 

./boot_info_script.sh

cat RESULTS.txt
```post results

just copy paste the commands

i gone far enough fixing your computer blind. Now i actually need information

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> ```
wget http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download

unzip boot_info_script060.zip 

chmod u+x boot_info_script.sh 

./boot_info_script.sh

cat RESULTS.txt
```post results

just copy paste the commands

i gone far enough fixing your computer blind. Now i actually need information



I already have that downloaded, I have it on my flash drive, was reading up on how to run the script, when I tried to run bash it was't there so I tried to install it with apt-get and all kinds of other commands to no avail!!


I do need bash to run the script correct?


also I took a screenshot of my directory list from filemanager and added it ti the post, I don't know if you took another look at that post because as I said I have a habit of modifying previous posts and am not sure whether this confuses the issue?

---

### Post by JASONFUSARO on 2011-06-21
root@PartedMagic:~# wget [http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download)
Connecting to sourceforge.net (216.34.181.60:80)
Connecting to downloads.sourceforge.net (216.34.181.59:80)
Connecting to cdnetworks-us-1.dl.sourceforge.net (174.35.19.11:80)
download             100% |*******************************| 34401  --:--:-- ETA
root@PartedMagic:~# unzip boot_info_script060.zip
unzip:  cannot find or open boot_info_script060.zip, boot_info_script060.zip.zip or boot_info_script060.zip.ZIP.
root@PartedMagic:~# chmod u+x boot_info_script.sh 
chmod: boot_info_script.sh: No such file or directory
root@PartedMagic:~# 


man I hate when some things work and others don't

---

### Post by spynappels on 2011-06-21
Bash is the shell you use when using the terminal. It is installed by default, but is not a command.

---

### Post by idoitprone on 2011-06-21
yep you use the command like usual

you have to be in the driectory and add execute permissions
and also you are require to unzip it

chmod is a command that changes permission.
unzip is pretty obvious


i wrote it  to get rid of the obvious minor errors

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> root@PartedMagic:~# wget [http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download)
Connecting to sourceforge.net (216.34.181.60:80)
Connecting to downloads.sourceforge.net (216.34.181.59:80)
Connecting to cdnetworks-us-1.dl.sourceforge.net (174.35.19.11:80)
download             100% |*******************************| 34401  --:--:-- ETA
root@PartedMagic:~# unzip boot_info_script060.zip
unzip:  cannot find or open boot_info_script060.zip, boot_info_script060.zip.zip or boot_info_script060.zip.ZIP.
root@PartedMagic:~# chmod u+x boot_info_script.sh 
chmod: boot_info_script.sh: No such file or directory
root@PartedMagic:~# 


man I hate when some things work and others don't

yep i do
type 

```
ls
```i wonder if it even there

try to get the usb you have the script. I guess we have to use that

unzip add excute permission and etc and run it

---

### Post by JASONFUSARO on 2011-06-21
> **JASONFUSARO said:**
> I already have that downloaded, I have it on my flash drive, was reading up on how to run the script, when I tried to run bash it was't there so I tried to install it with apt-get and all kinds of other commands to no avail!!


I do need bash to run the script correct?


also I took a screenshot of my directory list from filemanager and added it ti the post, I don't know if you took another look at that post because as I said I have a habit of modifying previous posts and am not sure whether this confuses the issue?





Finally done something right!!!!!


Hope this helps



Man I can't attach it wait let me save it to my flash so I don't lose it

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> Finally done something right!!!!!


Hope this helps



Man I can't attach it wait let me save it to my flash so I don't lose it


fixing your system blind is really difficult. OH you did not know bash was built in to linux. When you graphic card is not working properly the beauty of linux is that. It defaults to the shell so you can still fix your system

---

### Post by JASONFUSARO on 2011-06-21
> **JASONFUSARO said:**
> Finally done something right!!!!!


Hope this helps



Man I can't attach it wait let me save it to my flash so I don't lose it



I hope this is SUCCESSFUL dude!!!!
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda6 and looks at sector 346555376 of the 
                       same hard drive for the stage2 file.  A stage2 file is 
                       at this location on /dev/sda.  Stage2 looks on 
                       partition #6 for /boot/grub/menu.lst.
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of 
                       sda11 and looks at sector 920564064 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda11,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of 
                       sda12 and looks at sector 920564064 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda11,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda12,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   b W95 FAT32
/dev/sda2             411,648   183,967,743   183,556,096   7 NTFS / exFAT / HPFS
/dev/sda3         183,969,792   250,667,007    66,697,216  83 Linux
/dev/sda4         250,667,046   976,784,129   726,117,084   f W95 Extended (LBA)
/dev/sda5         250,669,056   341,999,615    91,330,560  83 Linux
/dev/sda6         342,001,664   393,201,663    51,200,000  83 Linux
/dev/sda7         393,207,003   416,372,634    23,165,632  82 Linux swap / Solaris
/dev/sda8         429,737,984   480,937,983    51,200,000  83 Linux
/dev/sda9         480,953,970   608,863,497   127,909,528  83 Linux
/dev/sda10        647,804,928   717,547,519    69,742,592  83 Linux
/dev/sda11        728,395,776   843,628,543   115,232,768  83 Linux
/dev/sda12        861,538,304   976,771,071   115,232,768  83 Linux

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7969 MB, 7969177600 bytes
126 heads, 10 sectors/track, 12353 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    15,564,799    15,556,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/sda1        3771-1537                              vfat       HDstartArea
/dev/sda10       bb3ba6a0-3a7a-4676-b0d0-89359b5d98bb   ext3       Home2
/dev/sda11       393c5b0e-153a-4aed-bd6b-e17689558783   ext4       
/dev/sda12       393c5b0e-153a-4aed-bd6b-e17689558783   ext4       
/dev/sda2        0E5A6700395DFEEF                       ntfs       WindowsVista
/dev/sda3        03cf3622-a18f-47c4-94d0-9b7c887f0411   ext4       UbuntuStu64Bit
/dev/sda5        234cd951-aed4-4866-b85a-c28ae4020598   ext4       UbuntuStudio32
/dev/sda6        b06bbdc9-7a7f-47a4-8fc7-9e09f9960319   ext4       _Fedora-15-i686-
/dev/sda7        c5a5b515-db58-4706-b2d4-53379a5a27e7   swap       
/dev/sda8        b06bbdc9-7a7f-47a4-8fc7-9e09f9960319   ext4       _Fedora-15-i686-
/dev/sda9        234cd951-aed4-4866-b85a-c28ae4020598   ext4       UbuntuStudio32
/dev/sdb1        426C23CB6C23B895                       ntfs       SoftwareDesign

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/unionfs/usr         squashfs   (rw)
/dev/loop1       /lib/unionfs/firmware    squashfs   (rw)
/dev/loop2       /lib/unionfs/modules     squashfs   (rw)
/dev/sda2        /media/sda2              fuseblk    (rw,allow_other,blksize=4096)
/dev/sda5        /mnt                     ext4       (rw)
/dev/sda6        /media/sda6              ext4       (rw)
/dev/sda8        /media/sda8              ext4       (rw)
/dev/sdb1        /media/sdb1              fuseblk    (rw,allow_other,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
	initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0605b3b1-32d5-4267-9880-2cfcd39edf52 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  89.217445374 = 95.796502528   boot/grub/core.img                             1
  89.209972382 = 95.788478464   boot/grub/grub.cfg                             1
 101.195255280 = 108.657577984  boot/initrd.img-2.6.38-10-generic              2
  97.216609955 = 104.385540096  boot/initrd.img-2.6.38-8-generic               2
  97.090164185 = 104.249769984  boot/vmlinuz-2.6.38-10-generic                 2
  89.215705872 = 95.794634752   boot/vmlinuz-2.6.38-8-generic                 12
 101.195255280 = 108.657577984  initrd.img                                     2
  97.216609955 = 104.385540096  initrd.img.old                                 2
  97.090164185 = 104.249769984  vmlinuz                                        2
  89.215705872 = 95.794634752   vmlinuz.old                                   12

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
	initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=234cd951-aed4-4866-b85a-c28ae4020598  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=25582a6f-ef0c-4eac-b9cc-a9696d67658d  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults             0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sdf1                                  /media/sdf1  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  ntfs  defaults             0  0  
/dev/sda7                                  /media/sda7  ext3  defaults             0  0  
/dev/sda8                                  /media/sda8  swap  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  
/dev/sde1                                  /media/sde1  ntfs  defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs  defaults             0  0  
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 151.654991150 = 162.838306816  boot/grub/core.img                             1
 151.670066833 = 162.854494208  boot/grub/grub.cfg                             1
 138.283622742 = 148.480909312  boot/initrd.img-2.6.38-8-generic               2
 119.731750488 = 128.560988160  boot/vmlinuz-2.6.38-8-generic                  1
 138.283622742 = 148.480909312  initrd.img                                     2
 119.731750488 = 128.560988160  vmlinuz                                        1

========================== sda6/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-32.fc15.i686)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.38.8-32.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.38.8-32.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img
title BootLoader
	rootnoverify (hd0,0)
	chainloader +1
title Other
	rootnoverify (hd0,1)
	chainloader +1
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jun 18 19:39:25 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 /                       ext4    defaults        1 1
UUID=a1008bd3-7fb2-493e-9d0c-fcb1edd512f8 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.206275940 = 177.388888064  boot/grub/grub.conf                            1
 165.206275940 = 177.388888064  boot/grub/menu.lst                             1
 165.250598907 = 177.436479488  boot/grub/stage2                               1
 165.248336792 = 177.434050560  boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img   1
 165.500976562 = 177.705320448  boot/initramfs-2.6.38.8-32.fc15.i686.img       2
 164.326065063 = 176.443768832  boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686         1
 165.475181580 = 177.677623296  boot/vmlinuz-2.6.38.8-32.fc15.i686             1

========================== sda8/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-32.fc15.i686)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.38.8-32.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.38.8-32.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img
title BootLoader
	rootnoverify (hd0,0)
	chainloader +1
title Other
	rootnoverify (hd0,1)
	chainloader +1
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jun 18 19:39:25 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 /                       ext4    defaults        1 1
UUID=a1008bd3-7fb2-493e-9d0c-fcb1edd512f8 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 207.042213440 = 222.309883904  boot/grub/grub.conf                            1
 207.042213440 = 222.309883904  boot/grub/menu.lst                             1
 207.044155121 = 222.311968768  boot/grub/stage2                               1
 207.084274292 = 222.355046400  boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img   1
 207.336914062 = 222.626316288  boot/initramfs-2.6.38.8-32.fc15.i686.img       2
 206.162002563 = 221.364764672  boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686         1
 207.311119080 = 222.598619136  boot/vmlinuz-2.6.38.8-32.fc15.i686             1

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos9)'
	search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
	initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=234cd951-aed4-4866-b85a-c28ae4020598  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=25582a6f-ef0c-4eac-b9cc-a9696d67658d  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults             0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sdf1                                  /media/sdf1  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  ntfs  defaults             0  0  
/dev/sda4                                  /media/sda4  ext4  defaults             0  0  
/dev/sda8                                  /media/sda8  swap  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  
/dev/sde1                                  /media/sde1  ntfs  defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs  defaults             0  0  
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 261.463398933 = 280.744186880  boot/grub/core.img                             1
 261.478470802 = 280.760370176  boot/grub/grub.cfg                             1
 248.092026711 = 266.386785280  boot/initrd.img-2.6.38-8-generic               2
 229.540154457 = 246.466864128  boot/vmlinuz-2.6.38-8-generic                  1
 248.092026711 = 266.386785280  initrd.img                                     2
 229.540154457 = 246.466864128  vmlinuz                                        1

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```





[COLOR="DarkOrange"]WOULD REALLY APPRECIATE A RUNDOWN ON IMPORTANT THINGS TO LOOK FOR SO I CAN HANDLE IT AT ANY FUTURE POINT IN TIME THAT I MAY HAVE TO GO IT ALONE!!!![/COLOR]


HIGHLIGHT IMPORTANT CRUCIAL THINGS THAT I NEED TO LOOK FOR

---

### Post by idoitprone on 2011-06-21
this explain a whole lot. sighhhh.... only if i had the information sooner.

What was the last operating system you install because some of the grub do not have the proper entries

I may have you maunally edit some of the entries

First let take a look a solution that is less work arrrg. Lots and lots of problems all over

---

### Post by JASONFUSARO on 2011-06-21
Ain't heard from you? Maybe you dove right into that mess and can't find your way back out????

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> this explain a whole lot. sighhhh.... only if i had the information sooner.

What was the last operating system you install because some of the grub do not have the proper entries

I may have you maunally edit some of the entries

First let take a look a solution that is less work arrrg. Lots and lots of problems all over



yea I know


I kept trying stuff and now I have a ton of stuff on top.

Last thing I installed was Fluxbox, which gave a whole lot of error messages when it was downloading packages, I kept hitting the return key, like as quick as a rabbit.


Why Fedora is there twice I have no clue.  


Also there are two loop directories Loop1 and Loop2 I can see them in TestDisk I think, not sure seen them somewhere, and have no clue what put them there best guess is Fluxbox


also way back when, I had UbuntuStudio64 and wanted to change to UbuntuStudio32 it wasn't working so like an idiot or is it idoit I copied it from nother home directory figuring it would use it instead and that may have started the ball rolling into this big giant piece of a Dung Ball that I have now.


I could just wipe everything out and start from scratch and have this lesson under my belt?? Rather than keep bothering you unless you enjoy cracking major problems??


with each install I thought I could fix the partitioning problem and it would square away the MBR but I think each link just did the opposite

---

### Post by goldshirt9 on 2011-06-21
if i were you i would [COLOR=Red]wait and do nothing[/COLOR] until idoitprone comes back with a solution.
[COLOR=Black]you may only make the problem worse ;)[/COLOR]

---

### Post by idoitprone on 2011-06-21
ok the only sensible solution i find is to get a cd that has grub 2, get another live cd try that ubuntu studio disk, even if it does not have a graphical console

your fedora installation is broken and i will have to manually fix your bootloader and check your uuids and fstab; however your ubuntu intallation still seems good.

first
use another live cd even if you do not get an graphical console and had to use the command line it will be fine

then
check which version
use it only if it is 1.97 and up
grub-install --version

use these commands again


```
sudo mount /dev/sda5 /mnt
  sudo grub-install --root-directory=/mnt /dev/sda
```

you do not need sudo if your are root
to check 

```
whoami
```

---

### Post by JASONFUSARO on 2011-06-21
> **goldshirt9 said:**
> if i were you i would [COLOR=Red]wait and do nothing[/COLOR] until idoitprone comes back with a solution.
[COLOR=Black]you may only make the problem worse ;)[/COLOR]




Yea, I am browsing the listing

thanks for keeping me put, I do get tempted to go it alone.

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> ok the only sensible solution i find is to get a cd that has grub 2, get another live cd try that ubuntu studio disk, even if it does not have a graphical console

your fedora installation is broken and i will have to manually fix your bootloader and check your uuids and fstab; however your ubuntu intallation still seems good.

first
use another live cd even if you do not get an graphical console and had to use the command line it will be fine

then
check which version
use it only if it is 1.97 and up
grub-install --version

use these commands again


```
sudo mount /dev/sda5 /mnt
  sudo grub-install --root-directory=/mnt /dev/sda
```

you do not need sudo if your are root
to check 

```
whoami
```

do I check the CD before install or after. Second do I run it as an install or am I just running it to use it.


If as an install, where should I install it to?Overwrite where it is already located or somewhere else, I have copied it to the end of my drive so I have it saved, I did that when Gparted was working I copied it with that. Like I said I don't need Fedora or Fluxbox I installed those in the hope of maybe they would correct the problem.

All I really want is Vista and UbuntuStudio32 everything else can go.

---

### Post by Elfy on 2011-06-21
Hi - good to see you getting some help here.

Could you please when you are posting long lists of things like the bootsdcript please use the code tags. 

2 ways of doing so - if you are using the New Reply button - highlight all and hit the # button in the top of the reply box. 

If you are using Quick Reply put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks - makes it easier for people to read (and for people like me with 75 posts per page slightly less daunting to read through :) )

No need to do anything about the previous posts. 

regards

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> do I check the CD before install or after. Second do I run it as an install or am I just running it to use it.


If as an install, where should I install it to?Overwrite where it is already located or somewhere else, I have copied it to the end of my drive so I have it saved, I did that when Gparted was working I copied it with that. Like I said I don't need Fedora or Fluxbox I installed those in the hope of maybe they would correct the problem.


I am rescuing your ubuntu installation.

i want you to check your cd if it has the correct grub. If it does then you are able to rescue your ubuntu installation. the first command mounts the correct parition
the second command overrides the mbr which is need to boot your computer. From the looks of it there is testdisk in the mbr and it does not seem to work

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> I am rescuing your ubuntu installation.

i want you to check your cd if it has the correct grub. If it does then you are able to rescue your ubuntu installation. the first command mounts the correct parition
the second command overrides the mbr which is need to boot your computer. From the looks of it there is testdisk in the mbr and it does not seem to work




Still not clear on how to check it, run it or some other way!


This is me being a moron, step by step please.

---

### Post by idoitprone on 2011-06-21
check before you use the command

```
grub-install --version
```if grub 1.97 and up
then do these commands

I hope that this grub 2 is compatible with the grub 2 from you ubuntu installation
```
sudo mount /dev/sda5 /mnt  
 sudo grub-install --root-directory=/mnt /dev/sda
```If not I might have to the annoying method of rescueing your fedora installation which will take alot longer. I rather tell you to reinstall fedora to rescue ubuntu which is a faster method than manually rescuing fedora

---

### Post by ppv on 2011-06-21
> **JASONFUSARO said:**
> Still not clear on how to check it, run it or some other way!
 
 
This is me being a moron, step by step please.
 
Just dropping by for this question -
 
Shut down your computer.
 
Start it again and remove whichever CD you have it in there and put in the UbuntuStudio Live CD
 
Then when you get a menu, select the option which is something like "Try without installing"
 
If it boots up in graphical mode you will get a desktop else you will get a screen with the command prompt.
 
If you got a desktop open up a terminal from the menu. Now either at the terminal or at the screen with the command prompt issue the below command and paste the output here.
 
```
 
grub-install --version

```

---

### Post by JASONFUSARO on 2011-06-21
> **ppv said:**
> Just dropping by for this question -
 
Shut down your computer.
 
Start it again and remove whichever CD you have it in there and put in the UbuntuStudio Live CD
 
Then when you get a menu, select the option which is something like "Try without installing"
 
If it boots up in graphical mode you will get a desktop else you will get a screen with the command prompt.
 
If you got a desktop open up a terminal from the menu. Now either at the terminal or at the screen with the command prompt issue the below command and paste the output here.
 
```
 
grub-install --version

```


I have been trying that with both my UbuntuStudio CD's but they are not live , I checked and apparently Studio does not have a Live CD

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> check before you use the command

```
grub-install --version
```if grub 1.97 and up
then do these commands

I hope that this grub 2 is compatible with the grub 2 from you ubuntu installation
```
sudo mount /dev/sda5 /mnt  
 sudo grub-install --root-directory=/mnt /dev/sda
```If not I might have to the annoying method of rescueing your fedora installation which will take alot longer. I rather tell you to reinstall fedora to rescue ubuntu which is a faster method than manually rescuing fedora


I took awhile because I thought Studio was the same type of install but its not like the Ubuntu Live Install

I am running my Ubuntu Lived CD

and I ran those commands


here is the output


ubuntu@ubuntu:~$ grub-install --version
grub-install (GRUB) [SIZE=3]**[COLOR=Red]1.99~rc1-13ubuntu3[/COLOR]**[/SIZE]
ubuntu@ubuntu:~$ whoami
ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ 



seems ok now what??

---

### Post by nothingspecial on 2011-06-21
OMG, this thread is amazing  

reboot (without a cd)

idoitprone I take my hat off to you, come to think of it JASONFUSARO, you can have my hat too.

---

### Post by JASONFUSARO on 2011-06-21
> **forestpiskie said:**
> Hi - good to see you getting some help here.

Could you please when you are posting long lists of things like the bootsdcript please use the code tags. 

2 ways of doing so - if you are using the New Reply button - highlight all and hit the # button in the top of the reply box. 

If you are using Quick Reply put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks - makes it easier for people to read (and for people like me with 75 posts per page slightly less daunting to read through :) )

No need to do anything about the previous posts. 

regards

COOL Thanks for the TIP



```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97-71.fc15) is installed in the boot 
                       sector of sda6 and looks at sector 346555376 of the 
                       same hard drive for the stage2 file.  A stage2 file is 
                       at this location on /dev/sda.  Stage2 looks on 
                       partition #6 for /boot/grub/menu.lst.
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of 
                       sda11 and looks at sector 920564064 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda11,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of 
                       sda12 and looks at sector 920564064 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda11,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda12,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   b W95 FAT32
/dev/sda2             411,648   183,967,743   183,556,096   7 NTFS / exFAT / HPFS
/dev/sda3         183,969,792   250,667,007    66,697,216  83 Linux
/dev/sda4         250,667,046   976,784,129   726,117,084   f W95 Extended (LBA)
/dev/sda5         250,669,056   341,999,615    91,330,560  83 Linux
/dev/sda6         342,001,664   393,201,663    51,200,000  83 Linux
/dev/sda7         393,207,003   416,372,634    23,165,632  82 Linux swap / Solaris
/dev/sda8         429,737,984   480,937,983    51,200,000  83 Linux
/dev/sda9         480,953,970   608,863,497   127,909,528  83 Linux
/dev/sda10        647,804,928   717,547,519    69,742,592  83 Linux
/dev/sda11        728,395,776   843,628,543   115,232,768  83 Linux
/dev/sda12        861,538,304   976,771,071   115,232,768  83 Linux

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7969 MB, 7969177600 bytes
126 heads, 10 sectors/track, 12353 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    15,564,799    15,556,608   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/sda1        3771-1537                              vfat       HDstartArea
/dev/sda10       bb3ba6a0-3a7a-4676-b0d0-89359b5d98bb   ext3       Home2
/dev/sda11       393c5b0e-153a-4aed-bd6b-e17689558783   ext4       
/dev/sda12       393c5b0e-153a-4aed-bd6b-e17689558783   ext4       
/dev/sda2        0E5A6700395DFEEF                       ntfs       WindowsVista
/dev/sda3        03cf3622-a18f-47c4-94d0-9b7c887f0411   ext4       UbuntuStu64Bit
/dev/sda5        234cd951-aed4-4866-b85a-c28ae4020598   ext4       UbuntuStudio32
/dev/sda6        b06bbdc9-7a7f-47a4-8fc7-9e09f9960319   ext4       _Fedora-15-i686-
/dev/sda7        c5a5b515-db58-4706-b2d4-53379a5a27e7   swap       
/dev/sda8        b06bbdc9-7a7f-47a4-8fc7-9e09f9960319   ext4       _Fedora-15-i686-
/dev/sda9        234cd951-aed4-4866-b85a-c28ae4020598   ext4       UbuntuStudio32
/dev/sdb1        426C23CB6C23B895                       ntfs       SoftwareDesign

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/unionfs/usr         squashfs   (rw)
/dev/loop1       /lib/unionfs/firmware    squashfs   (rw)
/dev/loop2       /lib/unionfs/modules     squashfs   (rw)
/dev/sda2        /media/sda2              fuseblk    (rw,allow_other,blksize=4096)
/dev/sda5        /mnt                     ext4       (rw)
/dev/sda6        /media/sda6              ext4       (rw)
/dev/sda8        /media/sda8              ext4       (rw)
/dev/sdb1        /media/sdb1              fuseblk    (rw,allow_other,blksize=4096)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
    initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0605b3b1-32d5-4267-9880-2cfcd39edf52 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  89.217445374 = 95.796502528   boot/grub/core.img                             1
  89.209972382 = 95.788478464   boot/grub/grub.cfg                             1
 101.195255280 = 108.657577984  boot/initrd.img-2.6.38-10-generic              2
  97.216609955 = 104.385540096  boot/initrd.img-2.6.38-8-generic               2
  97.090164185 = 104.249769984  boot/vmlinuz-2.6.38-10-generic                 2
  89.215705872 = 95.794634752   boot/vmlinuz-2.6.38-8-generic                 12
 101.195255280 = 108.657577984  initrd.img                                     2
  97.216609955 = 104.385540096  initrd.img.old                                 2
  97.090164185 = 104.249769984  vmlinuz                                        2
  89.215705872 = 95.794634752   vmlinuz.old                                   12

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
    initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=234cd951-aed4-4866-b85a-c28ae4020598  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=25582a6f-ef0c-4eac-b9cc-a9696d67658d  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults             0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sdf1                                  /media/sdf1  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  ntfs  defaults             0  0  
/dev/sda7                                  /media/sda7  ext3  defaults             0  0  
/dev/sda8                                  /media/sda8  swap  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  
/dev/sde1                                  /media/sde1  ntfs  defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs  defaults             0  0  
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 151.654991150 = 162.838306816  boot/grub/core.img                             1
 151.670066833 = 162.854494208  boot/grub/grub.cfg                             1
 138.283622742 = 148.480909312  boot/initrd.img-2.6.38-8-generic               2
 119.731750488 = 128.560988160  boot/vmlinuz-2.6.38-8-generic                  1
 138.283622742 = 148.480909312  initrd.img                                     2
 119.731750488 = 128.560988160  vmlinuz                                        1

========================== sda6/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-32.fc15.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.38.8-32.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.8-32.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img
title BootLoader
    rootnoverify (hd0,0)
    chainloader +1
title Other
    rootnoverify (hd0,1)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jun 18 19:39:25 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 /                       ext4    defaults        1 1
UUID=a1008bd3-7fb2-493e-9d0c-fcb1edd512f8 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.206275940 = 177.388888064  boot/grub/grub.conf                            1
 165.206275940 = 177.388888064  boot/grub/menu.lst                             1
 165.250598907 = 177.436479488  boot/grub/stage2                               1
 165.248336792 = 177.434050560  boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img   1
 165.500976562 = 177.705320448  boot/initramfs-2.6.38.8-32.fc15.i686.img       2
 164.326065063 = 176.443768832  boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686         1
 165.475181580 = 177.677623296  boot/vmlinuz-2.6.38.8-32.fc15.i686             1

========================== sda8/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=2
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-32.fc15.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.38.8-32.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.8-32.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img
title BootLoader
    rootnoverify (hd0,0)
    chainloader +1
title Other
    rootnoverify (hd0,1)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jun 18 19:39:25 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=b06bbdc9-7a7f-47a4-8fc7-9e09f9960319 /                       ext4    defaults        1 1
UUID=a1008bd3-7fb2-493e-9d0c-fcb1edd512f8 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 207.042213440 = 222.309883904  boot/grub/grub.conf                            1
 207.042213440 = 222.309883904  boot/grub/menu.lst                             1
 207.044155121 = 222.311968768  boot/grub/stage2                               1
 207.084274292 = 222.355046400  boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img   1
 207.336914062 = 222.626316288  boot/initramfs-2.6.38.8-32.fc15.i686.img       2
 206.162002563 = 221.364764672  boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686         1
 207.311119080 = 222.598619136  boot/vmlinuz-2.6.38.8-32.fc15.i686             1

=========================== sda9/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03cf3622-a18f-47c4-94d0-9b7c887f0411 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 03cf3622-a18f-47c4-94d0-9b7c887f0411
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 0E5A6700395DFEEF
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro vga=792 splash quiet quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 234cd951-aed4-4866-b85a-c28ae4020598
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=234cd951-aed4-4866-b85a-c28ae4020598 ro single vga=792 splash quiet
    initrd /boot/initrd.img-2.6.38-8-generic
}
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
--------------------------------------------------------------------------------

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda9 during installation
UUID=234cd951-aed4-4866-b85a-c28ae4020598  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda10 during installation
UUID=25582a6f-ef0c-4eac-b9cc-a9696d67658d  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ntfs  defaults             0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sdf1                                  /media/sdf1  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  ntfs  defaults             0  0  
/dev/sda4                                  /media/sda4  ext4  defaults             0  0  
/dev/sda8                                  /media/sda8  swap  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  
/dev/sde1                                  /media/sde1  ntfs  defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs  defaults             0  0  
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 261.463398933 = 280.744186880  boot/grub/core.img                             1
 261.478470802 = 280.760370176  boot/grub/grub.cfg                             1
 248.092026711 = 266.386785280  boot/initrd.img-2.6.38-8-generic               2
 229.540154457 = 246.466864128  boot/vmlinuz-2.6.38-8-generic                  1
 248.092026711 = 266.386785280  initrd.img                                     2
 229.540154457 = 246.466864128  vmlinuz                                        1

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

```

---

### Post by JASONFUSARO on 2011-06-21
> **nothingspecial said:**
> OMG, this thread is amazing  

reboot (without a cd)

idoitprone I take my hat off to you, come to think of it JASONFUSARO, you can have my hat too.




Yea I was thinking the same thing, it has gotten rather large, any rules about the size of threads??

---

### Post by JASONFUSARO on 2011-06-21
> **nothingspecial said:**
> OMG, this thread is amazing  

reboot (without a cd)

idoitprone I take my hat off to you, come to think of it JASONFUSARO, you can have my hat too.



I had to look at this a couple of times, before it clicked, hold the gun make sure it stays pointed at my forehead, whilst I pull the trigger

---

### Post by JASONFUSARO on 2011-06-21
Thanks idoitprone

I am back booting up fine

my menu does not have Fedora listed

Ubuntu with Linux 2.6.38-10-generic
Ubuntu with Linux 2.6.38-10-generic (recovery mode)
Previous Linux Versions
Memory test
Windows Vista
Ubuntu with Linux 2.6.38-8-generic sda9


now the first option gets me to the first Ubuntu but that was the one with a network problem

when I select the one on sda9 I get the messages that I originally had when I started this whole excursion

it has below the splash


Keys: Press F to attempt to fix errors  I to ignore  S to skip mount M for manual recovery


The first time (just awhile ago) I selected M and it was like a bomb went off screen filled with many many things then 
It rebooted 


then only  these options come up



S to skip mount M for manual recovery


so I am back running my Ubuntu Live CD because No network access in th option that will run and the one I had working real well won't get past the splash screen



and as far as Vista goes, that is still not getting anywhere



I think when I shrunk my partition and it shifted that is what caused that problem, based on what I have been reading critical system files need to be copied or moved so the bounderies stay flush both in Linux and windows, copy with terminal commands dd in Linux and raw copy in windows.

What should be my next step, should I try and delete those unwanted partitions, should I copy the copy of UbuntuStudio32 back? I think I messed up the menu pointer in the /root/grub directory changed something to point to (hd0,5) that was a while ago am not to certain, remember reading something and then trying it, the 5 is one less than the actual location on drive.


any suggestions

my new moto is AAEBUFIU   Ask An Expert Before You F It Up

---

### Post by idoitprone on 2011-06-21
i was feelin kidda ill and thinking about popeyes my lol.


when you in ubuntu and make sure this os is your main!!!!


i want you to do these commands

```
sudo grub-install /dev/sda

sudo update-grub
```

that should fix everything

when you delete the other oses, becareful 
when your done

always update the grub. 
```
sudo update-grub
```

nothingspecial, most of the post is because i been working blind. Never work blind unless you want a thread to be this long

---

### Post by JASONFUSARO on 2011-06-21
Well I am in UbuntuStudio32 thank you.

But when I don't have my 320GiB USB attached I don't get the Linux menu on reboot. Right now I have all the USB drives attached that were attached when I did the initial install, why that would make any difference I can't understand it.


That panel that is sitting there I can't modify it so something is still not right. In ubuntuStudio64 the network isn't working, and I think Vista is hopeless, and from what I have been reading it is more tricky installing it after Linux than before.  


What would be the safest approach at saving  all my apps and home directory so If I decide to wipe everything and start over this setup cane just be moved back, I have been reading but don't quite have a good grasp on what are the important directories to save, and whether or not to create separate partitions for them, from what I have read it simplifies the process of upgrading versions and keeping settings intact.

If I run that script again with all my USB drives attached will that give a clearer picture, yea I know that sounds funny.

Is there something I can run now before a reboot that will verify the MBR or GRUBS VBR are ok.

I still can't access anything with Gparted still showing unallocated Drive, but everything can be seen when I run Disk Utility see attachment. 



Any suggestions would be even more appreciated.

I don't even wan't to shut it down now until I come up with a real good plan of action.



Thanks again

---

### Post by idoitprone on 2011-06-21
which utility did you use to make the external paritions

You can safely delete some partitions, if you wish

Did you see those command i posted at the end.

Just dont delete the swap and the ubuntu parititon you been working on which is sda5 i believe

I will take a look at your windows
But it may require rescuing windows then you will have to rescue grub again. It was really simple. As you can see most of the post are because i been working blind. Since i now know you are somewhat capable. this process will be quicker

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> i was feelin kidda ill and thinking about popeyes my lol.


when you in ubuntu and make sure this os is your main!!!!


i want you to do these commands

```
sudo grub-install /dev/sda

sudo update-grub
```that should fix everything

when you delete the other oses, becareful 
when your done

always update the grub. 
```
sudo update-grub
```nothingspecial, most of the post is because i been working blind. Never work blind unless you want a thread to be this long



I can't delete them can't access them from the menu, and read the post I put up because there still seems to be something kooky going on behind the scenes not being able to boot unless my USB is attached, they were all attached when I installed but I don't know why that would make any difference, I have a 500GiB WD like my internal, 320GiB HP, abd Seagate 160GiB and two multiport Hubs with my scanner and printer and camera, but that should have no affect on the install am I right??

Am I supposed to run the GRUB commands now?? I am fearful of typeing anything man I don't wan't to lose it again:)

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> I can't delete them can't access them from the menu, and read the post I put up because there still seems to be something kooky going on behind the scenes not being able to boot unless my USB is attached, they were all attached when I installed but I don't know why that would make any difference, I have a 500GiB WD like my internal, 320GiB HP, abd Seagate 160GiB and two multiport Hubs with my scanner and printer and camera, but that should have no affect on the install am I right??

Am I supposed to run the GRUB commands now?? I am fearful of typeing anything man I don't wan't to lose it again:)

dont worry those commands are not harmful. It should not destory your installation. I was fearful of that thing where your usb must be attach to boot. That is why i told you to do those commands

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> which utility did you use to make the external paritions

You can safely delete some partitions, if you wish

Did you see those command i posted at the end.

Just dont delete the swap and the ubuntu parititon you been working on which is sda5 i believe

I will take a look at your windows
But it may require rescuing windows then you will have to rescue grub again. It was really simple. As you can see most of the post are because i been working blind. Since i now know you are somewhat capable. this process will be quicker


here we go again while I am answering one post you are putting up another one  and I am gonna get confused!

I used Gparted, It ran during one of the installs I think, I am confused, but I could have done right before off my Gparted CD to set up the partitions I wanted. 

That first partition I have up front of windows 200MiB that is supposed to be bootable right, I am a bit confused about that, or is the windows partitionsupposed to be bootable??

The blank partition , the first one in the extended section, that is my UbuntuStudio32, and the one at the end that looks blank, is the copy I made, did that with Gparted too, should have labeled it, but can't modify them anymore.

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> dont worry those commands are not harmful. It should not destory your installation. I was fearful of that thing where your usb must be attach to boot. That is why i told you to do those commands

k

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> here we go again while I am answering one post you are putting up another one  and I am gonna get confused!

I used Gparted, It ran during one of the installs I think, I am confused, but I could have done right before off my Gparted CD to set up the partitions I wanted. 

That first partition I have up front of windows 200MiB that is supposed to be bootable right, I am a bit confused about that, or is the windows partitionsupposed to be bootable??

The blank partition , the first one in the extended section, that is my UbuntuStudio32, and the one at the end that looks blank, is the copy I made, did that with Gparted too, should have labeled it, but can't modify them anymore. according to the script sda1 does not appear to have anything in it. Go take a look. I believe it should not be nesscessay since the boot files are in sda2 which in your windows parition
You can safely delete the fedora parition and that weird grub on sda11, becareful ok. You can do this while booted in ubuntu and when you done

```
sudo update-grub

```
i might be wary on deleting parition, since it chages the parition numbers sometimes which will render your os un bootable. try to do it from within the ubuntu studio and update the grub

i believe your windows can boot

---

### Post by JASONFUSARO on 2011-06-21
Just tried KDE partition manager and got this message


 p, li { white-space: pre-wrap; }  Configuration file "/root/.kde/share/config/kdedrc" not writable.
 Please contact your system administrator.


and 

 p, li { white-space: pre-wrap; }  Configuration file "/root/.kde/share/config/partitionmanagerrc" not writable.
 Please contact your system administrator.


Yep same with KDE can't read from it.


But why can file manager see it and the directories and even access them??????????????

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> Just tried KDE partition manager and got this message


 p, li { white-space: pre-wrap; }  Configuration file "/root/.kde/share/config/kdedrc" not writable.
 Please contact your system administrator.


and 

 p, li { white-space: pre-wrap; }  Configuration file "/root/.kde/share/config/partitionmanagerrc" not writable.
 Please contact your system administrator.


Yep same with KDE can't read from it.


But why can file manager see it and the directories and even access them??????????????

i believe that error because you used root and ubuntu disable root

try ```
gksu partitionmanager


```

---

### Post by JASONFUSARO on 2011-06-21
```

```> **idoitprone said:**
> i believe that error because you used root and ubuntu disable root

try ```
gksu partitionmanager


```



I ran the commands looks good

```
jasonfusaro@ubuntuStudio32Bit:~$ whoami
jasonfusaro
jasonfusaro@ubuntuStudio32Bit:~$ sudo grub-install /dev/sda
[sudo] password for jasonfusaro: 
Installation finished. No error reported.
jasonfusaro@ubuntuStudio32Bit:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows Vista (loader) on /dev/sda2
Found Ubuntu 11.04 (11.04) on /dev/sda3
Found Fedora release 15 (Lovelock) on /dev/sda6
Found Fedora release 15 (Lovelock) on /dev/sda8
Found Ubuntu 11.04 (11.04) on /dev/sda9
done
jasonfusaro@ubuntuStudio32Bit:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows Vista (loader) on /dev/sda2
Found Ubuntu 11.04 (11.04) on /dev/sda3
Found Fedora release 15 (Lovelock) on /dev/sda6
Found Fedora release 15 (Lovelock) on /dev/sda8
Found Ubuntu 11.04 (11.04) on /dev/sda9
done
jasonfusaro@ubuntuStudio32Bit:~$
```

---

### Post by JASONFUSARO on 2011-06-21
ran that gksu

jasonfusaro@ubuntuStudio32Bit:~$ gksu partitionmanager
partitionmanager(12328)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
partitionmanager(12328)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:


what does that mean???


your the Wizard of OZ dude!!  :)


no they are still coming up blank, I got KVM will that be any different??

I went Hog wild I downloaded all kinds of stuff, I get caried away like that, I don't look before I leap.

and sometimes don't read the screen before I click that button..:)

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> ran that gksu

jasonfusaro@ubuntuStudio32Bit:~$ gksu partitionmanager
partitionmanager(12328)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
partitionmanager(12328)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:


what does that mean???


your the Wizard of OZ dude!!  :)

aww crap i just realize you are running kde
did it fail?
```
kdesu partitionmanager
```

---

### Post by JASONFUSARO on 2011-06-21
If I don't respond, that is because I gotta run to the store before it closes, be back shortly Mr. Wizard.!!!

):P):P

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> aww crap i just realize you are running kde
did it fail?
```
kdesu partitionmanager
```


I didn't run this one, don't or do??


by the way how do you keep the smileys from diplaying in those lines do you have to put the whole line in quotes??


really gotta run to the store, be right back.

---

### Post by idoitprone on 2011-06-21
kdesu is just a command that elevates the permission to do some administrative 

partitionmanger is what you need

smileys?

try to put in code tages next time, it might prevent it
:)
```
:)
```

---

### Post by JASONFUSARO on 2011-06-21
When you said I am running KDE isn't my system running GNOME, and also does it get confused when you try and mix variants, I think I read that somewhere ie. if you run a certain package to install thenyou have to stick with that and not switch.

Is there a rule about the length and size of threads??? Should this be closed and considered solved and then start another one?? What about tags for searching should I think that through in case someone else runs into the same jam they can find it more easily?? I only been at this a few weeks so I still ain picked up on the protocol.

Also I probably should limit my stupid questions when I can G:):)GLE them.

---

### Post by idoitprone on 2011-06-21
> **JASONFUSARO said:**
> When you said I am running KDE isn't my system running GNOME, and also does it get confused when you try and mix variants, I think I read that somewhere ie. if you run a certain package to install thenyou have to stick with that and not switch.

Is there a rule about the length and size of threads??? Should this be closed and considered solved and then start another one?? What about tags for searching should I think that through in case someone else runs into the same jam they can find it more easily?? I only been at this a few weeks so I still ain picked up on the protocol.

Also I probably should limit my stupid questions when I can G:):)GLE them.

i believe the solved button is near thread tools

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> according to the script sda1 does not appear to have anything in it. Go take a look. I believe it should not be nesscessay since the boot files are in sda2 which in your windows parition
You can safely delete the fedora parition and that weird grub on sda11, becareful ok. You can do this while booted in ubuntu and when you done

```
sudo update-grub

```i might be wary on deleting parition, since it chages the parition numbers sometimes which will render your os un bootable. try to do it from within the ubuntu studio and update the grub

i believe your windows can boot


Now when  you say delete it, how I can't get into Gparted I can delete the stuff through file manager but that wont get rid of the partition, and if I do happen to find a way to delete them can I slide the swap file left or right or should I move it right to the end of the drive?



tried that kdesu

jasonfusaro@ubuntuStudio32Bit:~$ kdesu partitionmanager
kdesu: command not found


just did a quick google can't seem to hit on one that explains on getting it to work, tried apt-get or install but have no clue about it this early in the game.

---

### Post by JASONFUSARO on 2011-06-21
I think I am ready to try a reboot, and see what the menu looks like and see if I get back here ok.

---

### Post by JASONFUSARO on 2011-06-21
grub-install --version in Fedora is 0.97-71.fc 15 would that mean that it is not advisable to  run that sudo update-grub command ??

---

### Post by idoitprone on 2011-06-21
update grub in the main os

which mean when you boot into ubuntustudio32

---

### Post by JASONFUSARO on 2011-06-21
> **idoitprone said:**
> update grub in the main os

which mean when you boot into ubuntustudio32

thanks

---

