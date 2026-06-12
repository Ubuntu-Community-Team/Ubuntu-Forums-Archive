---
title: "Upgraded to karmic but grub calls wrong kernel"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by dbuehler on 2009-11-03
I upgraded from jaunty to karmic but it appears that grub was not updated.  Grub still says "Ubuntu 9.04, kernel 2.6.28-15-generic."  I also have no sound and suspect this is why.

I guess I need to edit menu.lst to call the correct kernel.  Here's the way it is now:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro quiet splash noapic
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

Should I just edit the 'kernel' line to call the correct kernel and change the title to match?  Do I need to change the initrd line or the next section for recovery mode?  Any help is appreciated.

Thanks.

---

### Post by Zoot7 on 2009-11-03
Does running
```
sudo update-grub
```

Find the installed kernel and then list it in menu.lst?

---

### Post by dbuehler on 2009-11-03
update-grub finds the new kernel but menu.lst still calls the old one.

---

### Post by ranch hand on 2009-11-03
Make the new one the default to boot to.

I am assuming grub-legacy here.  Where is the new kernel in your menu.lst?

Posting that would be nice.

---

### Post by drs305 on 2009-11-03
Use StartUp-Manager - it should detect the installed kernels and you can select which one you want without manually editing the files. SUM works with Grub legacy and somewhat with Grub 2, but with both you can set the default kernel.

Here is a link about installing and running SUM:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

