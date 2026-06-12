---
title: "From 9.04 to 9.10: no sound!"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by OllieGab on 2009-10-31
So I upgraded from 9.04 to 9.10 and everthing seems to be working - except the sound. Tried various sites and played video clips; no sound.

Booted up XP (dual boot), sound works fine, so it is obviously the upgrade...
Suggestions, anyone?

Cheers
Ollie

---

### Post by jrrader on 2009-10-31
Well, for some reason the sound was muted on mine when I first started it up.  I'm guessing you already checked that.

---

### Post by humphreybc on 2009-10-31
Karmic has changed from Alsa audio to Pulse Audio by default, and, you're not alone. Many people are having problems with pulse audio.

Hang tight, i'm sure someone who knows more about pulse than I do will be able to help you out in a jiffy!

---

### Post by PippoFranco on 2009-10-31
I have the same problem, I made a fresh install of 9.10 on my ACER TravelMate 8200 and I have no sound at all. It is funny, with a trial with the beta everything was working aoutn of the box.
[SOLVED] I have installed the SUN VirtualBox, the installation forced a kernell recompile and thi made the sound OK

---

### Post by Jatepola on 2009-10-31
I'm getting the same error. Just after upgrading from 9.04 to 9.10 I got no sound. Help!

---

### Post by braete on 2009-10-31
you migh try this:

in sound preferences under hardware tab check if ur soundcard had a proper profile (you might have some hdmi device so ur sound card isnt set as analog-stereo-duplex)

or instal gnomealsamixer(if any tabs chose the one with the name of ur soundcard) and check there if master or pcm is muted (this fixed my microphone issues, as it was muted, but i guess this might also be the case with the lack of sound)

---

### Post by OllieGab on 2009-10-31
In my hardware tab (sound preferences) there is absolutely nothing there.
The 'Choose a device to configure' field is empty!

---

### Post by braete on 2009-10-31
> **OllieGab said:**
> In my hardware tab (sound preferences) there is absolutely nothing there.
The 'Choose a device to configure' field is empty!

ohoo, so pulse doesnt see any soundcard :confused:

run in a terminal aplay -l and post output

---

### Post by jinny on 2009-10-31
Same problem... this is my output:

aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by Spice Weasel on 2009-10-31
I have exactly the same problem X_X

---

### Post by NCLI on 2009-10-31
Report bugs, please, all of you. Just go to System->Administration->System Testing, then make sure to submit a bug once you reach the part where it tests whether sound is working.

Reporting this means that it will probably be fixed quickly, since this is obviously a regression.

---

### Post by OllieGab on 2009-10-31
> **jinny said:**
> Same problem... this is my output:

aplay -l
aplay: device_list:223: no soundcards found...

Identical to my output!

---

### Post by braete on 2009-10-31
> **NCLI said:**
> Report bugs, please, all of you. Just go to System->Administration-System Testing, then make sure to submit a bug once you reach the part where it tests whether sound is working.

Reporting this means that it will probably be fixed quickly, since this is obviously a regression.

^this

the os doesnt "see" ur soundcards at all if they dont appear even in alsa.

if they where to be in that alsa list it should be easy to properly configure pulse if that where to be the problem

on a sidenote.
try a clean install or boot in live mode and try sound
i noticed that 9.10 doesnt use some alsa related files (.asounrc)and that some pulse audio components are obsolete (pamanager and padevchooser)

---

### Post by alunparry on 2009-10-31
no sound here either, although my Sound Preferences/Hardware tab does list things:

c0001
Internal Audio
SAA7131/SAA7133/SAA7135 Video Broadcast Decoder

But no sound since the upgrade. All worked great beforehand.

---

### Post by BFG on 2009-10-31
I get this too. No sound driver.

> **NCLI said:**
>  then make sure to submit a bug
Unfotunately, clicking bug report results in the system Testing app crashing out.

I think I'm going to re-install.  This is one of about a dozen problems.

---

### Post by alonc on 2009-10-31
I also have no sound after upgrade.
No sound card at the “Sound Preferences” Hardware tab
I fixed it by editing the default.pa file:
```
sudo gedit /etc/pulse/default.pa
```
and uncomment lines 45 and 46
```

load-module module-alsa-sink
load-module module-alsa-source device=hw:0,1

```
saved it and reboot.

Now sound is working but still no sound card at the Hardware list.
[LEFT] 
[FONT=Times New Roman, serif] [/FONT][/LEFT]

---

### Post by Cardcaptor Stacey on 2009-10-31
Mine sound keeps dying and coming back on. I get weird clicking noises when I turn my speakers on.

---

