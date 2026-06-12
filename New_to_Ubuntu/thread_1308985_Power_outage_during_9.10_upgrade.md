---
title: "Power outage during 9.10 upgrade"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by russcb on 2009-11-01
Help!! I had a power outage during the 9.10 upgrade and when the computer starts up it wont go past;
"One or more of the mounts listed in /etc/fstab cannot yet be mounted
(ESC for recovery shellc1a2c9b258cc9)
/: waiting for /dev/disk/by-uuid/f55ac981-0bb4-4756-9927-3c1a2c9b258c
/tmp: waiting for (null)
swap: waiting for UUID=317982b7-25a4-4269-acb7-591682d485f4. 
Absolute novice!! What can I do to get it going?????":(

---

### Post by lavinog on 2009-11-01
Do you have access to a live cd?

I think your only option is to reinstall.
Use a live cd to backup your files, and reinstall.

---

### Post by kansasnoob on 2009-11-01
Are you posting using the Live CD right now?

---

### Post by synicalx on 2009-11-01
I know the feeling :(

Like others have said, pop in the Live CD, find your drivers/files and put them onto some sort of backup media (Blank DVD's, an external hard drive, USB stick etc) and do a fresh install.

It sounds as if some of the files needed to run the OS from your current hard drive have been corrupted or damaged, but it's unlikely any of your personal files (photos etc) have been touched ;)

---

### Post by russcb on 2009-11-01
Thanks for your prompt replies!
OK! I now have booted up on a live CD ready to copy my files to a flask disk, I have located my files, but how to I get permission to do so!!

---

### Post by russcb on 2009-11-01
> **lavinog said:**
> Do you have access to a live cd?

I think your only option is to reinstall.
Use a live cd to backup your files, and reinstall.

Hi lavinog! Using LiveCD. How do I backup to a Flash drive? It tells me I do not have permission.:confused:
Thanks

---

### Post by ikt on 2009-11-01
> **russcb said:**
> Help!! I had a power outage during the 9.10 upgrade and when the computer starts up it wont go past;
"One or more of the mounts listed in /etc/fstab cannot yet be mounted
(ESC for recovery shellc1a2c9b258cc9)
/: waiting for /dev/disk/by-uuid/f55ac981-0bb4-4756-9927-3c1a2c9b258c
/tmp: waiting for (null)
swap: waiting for UUID=317982b7-25a4-4269-acb7-591682d485f4. 
Absolute novice!! What can I do to get it going?????":(

Does GRUB load up at all?

---

### Post by ZankerH on 2009-11-01
> **russcb said:**
> Thanks for your prompt replies!
OK! I now have booted up on a live CD ready to copy my files to a flask disk, I have located my files, but how to I get permission to do so!!

You need to open nautilus (the file manager) as superuser: Open the terminal (under Applications->Accessories) and type in "gksu nautilus".

---

### Post by russcb on 2009-11-01
> **ikt said:**
> Does GRUB load up at all?
Yes! and Ubuntu loading process appears followed by the message.

---

### Post by ikt on 2009-11-01
> **russcb said:**
> Yes! and Ubuntu loading process appears followed by the message.

Is there a 'recovery' option in the grub menu? Although thinking about it now if there was and you were able to go in, drop to root, run apt-get upgrade and finish off the upgrade I think would be a little to easy :(

---

### Post by lavinog on 2009-11-01
> **russcb said:**
> Hi lavinog! Using LiveCD. How do I backup to a Flash drive? It tells me I do not have permission.:confused:
Thanks

What is causing the permission problem?  Can you copy anything, or create a blank file onto the flash drive?
If not, check the flash drive for a write protect switch, or run a disk check on it in windows.  Make sure you always unmount the drive when using windows.

---

### Post by jamespi on 2009-11-02
i had the same problem - i fixed it like this:

[LIST=1]
[*]check / fix filesystem on your root partition
[*]boot from your harddisc but chose "recovery mode"
[*]when it gets to the error message again, press ESC to get a prompt up
[*]remount your root partition as read/write
[*]check your networking
[*]reinitiate the upgrade procedure
[/LIST]

Step 1 - fix filesystem

Boot ubuntu or anything with GParted from a liveCD or liveUSB stick
Run System->Administration->Gparted or System->Adminstration->Partition Editor depending on what it's called.
Figure out which partition is your root partition - (hint it'll be in ext3 or ext4 format)
Make a note of what label it's given by linux Probably sda1 or sda2 or something - you'll need this in step 4.
Right click it and chose "check"
Let it finish - hopefully nothing will be wrong or it will fix what is wrong. (if it's worse that that you'll have to google a solution for fixing it)

Step 2 - Reboot, choose the 2nd option down the list when grub appears this should be the newest kernel, but in "recovery mode"

Step 3 - When you get to the annoying error about waiting for drives to mount, it should say "press ESC for prompt" or something like that, press it. If it doesn't give you a prompt then i don't know what to do so you'll have to keep looking for solutions.

Step 4 - Remount your root partition as read/write
For some reason when the upgrade procedure gets broken half way through GRUB is left in a state where it is instructed to mount all drives as read only.
You need to remount your root partition as read/write so that you can resurrect the upgrade process
remember the label for your partition that you noted down in step 2? It goes here:

```
mount /dev/sda1 -o rw,remount
```

just replace sda1 with whatever your root partition is called.

Step 5 - check your networking

type 
```
ping www.google.com
```
if it gets a reply rather than just timing out you have an internet connection!
At this point my networking wasn't working - i had an ethernet cable connecting the pc to my router so i knew i had a link. Getting wifi up manually is outside of my scope im afraid, but to get wired networking up i scoured the forums and came up with this:
type:
```
mkdir /var/run/network
```
don't ask me why..
and then get a text editor up:
```
nano /etc/network/interfaces
```
then add the lines: 
```
iface eth0 inet dhcp
auto eth0
```
press ctrl-O to save then ctrl-X to exit
then at the prompt type:
```
ifup eth0
```
it should churn out some ip addresses and something about DHCPDISCOVER then NTP then it'll hang - press ctrl-C to get a prompt back
then type 
```
ping www.google.com
```
if it gets a reply rather than just timing out you have an internet connection!
if you don't have a internet connection then you'll have to get googling as it's outside my scope

Step 6 - resume the upgrade
type
```
dpkg --configure -a
```
you might have to answer some question when prompted. I generally just agree with what it suggests.
then type 
```
apt-get update
```
then type
```
apt-get upgrade
```
again there will be questions to answer, as what is happening in front of your very eyes is the upgrade procedure finishing what it started.
once this finishes type
```
apt-get update
```
then type
```
apt-get upgrade
```
just to make sure no stragglers are left - keep repeating these two commands until nothing new happens. 

then type
shutdown now -h
your computer will switch off. Turn it on. Mine booted perfectly into Karmic. Hooray!

---

