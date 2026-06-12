---
title: "No sound card"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by milesorvana on 2009-11-08
Ok, for the past couple days i have had issues with my sound since i upgraded to Karmic. However thanks to another thread i found out that my comp is not picking up my sound card. How would i make it recognize my sound card?

---

### Post by Lateralis on 2009-11-08
Hmmm... Not detected at all?  What is your hardware? 

Can you post the output of 

```

sudo lshw -C multimedia

```

---

### Post by milesorvana on 2009-11-08
*-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:302c0000-302c3fff

---

### Post by Lateralis on 2009-11-08
Looks like Ubuntu is able to pick up the sound card and looks like it is using the correct driver.  Just to double check, what happens if you type 

```

lsmod | grep snd_hda_intel

```

You should have a line that looks like 

```

snd_hda_intel          31880  2 

```

in addition to a few other lines.  If you do have that line above, then I believe the correct module is being loaded into the kernel, so in principle the sound card should work. (I think!)

Now, that being said, I did have some problems with the sound on my laptop after I upgraded from Jaunty to Karmic the other week.  The sound card in my laptop is an Intel HDA card, similar, although not identical, to your own.  For me my sound would sometimes work, otherwise it wouldn't, upon booting into Ubuntu. It all now seems quite happy after installing a large array of updates in the last 10 days.  It may well be that there is an update in the proposed repository that has fixed the issue.  But as a first check, let see if the correct module is being loaded into the kernel.

---

### Post by milesorvana on 2009-11-08
This is what i got.

```
snd_hda_intel         434100  0 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
```

---

### Post by Lateralis on 2009-11-08
Well, I think I now have to admit that I'm not sure what is going on.  Looks like the module is being loaded up, but whereas you get 434100 0 next to it (size of module and the "used by") I get 31880  2 and on two separate machines.  

So, now I'm just shooting from the hip... Can you type *uname -r* into the command line.  This will tell us what kernel you're using.  I'm using 2.6.31-14-generic.  The other potential thing to try is enable the proposed repository and try updating your system through that, assuming the proposed repository isn't already enabled in your software sources list.  Again, that is just a guess - may work, may not... but I'm a physicist... I experiment!

---

### Post by milesorvana on 2009-11-08
this is the result of typing ```
uname -r
```
```
2.6.28-13-generic
```

---

### Post by Lateralis on 2009-11-08
Perhaps that is it?  Having an older kernel.  

There appears to be a newer kernel in the main repos.  Could try upgrading to that kernel perhaps?

---

### Post by milesorvana on 2009-11-08
now how would i update it?

---

### Post by Lateralis on 2009-11-08
Ah ha!  Well, for me, this sort of stuff just kinda happens.  =P  

Anyway, I would hope that Ubuntu would update itself frequently (default is to check daily for updates) and update the kernel too.  But we can check where you get your updates from and how often your system checks for updates.   

System -> Administration -> Software packages

Make sure that under the Ubuntu Software tab that the "main" and "universe" tabs are checked; that under the updates tab the karmic-security and karmic-updates options are also checked and that "check for updates" is checked and that "daily" is selected from the drop down menu.

Then in the command line type 

```

sudo aptitude update
sudo aptitude full-upgrade

```

With any luck, you'll see an update for the linux kernel in the list of possible updates you'll see some updates looking something like "linux-headers-2.6.31-15".  

*crosses fingers*

---

### Post by milesorvana on 2009-11-08
now i typed in what you said to in the terminal and made sure everything was checked off, and this is what it gave me.```
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release             
Hit http://security.ubuntu.com karmic-security/main Packages        
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources

``` then after the next thing i got this. ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

---

### Post by Lateralis on 2009-11-09
Try adding the poposed repository and doing that again.  

So go through the steps I mentioned in my previous post and under the Upates tab of the Software Sources GUI select the proposed updates.  Then try updating and upgrading again.  There is definitely an updated kernel in the proposed repository (I updated my home PC to that kernel yesterday).

---

### Post by Lateralis on 2009-11-09
OK, I've just been [looking over the forum]("http://ubuntuforums.org/showthread.php?t=1307491"), and I *may* have found out what has happened.  It is possible that you have downloaded the updated kernels (2.6.31-**) but that they haven't been correctly added to your grub boot menu list.  This would mean that they are installed on the system but you can't select at startup.  This is purely a guess, but we can easily check for that.  Can you post the outputs of:

```

ls /boot | grep vmlinuz
cat /boot/grub/menu.lst

```


As you've upgraded from Jaunty to Karmic, I'll assume that your grub is not the grub 2 beta.  If it is the beta then I'm not sure how I can help you as I'm still on the old grub and as I understand it Grub 2 won't make use of menu.lst.  You can determine your grub version by typing ```
grub --version
``` into the command line; mine is 0.97.

If after running those two commands above you find that you have more kernels (vmlinuz files) than you have listed in grub's menu.lst, ie. you have kernels sitting there that aren't given you as options to boot from at start up, then you could try running *update-grub* from the command line.  Before you do that, it is probably a good idea to make a backup copy of menu.lst to ensure against any failures or errors. 

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old.backup # make a backup of menu.lst in the same directory
sudo update-grub # update grub using built in programme

```

This is for versions of grub that aren't the version 2 beta.  For version two, you can use 

```

sudo update-grub2

```

but as I've said I have never used grub version 2 so have no idea what doing that will actually do!

---

### Post by milesorvana on 2009-11-09
```
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=92772d02-854a-4853-92ae-547db93b5ebf

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows 95/98/NT/2000
root        (hd0,0)
makeactive
chainloader    +1
```