### Post by NCLI on 2009-10-31
> **BFG said:**
> I get this too. No sound driver.


Unfotunately, clicking bug report results in the system Testing app crashing out.

I think I'm going to re-install.  This is one of about a dozen problems.
Uh, wow. I guess you'll have to report a bug for System testing then, please do this before re-installing:

"ubuntu-bug checkbox-gtk"

For the rest of you: [COLOR=Red]_**PLEASE USE "SYSTEM TESTING" TO REPORT BUGS FOR YOUR AUDIO PROBLEMS!!!**_[/COLOR]

---

### Post by johngrey on 2009-10-31
I had the same thing - sound output was set to 'dummy', nothing else in any of the options, no relevant settings in alsamixer

This suggestion from BAiHAX in [this thread]("http://ubuntuforums.org/showthread.php?t=1243064&page=2") worked for me.

------------------------------------------------

[INDENT]# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
[/INDENT]

---

### Post by abooks on 2009-10-31
Same here: no sound card detected. No volume control on bottom tool bar either. I suppose reporting bugs is different in Kubuntu?

---

### Post by camaron1 on 2009-10-31
I had the same problem. I uninstalled Pulse audio and installed esound. This worked for me, my sound is back. This is a pulse audio bug that hopefuly will be sorted soon.

---

### Post by jinny on 2009-10-31
> **camaron1 said:**
> I had the same problem. I uninstalled Pulse audio and installed esound. This worked for me, my sound is back. This is a pulse audio bug that hopefuly will be sorted soon.