Or the community doc based on the same thread:
[https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")

If you need/want to edit the files manually, please confirm if you are using Grub legacy (or Grub 2). The version is listed at the top of the boot menu.

---

### Post by kansasnoob on 2009-11-03
I'd really like to see the output of:

```
ls /boot/grub
```

Is this a multi-boot?

---

### Post by ranch hand on 2009-11-03
Oh my, is anyone in testing?

---

### Post by dbuehler on 2009-11-03
Grub is the one that came with Ubuntu so I assume it is legacy.

It sounds like SUM will make the changes so I will try that route and let you know how it goes.

To answer the other question, here is the output of "ls /boot/grub"

dan@winston:/boot/grub$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  minix_stage1_5     stage2
device.map     grubenv            menu.lst      reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  installed-version  menu.lst~     stage1

---

### Post by kansasnoob on 2009-11-03
> **ranch hand said:**
> Oh my, is anyone in testing?

Something I saw when we were still in testing was where /grub would, after various updates/upgrades, end up with both legacy grub and grub2 files and folders.

I saw that mess with things a few times. The easiest thing was to basically rename /boot/grub, create a new /boot/grub directory, and start fresh.

The methodology would be the same as I described here (notice that appendix #2 describes very briefly how to start with a fresh grub2):

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

### Post by kansasnoob on 2009-11-03
> **dbuehler said:**
> Grub is the one that came with Ubuntu so I assume it is legacy.

It sounds like SUM will make the changes so I will try that route and let you know how it goes.

To answer the other question, here is the output of "ls /boot/grub"

dan@winston:/boot/grub$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  minix_stage1_5     stage2
device.map     grubenv            menu.lst      reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  installed-version  menu.lst~     stage1

That looks fine. I'd try SUM.

---

### Post by drs305 on 2009-11-03
> **dbuehler said:**
> 
It sounds like SUM will make the changes so I will try that route and let you know how it goes.


SUM is the easiest thing to try, but there is a good chance that there will be more that needs to be done. Nevertheless, having SUM installed will allow you to make several of the basic changes later even if your install did not go quite "as planned".

---

### Post by dbuehler on 2009-11-03
I tried SUM but the drop-down menu under "default operating system" doesn't list the new kernel.  All it shows are the ubuntu 9.04 files.

---

### Post by kansasnoob on 2009-11-03
I'm curious what the output shows if you run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If it shows a bunch of stuff to be either installed or removed **just click no (n)** and post the output here.

Likewise with;

```
sudo apt-get -f install
```

Just don't click on yes yet if it's going to remove a bunch of stuff. It might tell you to run autoremove but don't do it until we have time to look at it.

---

### Post by kansasnoob on 2009-11-03
Just FYI what I'm looking for is some indication that the new kernel is "completely" installed. I've seen some strange upgrade behavior in recent days.

Another way we might be able to tell is by looking in /boot, for instance (this is from my 9.04):

> lance@lance-desktop:~$ ls /boot
abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-12-generic         System.map-2.6.28-11-generic
abi-2.6.28-13-generic         System.map-2.6.28-12-generic
abi-2.6.28-14-generic         System.map-2.6.28-13-generic
abi-2.6.28-15-generic         System.map-2.6.28-14-generic
abi-2.6.28-16-generic         System.map-2.6.28-15-generic
config-2.6.28-11-generic      System.map-2.6.28-16-generic
config-2.6.28-12-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-12-generic
config-2.6.28-14-generic      vmcoreinfo-2.6.28-13-generic
config-2.6.28-15-generic      vmcoreinfo-2.6.28-14-generic
config-2.6.28-16-generic      vmcoreinfo-2.6.28-15-generic
grub                          vmcoreinfo-2.6.28-16-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-12-generic  vmlinuz-2.6.28-12-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-14-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.28-16-generic  vmlinuz-2.6.28-16-generic


You can see that I have every kernel throughout the life cycle of Jaunty. Of course since my Karmic was a fresh install it only shows the new Karmic kernel.

---

### Post by drs305 on 2009-11-04
> **dbuehler said:**
> I upgraded from jaunty to karmic but it appears that grub was not updated.  Grub still says "Ubuntu 9.04, kernel 2.6.28-15-generic."  I also have no sound and suspect this is why.

I guess I need to edit menu.lst to call the correct kernel.  Here's the way it is now:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro quiet splash noapic
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

Should I just edit the 'kernel' line to call the correct kernel and change the title to match?  Do I need to change the initrd line or the next section for recovery mode?  Any help is appreciated.

Thanks.

Well, back to your original post. As kansasnoob says, take a look at your /boot directory and check the contents. Earlier you stated that update-grub found the new kernel.  I think it's time to just try your original suggestion and see if Karmic runs:

Backup menu.lst:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksu gedit /boot/grub/menu.lst
```

Check for existing Karmic kernels:
```
ls /boot | grep vmlinuz-2.6.31
```


Add this to menu.lst. If you want to do the minimum amount of tweaking, place it in the list where the current default is (i.e. if the first "title" is the one that currently boots, make this the first entry). Make sure the kernel number and UUIDs are correct:
> 
title		Ubuntu 9.10, kernel 2.6.31-[COLOR="Red"]14[/COLOR]-generic
uuid		[COLOR="Red"]7fa103ed-2bbe-4b75-9685-ca02cd31254e[/COLOR]
kernel		/boot/vmlinuz-2.6.31-[COLOR="Red"]14[/COLOR]-generic root=UUID=[COLOR="Red"]7fa103ed-2bbe-4b75-9685-ca02cd31254e[/COLOR] ro quiet splash noapic
initrd		/boot/initrd.img-2.6.31-[COLOR="Red"]14[/COLOR]-generic
quiet


---

### Post by dbuehler on 2009-11-04
Sorry for the delay in answering but I crashed grub and it took me a while to correct that. :-( 

Here's the output from the first command:
dan@winston:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for dan: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                
Get:5 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [1,300B]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Get:6 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources [722B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [21.8kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [8,059B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [14B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [692B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [10.8kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [14B]
Fetched 97.2kB in 1s (71.2kB/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  binutils binutils-static brasero empathy empathy-doc f-spot
  libbrasero-media0 libempathy-common libempathy-gtk-common libempathy-gtk28
  libempathy30 libkrosspython0 nvidia-common python python-dev python-kde4
  python-minimal ubuntu-xsplash-artwork xsplash
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,067kB of archives.
After this operation, 164kB disk space will be freed.
Do you want to continue [Y/n]? n


Output from next command:
dan@winston:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 menu libsvga1 binutils-static liblzo2-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.


The /boot directory seems to have the correct kernel. Here's the contents:
dan@winston:/boot$ ls
abi-2.6.28-15-generic         memtest86+.bin
abi-2.6.31-14-generic         System.map-2.6.28-15-generic
config-2.6.28-15-generic      System.map-2.6.31-14-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.28-15-generic
grub                          vmcoreinfo-2.6.31-14-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic

However, when I edit menu.lst per the last suggestion, the new kernel does not show up.  It almost seems to me that the new kernel is not being seen even though it shows up on a listing of /boot.

Dan

---

### Post by kansasnoob on 2009-11-04
Would you please just post your menu.lst:

```
cat /boot/grub/menu.lst
```

---

### Post by QLee on 2009-11-04
[QUOTE=dbuehler]I upgraded from jaunty to karmic but it appears that grub was not updated.[/QUOTE]

If I understand correctly this is default behaviour, the update leaves your legacy GRUB unless you choose differently.

 [QUOTE=dbuehler] Grub still says "Ubuntu 9.04, kernel 2.6.28-15-generic."  I also have no sound and suspect this is why.[/QUOTE]

By "Grub says" I assume you mean the menu display.


[QUOTE=dbuehler]I guess I need to edit menu.lst to call the correct kernel.  Here's the way it is now:

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro quiet splash noapic
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

Should I just edit the 'kernel' line to call the correct kernel and change the title to match?  Do I need to change the initrd line or the next section for recovery mode?  Any help is appreciated.[/QUOTE]


As long as the boot partition remains the same as the UUID you cited (and the version files you want to use are in your /boot), then yes, changing the lines in the stanza to the correct vmlinuz and initrd would work.

(you didn't change to ext4 filesystem did you?)

I suspect that the upgrade gave you GRUB2 as the GRUB binary on your system, thus when you issue grub-update it writes the GRUB2 stuff to your /boot but your legacy grub in your MBR still uses the menu.lst because it doesn't know about grub.cfg.

Edit: I suppose I should mention this too, If my theory is correct and you have GRUB2 installed in your system you could install GRUB2 and use it. You already know it sees all your kernels, at least you said so and it will add menu options automagically.

---

### Post by kansasnoob on 2009-11-04
> I suspect that the upgrade gave you GRUB2 as the GRUB binary on your system, thus when you issue grub-update it writes the GRUB2 stuff to your /boot but your legacy grub in your MBR still uses the menu.lst because it doesn't know about grub.cfg.

If that were true grub.cfg would have shown up in /boot/grub and it didn't.

---

### Post by QLee on 2009-11-04
> **kansasnoob said:**
> If that were true grub.cfg would have shown up in /boot/grub and it didn't.

I take your point, it's a good one.


Edit: Except, I can't find any place where the OP states what is in /boot/grub.
Edit2: Ah, found it on 1st page of thread

Edit3: Editing the stanza in menu.lst to the correct versions of vmlinuz and initrd should work then because the legacy GRUB in the MBR will parse menu.lst at boot.

---

### Post by kansasnoob on 2009-11-04
> Edit: Except, I can't find any place where the OP states what is in /boot/grub.

Post #8.

---

### Post by dbuehler on 2009-11-04
Here is my menu.lst:
dan@winston:/boot/grub$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7fa103ed-2bbe-4b75-9685-ca02cd31254e

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro quiet splash noapic
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7fa103ed-2bbe-4b75-9685-ca02cd31254e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7fa103ed-2bbe-4b75-9685-ca02cd31254e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


When I said that grub said it found the new kernel, I was trying to explain that when I issued update-grub, the new kernel version was displayed on the screen.  Old version was there also.  However, when I just now tried it, I get a message that a new version is available.  After this post I will try installing the new one and see if that helps.


And, no, I did not switch to ext4.  

I have also not installed grub2.  From some of the posts I got the impression it had some problems but I am willing to try.  I guess I can do that in synaptic by removing grub and installing grub2.  I will try that if the grub-update doesn't work.

I will let you know what happens.

Dan

---

### Post by kansasnoob on 2009-11-04
If you want to install grub 2 that's fine but it requires a bit more than just installing a package:

```
sudo mv /boot/grub /boot/grub_legacy
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

---

### Post by QLee on 2009-11-04
[QUOTE=dbuehler]
I have also not installed grub2.  From some of the posts I got the impression it had some problems but I am willing to try.  I guess I can do that in synaptic by removing grub and installing grub2.  I will try that if the grub-update doesn't work.[/QUOTE]

No particular reason to do this at this time, it's your choice.

It will be different in several ways from what you are familiar with.

You might want to look at this thread in our community tutorials and tips, it's called GRUB2 Guide.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by kansasnoob on 2009-11-04
> Editing the stanza in menu.lst to the correct versions of vmlinuz and initrd should work then because the legacy GRUB in the MBR will parse menu.lst at boot.

I was thinking somewhat along the same lines. I was thinking of taking the lazy way out and doing "sudo mv /boot/grub/menu.lst /boot/grub/menu.lst_old" then running "sudo update-grub" which should then ask to create a new menu.lst, just say yes and see what the new list looks like ;)

But it looks like we're going a different direction now.

---

### Post by QLee on 2009-11-04
> **kansasnoob said:**
> I was thinking somewhat along the same lines. I was thinking of taking the lazy way out and doing "sudo mv /boot/grub/menu.lst /boot/grub/menu.lst_old" then running "sudo update-grub" which should then ask to create a new menu.lst, just say yes and see what the new list looks like ;)

But it looks like we're going a different direction now.


I'm not sure we are, I think this is what OP is currently proposing except for the backup of menu.lst

Should work.

---

### Post by dbuehler on 2009-11-04
Success!

I went back over what I had done this morning and see where I went wrong.  Answer #15 has the fix but somehow I didn't end up actually editing menu.lst.  I'm still a newbie but hopefully I am learning.  :-)

Anyway, I got it now loading the correct kernel and my sound works. 

Thanks for all the help!

Dan

---