```
grub (GNU GRUB 0.97)
```
(By the way, i appreciate all the help so far. Everyone else just told me to search the forums and i have no idea what all this stuff means ^_^")

---

### Post by Lateralis on 2009-11-09
Hehe.  No problem at all... but don't thank me just yet... you still don't have sound! :P  

Anyway, can you also just post the output of the other command I mentiond: 

```

ls /boot | grep vmlinuz

```

---

### Post by milesorvana on 2009-11-09
Still... your putting an effort to help me out here.

```
vmlinuz-2.6.28-13-generic
vmlinuz-2.6.31-14-generic
```

---

### Post by Lateralis on 2009-11-10
Ah ha!  So, it looks like you have the updated kernel, but it hasn't been added to the grub boot menu.  It also looks like the older kernel (2.6.28-11) is no longer installed on your system but is still an option to boot from.  How kooky!  

Anyway, I believe this is easy to change.  Firstly, make a backup of this menu.list in case something goes wrong: 

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.9.04.backup

```

This will mean that should something screw up, you can easily move it back and all will be fine.  

Next, try running

```

sudo update-grub

```

This will initiate a script to update the grub boot menu by looking in /boot/ to determine what kernels you have.  If you then look at menu.lst again

```

cat /boot/grub/menu.lst | grep vmlinuz

```

you should see 4 lines and two different kernels listed, specifically:


kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b4670964-2580-44af-98da-bc993cd87397 ro quiet splash 
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=b4670964-2580-44af-98da-bc993cd87397 ro  single
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b4670964-2580-44af-98da-bc993cd87397 ro quiet splash 
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b4670964-2580-44af-98da-bc993cd87397 ro  single

If that is not the case, then update-grub hasn't done is thang and hasn't updated menu.lst properly.  In which case, we'll have to do it by hand.  


To do it by hand, you will need to edit menu.lst directly.  You should already have a backup copy of the "good" file, so we can simply proceed with editing the file:

```

gksudo gedit /boot/grub/menu.lst

```

Scroll down the file until you reach "## ## End Default Options ##".  Just underneath this add the following:

```

title        Ubuntu 9.04, kernel 2.6.31-14-generic
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,4)
uuid        92772d02-854a-4853-92ae-547db93b5ebf
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=92772d02-854a-4853-92ae-547db93b5ebf ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

```

If you wish, you can then delete the two entries in menu.lst which is listed as using the 2.6.28-11 kernel.  


Then try rebooting into the newer kernel.  I can in no way guarantee that this newer kernel will suddenly give you sound back, but I believe it helped fix my sound problems. :)

If, after all that, you find that your sound still doesn't work, then the next thing to try is updating packages through the proposed repository.  This is something that I do all the time.  Under System->Administration->Software sources, select the updates tab and check the "proposed updates (karmic-proposed)" option.  Then in a terminal:

```

sudo aptitude update
sudo aptitude safe-upgrade

```

You'll see a list of package updates; it may be quite long.  This will update any packages you have on your system using updates that have been proposed but haven't yet been migrated over to the main repository.  If you're unhappy about updating everything you see, you could post the output of the safe-upgrade command and we can see if there is a package update that might fix the sound.

---

### Post by milesorvana on 2009-11-10
Ok, so i did the first thing you told me and it did it all fine. I didn't have to do it manually. however after the reboot the sound didn't work still. So i moved on to the next thing and here is what i got.

```
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Get:1 http://security.ubuntu.com karmic-security Release.gpg [189B]
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com karmic-security Release [37.1kB]
Hit http://us.archive.ubuntu.com karmic Release    
Get:4 http://us.archive.ubuntu.com karmic-updates Release [44.1kB]
Hit http://us.archive.ubuntu.com karmic/main Packages                        
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Get:5 http://security.ubuntu.com karmic-security/main Packages [11.5kB]
Get:6 http://us.archive.ubuntu.com karmic-updates/main Packages [52.0kB]
Get:7 http://us.archive.ubuntu.com karmic-updates/restricted Packages [14B] 
Get:8 http://us.archive.ubuntu.com karmic-updates/main Sources [18.9kB]
Get:9 http://security.ubuntu.com karmic-security/restricted Packages [14B]
Get:10 http://security.ubuntu.com karmic-security/main Sources [3,962B]    
Get:11 http://security.ubuntu.com karmic-security/restricted Sources [14B]      
Get:12 http://security.ubuntu.com karmic-security/universe Packages [5,432B]    
Get:13 http://security.ubuntu.com karmic-security/universe Sources [793B]       
Get:14 http://security.ubuntu.com karmic-security/multiverse Packages [14B]     
Get:15 http://security.ubuntu.com karmic-security/multiverse Sources [14B]      
Get:16 http://us.archive.ubuntu.com karmic-updates/restricted Sources [14B]     
Get:17 http://us.archive.ubuntu.com karmic-updates/universe Packages [24.3kB]
Get:18 http://us.archive.ubuntu.com karmic-updates/universe Sources [4,672B]
Get:19 http://us.archive.ubuntu.com karmic-updates/multiverse Packages [14B]
Get:20 http://us.archive.ubuntu.com karmic-updates/multiverse Sources [14B]
Fetched 203kB in 1s (139kB/s) 
```

---

### Post by milesorvana on 2009-12-07
Can someone please help me? I have been trying everything i can find here on the fourms and nothing is working. i am still without sound.

---

### Post by bejurne on 2009-12-20
I seem to have the same problem. Did you find any solution yet?

The card shows up in lspci:
```
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
```

The required modules seem to run as well:
```
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_pcm                75296  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    59204  17 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```

It does not show in audio preferences though. The hardware tab shows no devices at all. The list is completely empty...

Any ideas? I really need my sound back.

---