How did you do it? I've tried to install esound from Synaptic but it says it's going to remove also ubuntu-desktop besides pulseaudio... :(

---

### Post by camaron1 on 2009-10-31
> **jinny said:**
> How did you do it? I've tried to install esound from Synaptic but it says it's going to remove also ubuntu-desktop besides pulseaudio... :(

Remove ubuntu-desktop for installing esound or uninstaling pulse audio? To be honest, not sure that installing esound is essential. I just folled advice from launchpad, someone had done and it worked. It worked for me too. But I suppose the important thing is to remove pulse audio. This is a sound server, it does not have the actual drivers (that is Alsa), it only serves the sound to different apps. so esound might no be necessary. 

On the other hand at some point I also removed ubuntu-desktop (The upgrade to 9,10 has given me more than one problem) but I think this is only a metapackage, it is not vital. My system is working OK now.

Good luck, tell us how it goes

---

### Post by the.drizzle on 2009-10-31
I've now had the same problem, but fixed it in a different way...

For some reason, the upgrade simple made a directory /boot/ and put the new kernel (2.6.31-14) image in there.  Thus, when I actually started the system, grub didn't find this new image, as the /boot/ path is supposed to be at /dev/sdc1/, not a sub-folder of /dev/sdc3.

Simple solution--copy the contents of the newly-created /boot/ directory to where they are supposed to be, fix menu.lst and /etc/fstab to match reality, and delete /boot (the newly created one) for good measure.

Restarted and everything is super!

---

### Post by nelio2k on 2009-11-01
For Dell Mini-9's or A90 uses the following line needs to be added /etc/modprobe.d/alsa-base.conf to fix the sound.

options snd-hda-intel model=dell

After the line is added, then then sound should work after a restart.

---

### Post by OllieGab on 2009-11-01
> **the.drizzle said:**
> I've now had the same problem, but fixed it in a different way...

For some reason, the upgrade simple made a directory /boot/ and put the new kernel (2.6.31-14) image in there.  Thus, when I actually started the system, grub didn't find this new image, as the /boot/ path is supposed to be at /dev/sdc1/, not a sub-folder of /dev/sdc3.

Simple solution--copy the contents of the newly-created /boot/ directory to where they are supposed to be, fix menu.lst and /etc/fstab to match reality, and delete /boot (the newly created one) for good measure.

Restarted and everything is super!

I'm not quite sure of what all the above means (or what to do with it) but after looking at my menu.lst file I discovered that 9.10 was not mentioned there at all (should have updated automatically during upgrade, surely?) I added another option, identical to the first one on the list, but changed the kernel version to 2.6.31-14 in all relevant places, and after re-booting my sound was back! However, some of my computer's settings seem to have been affected, eg I can't see my desktop icons, or my desktop picture: background totally black! Though I know my icons are there somewhere in the background as I can click on them (or where I think they are!) and check their properties!

---

### Post by fidelandche on 2009-11-01
This worked for me,

  # first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

---

### Post by Tholley on 2009-11-01
> **fidelandche said:**
> This worked for me,

  # first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

Tried this, still nothing for me.

> I've now had the same problem, but fixed it in a different way...

For some reason, the upgrade simple made a directory /boot/ and put the new kernel (2.6.31-14) image in there. Thus, when I actually started the system, grub didn't find this new image, as the /boot/ path is supposed to be at /dev/sdc1/, not a sub-folder of /dev/sdc3.

Simple solution--copy the contents of the newly-created /boot/ directory to where they are supposed to be, fix menu.lst and /etc/fstab to match reality, and delete /boot (the newly created one) for good measure.

Restarted and everything is super! 	  	

So how do you go about this?

---

### Post by svenni on 2009-11-01
Have you checked that you are using the latest kernel?

After the upgrade I could not get any sound either, and I tried everything from deleting pulse settings in ~/.pulse and change stuff in /etc/modprobe.d/alsa-base.conf, yet nothing made my sound card appear.

Then I booted a live CD, and I suggest you do this to see if it is your settings or Karmic itself which is having problems. The live CD played sound perfectly, so I figured there was something wrong with my install.

Then I had a look at System > Administration > System Monitor, looked at the System tab, and realized the kernel installed was 2.6.28.

To upgrade the kernel to 2.6.31 I went to System > Administration > Synaptic and uninstalled 2.6.28, and reinstalled 2.6.31.

Now my sound works perfectly fine.

---

### Post by Tholley on 2009-11-02
Sorry for taking so long to reply, I couldn't logon again yesterday for some reason.

> To upgrade the kernel to 2.6.31 I went to System > Administration > Synaptic and uninstalled 2.6.28, and reinstalled 2.6.31.

So how do you do this? I saw where I have 2.6.28, but did not see 2.6.31 anywhere in Synaptic.

---

### Post by the.drizzle on 2009-11-02
> **Tholley said:**
> Tried this, still nothing for me.



So how do you go about this?

Sorry for the slow reply...

Basically, it seems to come back to how your system is set up.  I have my main hard drive partitioned into four:

/dev/sdc1  /boot
/dev/sdc2  (swap)
/dev/sdc3  /
/dev/sdc4  /home

when upgrading to 9.10, the upgrade tool seems to have copied the new kernel image to the folder /boot/  In other words, the kernel (and the associated menu.lst file) were written to /dev/sdc3/ not /dev/sdc1 where they were supposed to be put.

To fix this, simply make a temporary mount point for the actual /boot/ device, and go there:

```

$sudo mkdir /mnt/tempboot
$sudo mount /dev/<your boot sector> /mnt/tempboot
$sudo cp /boot/*31* /mnt/tempboot/
$sudo mv /mnt/tempboot/menu.lst /mnt/tempboot/menu.lst.old
$sudo cp /boot/menu.lst /mnt/tempboot/
$sudo umount /mnt/tempboot

```

And then re-start your computer.

The re-naming of the old menu.lst file is to give you a fallback if the new one fails, and you should also check where /etc/fstab is mounting /boot--fix it if need be.

Once that's all done, wipe out the contents of the new (useless!) /boot drive, and restore it to being a mountpoint as it's meant to be.

Cheers!

---

### Post by Tholley on 2009-11-02
You may have to hold my hand on this... ;)

> To fix this, simply make a temporary mount point for the actual /boot/ device, and go there:

How do I do this? Just create a new folder?

---

### Post by the.drizzle on 2009-11-02
I've written the instructions in the post.

(That is, the commands I wrote are to be entered at the command line...)

;)

---

### Post by Tholley on 2009-11-02
Just copy and paste this in terminal?

 	Code:
 	$sudo mkdir /mnt/tempboot
$sudo mount /dev/<your boot sector> /mnt/tempboot
$sudo cp /boot/*31* /mnt/tempboot/
$sudo mv /mnt/tempboot/menu.lst /mnt/tempboot/menu.lst.old
$sudo cp /boot/menu.lst /mnt/tempboot/
$sudo umount /mnt/tempboot 


What about <your boot sector> 

Sorry if I seem dimwitted... windows for years and years...

---

### Post by the.drizzle on 2009-11-02
It depends on how your hard drive is partitioned; this solution may not even be appropriate for you.

Where is your /boot partition?  That is, please post the output of:

```

$ more /etc/fstab | grep boot

```

This may or may not be the best thing to look at, but it's a starting point...

EDIT:

Also, what is the output of

```

$ uname -r

```

---

### Post by Tholley on 2009-11-02
Thanks for all the help...

I'm at a diff computer right now, but am booting up the 9.10 right now and will be back with you in a jiffy.

---

### Post by Tholley on 2009-11-02
> **the.drizzle said:**
> It depends on how your hard drive is partitioned; this solution may not even be appropriate for you.

Where is your /boot partition?  That is, please post the output of:

```

$ more /etc/fstab | grep boot

```This may or may not be the best thing to look at, but it's a starting point...

EDIT:

Also, what is the output of

```

$ uname -r

```

I copied and pasted in terminal "command not found"

for either

---

### Post by the.drizzle on 2009-11-02
> **Tholley said:**
> I copied and pasted in terminal "command not found"

for either

you know that you don't include the $ character, right?

---

### Post by Tholley on 2009-11-02
oops... no I didn't :(

Try again...

---

### Post by Tholley on 2009-11-02
1st one nothing, 2nd ?

terrell@terrell-bedroom:~$ more /etc/fstab | grep boot
terrell@terrell-bedroom:~$ uname -r
2.6.28-15-generic
terrell@terrell-bedroom:~$

---

### Post by the.drizzle on 2009-11-02
> **Tholley said:**
> 1st one nothing, 2nd ?
terrell@terrell-bedroom:~$ uname -r
2.6.28-15-generic
terrell@terrell-bedroom:~$

OK, there's your problem; you're not loading up the new 2.6.31 kernel, hence the alsa modules not loading either.

You need to edit your menu.lst file to load the correct kernel, and I have a hunch you've got the new (correct) file sitting somewhere where grub is not seeing it.

So that I can give you step-by-step instructions, I need to know a few things.

First, what is the output of
```

$ls /boot

```

and also, it would be handy to know your partition table.  Please paste the output of

```

$sudo sfdisk -l /dev/sda

```

(or whatever the label of your hard drive is, i.e., sda, sdb, etc...)  This will allow you to see where the actual boot device is; it's then your job to copy the 2.6.31 kernel onto that sector, as well as the new menu.lst file.

EDIT:

Actually, since it will speed this up, can you also post the output of
```

$cat /etc/fstab

```

---

### Post by Tholley on 2009-11-02
terrell@terrell-bedroom:~$ $ls /boot
bash: /boot: is a directory
terrell@terrell-bedroom:~$

1st one

---

### Post by Tholley on 2009-11-02
oops...

errell@terrell-bedroom:~$ $ls /boot
bash: /boot: is a directory
terrell@terrell-bedroom:~$ 
terrell@terrell-bedroom:~$ ls /boot
abi-2.6.28-15-generic         memtest86+.bin
abi-2.6.31-14-generic         System.map-2.6.28-15-generic
config-2.6.28-15-generic      System.map-2.6.31-14-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.28-15-generic
grub                          vmcoreinfo-2.6.31-14-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
terrell@terrell-bedroom:~$

---

### Post by Tholley on 2009-11-02
2
terrell@terrell-bedroom:~$ sudo fdsik /dev/sda
sudo: fdsik: command not found
terrell@terrell-bedroom:~$

---

### Post by Tholley on 2009-11-02
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5a577036-cb78-488c-8995-94347ea45635 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
terrell@terrell-bedroom:~$

---

### Post by the.drizzle on 2009-11-02
OK, easy enough.  Please post the output of 

```

$sudo cat /boot/menu.lst

```

And I can show you what needs to change.

---

### Post by jinny on 2009-11-03
I've been able to enable audio for the 2.6.31 kernel but I'm stuck with the 2.6.28 for video card issues...is there anyway to make audio work also with this older kernel?

---

### Post by Tholley on 2009-11-03
> **the.drizzle said:**
> OK, easy enough. Please post the output of 
 
```

$sudo cat /boot/menu.lst

```
 
And I can show you what needs to change.
 
Sorry... got too tired and had to hit the hay last night.
 
I'll continue this evening when I get back home from work.
 
Thanks again...

---

### Post by camaron1 on 2009-11-03
> **Tholley said:**
> Sorry for taking so long to reply, I couldn't logon again yesterday for some reason.



So how do you do this? I saw where I have 2.6.28, but did not see 2.6.31 anywhere in Synaptic.


I think it's called linux-image 2.6.31 or something very similar. I had to do it myself too (but didn't fixed the sound, removeing pulseaudio did). Sorry I'm at work just now and can't be more specific.

---

### Post by svenni on 2009-11-03
> **Tholley said:**
> Sorry for taking so long to reply, I couldn't logon again yesterday for some reason.



So how do you do this? I saw where I have 2.6.28, but did not see 2.6.31 anywhere in Synaptic.

**Edit:** Sorry, it seems I forgot to mention the full package name in my first post. It is *linux-image-2.6.31-14-generic*.

Here is how you may try to install it from a terminal window:

Run
```
sudo apt-get update
```
to make sure you are up-to-date with all your packages.

Then, try to run
```
sudo apt-get install linux-image-2.6.31-14-generic
```

If this fails, try to change your package server. You might do this by going to System > Administration > Software Sources and set "Download from:" to "Main server". I don't think this should affect anything, but it is worth the try.

Then run the two commands above once more.

If the commands works, try to remove the 2.6.28 image.

Good luck :) And please tell us what fixes your problem in the end.

---

### Post by Tholley on 2009-11-03
I should be able to let you know some results in a couple of hours from now.
 
Been a long day at work!  :mad:

---

### Post by Tholley on 2009-11-03
> **the.drizzle said:**
> OK, easy enough.  Please post the output of 

```

$sudo cat /boot/menu.lst

```And I can show you what needs to change.

Drizzle... No such file

```
terrell@terrell-bedroom:~$ sudo cat /boot/menu.lst
[sudo] password for terrell: 
cat: /boot/menu.lst: No such file or directory
terrell@terrell-bedroom:~$ 
```

---

### Post by Tholley on 2009-11-03
> **svenni said:**
> **Edit:** Sorry, it seems I forgot to mention the full package name in my first post. It is *linux-image-2.6.31-14-generic*.

Here is how you may try to install it from a terminal window:

Run
```
sudo apt-get update
```to make sure you are up-to-date with all your packages.

Then, try to run
```
sudo apt-get install linux-image-2.6.31-14-generic
```If this fails, try to change your package server. You might do this by going to System > Administration > Software Sources and set "Download from:" to "Main server". I don't think this should affect anything, but it is worth the try.

Then run the two commands above once more.



If the commands works, try to remove the 2.6.28 image.

Good luck :) And please tell us what fixes your problem in the end.


Does this mean anything?
```
terrell@terrell-bedroom:~$ sudo apt-get install linux-image-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.31-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libwildmidi0 libsoundtouch1c2 libopenspc0 libfftw3-3 binutils-static
  python-speechd liblouis0 freepats python-louis libkate1 libcdaudio1
  libmimic0 pulseaudio-module-zeroconf libgconfmm-2.6-1c2 liblouis-data
  pavumeter libglademm-2.4-1c2a libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
terrell@terrell-bedroom:~$ 
```

---

### Post by the.drizzle on 2009-11-03
Then find it first!

```

$locate menu.lst

```

The above stuff you posted is useless, as we've already established that the 2.6.31 kernel is on your system.  The problem is that your bootloader (presumably grub) is pointing at the old one.  Thus, you need to edit one or two lines in the file menu.lst to point it to the correct file, which you've already shown above is there, waiting to be used.

---

### Post by Tholley on 2009-11-03
Does this help any?

locate menu.lst
/boot/grub/menu.lst
/boot/grub/menu.lst.backup
/boot/grub/menu.lst~
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/var/lib/ucf/cache/:var:run:grub:menu.lst
terrell@terrell-bedroom:~$

---

### Post by the.drizzle on 2009-11-03
```

$cat /boot/grub/menu.lst

```

Also, it would still help to also have the output of
```

$sudo sfdisk -l /dev/sda

```

---

### Post by Tholley on 2009-11-03
terrell@terrell-bedroom:~$ cat /boot/grub/menu.lst
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
timeout        6

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=809153b0-44a1-492f-a1ed-f17a5d218e4a

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
# defoptions=quiet splash vga=795

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic


title        Ubuntu 9.04, memtest86+
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

terrell@terrell-bedroom:~$ sudo sfdisk -l /dev/sda
Disk /dev/sda: 36481 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  15667   15668- 125853178+   7  HPFS/NTFS
/dev/sda2      15668   36479   20812  167172390    f  W95 Ext'd (LBA)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      31871+  36479    4609-  37021761    7  HPFS/NTFS
        start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      15668+  31496   15829- 127146379+  83  Linux
/dev/sda7      31497+  31870     374-   3004123+  82  Linux swap / Solaris
terrell@terrell-bedroom:~$

---

### Post by the.drizzle on 2009-11-03
OK, re-name your existing menu.lst file
```

$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old.kernel

```

Copy the below, save it as /boot/grub/menu.lst, and reboot.  Soundcard may need to be un-muted, but should work fine.

```

default        0                            
timeout        6                            
color cyan/blue white/blue                  

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a  
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.31-14-generic                                                                     
quiet                                                                                                                

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a  
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro quiet splash vga=795 
initrd        /boot/initrd.img-2.6.28-15-generic                                                                     
quiet                                                                                                                

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a                  
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=809153b0-44a1-492f-a1ed-f17a5d218e4a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic                                                       


title        Ubuntu 9.04, memtest86+
uuid        809153b0-44a1-492f-a1ed-f17a5d218e4a
kernel        /boot/memtest86+.bin              
quiet                                           

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by Tholley on 2009-11-03
Save it to where?

---

### Post by the.drizzle on 2009-11-03
Aurrgh!
> **the.drizzle said:**
>  save it as /boot/grub/menu.lst

Copy the above, and type:
```

$sudo nano -w /boot/grub/menu.lst

```

and paste via <shift> + <insert>.  Then hit <ctrl> + <x> to save and exit nano.  Then reboot.  Then un-mute your sound-card if necessary.

---

### Post by Tholley on 2009-11-03
Sorry for the aggravation, but I am in the Beginners talk for a reason. ;)

Ok... I went to file system, then opened the boot folder, then grub, I do not have an option to paste (it is greyed out even tho I did copy your text). It will not let me. There are 2 menu.lst... 1 = menu.lst.backup and 2 = menu.lst.old.kernel.

What the heck should I be doing?

---

### Post by the.drizzle on 2009-11-03
I realize it's the biginners area, but you're simply not following my instructions, hence the frustration.

Open a terminal, and type:
```

$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.9.04

```

Which you don't even have to do, it's a safety step.  Once you do that, follow the directions in my last post for inserting the fixed menu.lst file I've posted.  Then reboot, then un-mute your soundcard if necessary.

---

### Post by Tholley on 2009-11-03
> **the.drizzle said:**
> I realize it's the biginners area, but you're simply not following my instructions, hence the frustration.

Open a terminal, and type:
```

$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.9.04

```Which you don't even have to do, it's a safety step.  Once you do that, follow the directions in my last post for inserting the fixed menu.lst file I've posted.  Then reboot, then un-mute your soundcard if necessary.

Sorry dude but something just aint working. I copied and pasted your command and ...

terrell@terrell-bedroom:~$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.9.04
mv: cannot stat `/boot/grub/menu.lst': No such file or directory
terrell@terrell-bedroom:~$

---

### Post by the.drizzle on 2009-11-03
I've PM'd you.

---

### Post by fher98 on 2009-11-04
> **the.drizzle said:**
> I realize it's the biginners area, but you're simply not following my instructions, hence the frustration.

Open a terminal, and type:
```

$sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.9.04

```

Which you don't even have to do, it's a safety step.  Once you do that, follow the directions in my last post for inserting the fixed menu.lst file I've posted.  Then reboot, then un-mute your soundcard if necessary.

So what happend???

---

### Post by Louigi Verona on 2009-11-04
I've updated from 9.04 to 9.10 and there was no sound.
Updated the grub to grub2 - and the sound came back since I was now loading the correct kernel.

HOWEVER

sometimes the sound would disappear again. I would check - the correct kernel is loaded but the sound isn't there.

When the sound is there - for some reason TWO sound devices are displayed in the system - internal audio and some analog audio - though I have just one internal soundcard in my laptop.
When the sound isn't there - only one sound device is shown.

All in all, very frustrating, I must say. At this moment I am not very happy about moving to Karmic as it seriously disrupted my work. I now need things to be done but I am here trying to get back sound and DSL connection.

---

### Post by svenni on 2009-11-04
It appears that you already have both kernels installed. If you find editing the /boot/grup/menu.lst file a bit tricky, I suggest you try uninstalling the 2.6.28 kernel and reinstall the 2.6.31 kernel.

Go to System > Administration > Synaptic and search for linux-image in the "Quick search".

Right click the one named linux-image-2.6.28-15-generic and click "Mark for removal".

Right click the one named linux-image-2.6.31-14-generic and click "Mark for reinstallation".

Then hit the Apply button in Synaptic.

Should it ask you if you want to keep or update the menu.lst file, choose to update it with the one from the package manager.

Otherwise I would suggest you keep try to update the menu.lst file, but I would rather use the command

```
gksu gedit /boot/grub/menu.lst
```

to edit it, since nano is a bit hard to use if you have never used a terminal text-editor.

---

### Post by Tholley on 2009-11-04
> **fher98 said:**
> So what happend???
 
at the bottom of post #63, i copied from terminal "no such file or directory", so something didn't go right. Got an email from drizzle that copied better and opened up a blank menu.lst.
 
copied and pasted new menu, but didn't paste correctly, and I think wiped out grub, since after reboot, just got a black screen for typing commands, typed boot, got error 8, something about kernel not being loaded.
 
Should be able to go back in and fix it all using Live CD tonight.
 
Once I have success, I will post the correct fix. (at least for my sound problem)

---

### Post by Tholley on 2009-11-04
>  
Otherwise I would suggest you keep try to update the menu.lst file, but I would rather use the command


Code:
gksu gedit /boot/grub/menu.lst
to edit it, since nano is a bit hard to use if you have never used a terminal text-editor.

 
I think that is what drizzle was trying to get me to do, but somehow I managed to screw it up.

---

### Post by Bunnybugs on 2009-11-04
Everyone has that problem... you can go back to alsa...

Here is the ultimate description to do that: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Tholley on 2009-11-04
> **Bunnybugs said:**
> Everyone has that problem... you can go back to alsa...
 
Here is the ultimate description to do that: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
I beleive this was the first thing I tried, and did not work for me.

---

### Post by Bunnybugs on 2009-11-04
L0Lz...

It worked a couple a days for me, but just rebooted and lost sound again... it works again now;) it&#347; not perfect... but 2 codes to remember isn't that kinda hard

---

### Post by Tholley on 2009-11-04
Waiting on Drizzle to email me how to edit the menu.lst files thru Live CD.

I cant access anything now during bootup except a black screen that only use cmds.

So I am in live CD now, but not sure how to access the menu.lst, much less edit it in live CD.

Any other help while I'm waiting? He is in a different country so don't know the time diff.

---

### Post by Tholley on 2009-11-05
update on sound issue. I'm not sure this will help anyone, but I will give a brief of what fixed the sound problem. (even tho now that I was really able to boot into 9.10, I now have a graphics issue)
 
After allot of checking how my system was set up. it seems for the most part, what fixed it was, going int o the "terminal text editor" and adding the 9.10, kernel 2.6.31 entry to the grub startup screen.
 
I would copy and paste what worked for me, but if someones wystem is set up differently than mine, it could cause more problems even greater.

---

### Post by coldsystem on 2009-11-05
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)
Try  this  link . you  will be  happy :)
i  had the  same issue . Now  the  sound  is  cool  :)

---

### Post by speculater on 2009-11-06
> **coldsystem said:**
> [http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)
Try  this  link . you  will be  happy :)
i  had the  same issue . Now  the  sound  is  cool  :)


This worked for me! Thanks.

---

### Post by Tholley on 2009-11-06
Hmmm... since I ended up doing a fresh install after all, and don't have sound again after fixing it before, this could be worth a try and could possibly save me from having to go thru everything (allot!) I did before.
 
I'll post back results later tonight or tomorrow.

---

### Post by abooks on 2009-11-07
I'm a guy from way back on page 2. I uninstalled Pulse and it seemed to help. Every time I close a program the speakers make a faint "thump" sound. I also uninstalled 2.6.29-15 and it didn't seem to make a difference. Amarok will play music (stuff that's in documents), and seems to detect CD drive, but says there are no tracks. Somewhere else I read Amarok doesn't do CDs (??), so what program does? What's the code for tecting the CD drive in terminal mode?

---

### Post by Gato303co on 2009-11-09
> **NCLI said:**
> Report bugs, please, all of you. Just go to System->Administration->System Testing, then make sure to submit a bug once you reach the part where it tests whether sound is working.

Reporting this means that it will probably be fixed quickly, since this is obviously a regression.

Report bugs? Sorry, but I reported a bug on 9.04 and got like 20 mails telling me "your post is duplicated" so my effort was futile, so I am not reporting  bugs anymore, it just doesnt work nor help

---

### Post by Gato303co on 2009-11-09
Anyone knows how to downgrade to Ubuntu 9.04? (if nobody helps I will have to go back to Windows XP)

---

### Post by mdrsc on 2009-11-14
Hi,
I have the same problem and I was reading this thread and in my case I did this and the information is after the quote:

> **the.drizzle said:**
> OK, there's your problem; you're not loading up the new 2.6.31 kernel, hence the alsa modules not loading either.

You need to edit your menu.lst file to load the correct kernel, and I have a hunch you've got the new (correct) file sitting somewhere where grub is not seeing it.

So that I can give you step-by-step instructions, I need to know a few things.

First, what is the output of
```

$ls /boot

```and also, it would be handy to know your partition table.  Please paste the output of

```

$sudo sfdisk -l /dev/sda

```(or whatever the label of your hard drive is, i.e., sda, sdb, etc...)  This will allow you to see where the actual boot device is; it's then your job to copy the 2.6.31 kernel onto that sector, as well as the new menu.lst file.

EDIT:

Actually, since it will speed this up, can you also post the output of
```

$cat /etc/fstab

```

```
mrayo@mrayo-laptop:~$ ls /boot
abi-2.6.24-24-generic             initrd.img-2.6.31-15-generic
abi-2.6.31-14-generic             memtest86+.bin
abi-2.6.31-15-generic             System.map-2.6.24-24-generic
config-2.6.24-24-generic          System.map-2.6.31-14-generic
config-2.6.31-14-generic          System.map-2.6.31-15-generic
config-2.6.31-15-generic          vmcoreinfo-2.6.31-14-generic
grub                              vmcoreinfo-2.6.31-15-generic
initrd.img-2.6.24-24-generic      vmlinuz-2.6.24-24-generic
initrd.img-2.6.24-24-generic.bak  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-14-generic      vmlinuz-2.6.31-15-generic
mrayo@mrayo-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=786ee51d-f067-4347-864b-0ac736483aa4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aa448c11-7e9d-4674-802a-ed1d6328db74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I would really aprecciate any help;)

---

### Post by WitchCraft on 2009-11-14
Ubuntu 9.10 comes with a new kernel.
What you are experiencing is typical for a kernel upgrade.
Since you UPGRADED from 9.04 to 9.10, you have a new kernel, but still the old ALSA drivers (whoever forgot to make them part of the upgrade)...

You need to recompile the ALSA drivers.
Or you can edit grub (the bootloader) to load the old kernel with the new OS.
 /boot/grub/menu.lst (grub1) OR /boot/grub/grub.cfg (grub2)

Needless to say you then will experience problems with the old kernel and the new drivers of the upgrade...

---

### Post by houdodu on 2009-12-09
had this problem. fixed it. no idea why this would work, but heres what i did:

sudo apt-get remove pulseaudio
sudo reboot

sudo apt-get install pulseaudio
sudo pulseaudio&

i also did
sudo apt-get install asoundconf-gtk && asoundconf-gtk
but i dont think it did anything

---

### Post by Ryantoss on 2009-12-12
> **fidelandche said:**
> This worked for me,

  # first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

Hello everybody 

I've also experienced this problem and this man helped me out.

However, this problem will comeback when i restart my computer thus i have to put these two commands again.

I fixed this problem by add it up in startup applications. 

Could anybody tell me why this problem has occurred. I want to know about this sound problem. Looking for your replies soon.

Sorry for bad language

Ryan Toss

---

### Post by FreyGrimrod on 2009-12-13
way to drop the ball.... I am not amused.... this problem has been common since August.... *goes about vehemently removing anything pulse audio related while debating about downgrading all I see are negatives in karmic thus far...*

And uh no this wasn't an upgrade this was a fresh install on virgin drives

---

### Post by nsleiman on 2009-12-13
it worked for me thank you :)

---

### Post by kirenpillay on 2009-12-14
I had the same problem after upgrading from 9.04 to 9.10. 

Today, I did a completely fresh install of 9.10, and everything works perfectly! :)

Pulseaudio works fine and another bug where the volume control buttons on my HP nx9420 laptop stopped working, where fixed!

I think the issue is with the update process reading old files?

---

### Post by rosswmcgee on 2009-12-16
OK did this:
sudo apt-get install asoundconf-gtk && asoundconf-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
asoundconf-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
You need at least one ALSA sound card for this to work!


So where do I get the Alsa Card?

---

### Post by Ryantoss on 2009-12-21
> **rosswmcgee said:**
> OK did this:
sudo apt-get install asoundconf-gtk && asoundconf-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
asoundconf-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
You need at least one ALSA sound card for this to work!


So where do I get the Alsa Card?

try these

> sudo apt-get remove pulse
sudo apt-get install pulse
sudo reboot


after reboot

> sudo apt-get remove alsa
sudo apt-get install alsa

it should help.

---

### Post by juanvi on 2010-01-07
> **alonc said:**
> I also have no sound after upgrade.
No sound card at the “Sound Preferences” Hardware tab
I fixed it by editing the default.pa file:
```
sudo gedit /etc/pulse/default.pa
```
and uncomment lines 45 and 46
```

load-module module-alsa-sink
load-module module-alsa-source device=hw:0,1

```
saved it and reboot.

Now sound is working but still no sound card at the Hardware list.
[LEFT] 
[FONT=Times New Roman, serif] [/FONT][/LEFT]

Thanks a lot. That worked for me!

---

### Post by azog_on_linux on 2010-01-10
Cheers the.drizzle.. forcing the boot on 2.6.31-14 sorted the issue for me. Im not so sure why the image is "installed" during the upgrade but not configured in grub. *shrug*

---

### Post by zhenbanjiezhuan on 2010-03-08
i have the same problem!! sound works fine in XP[dual boot]..i have an HDMI device and an Intel sound....the Intel device will really make sound [for my laptop].the Intel is shown in terminal when i check it, but if i go to sound preference --> output, my Intel is not showing up..only the HDMI device...

---

