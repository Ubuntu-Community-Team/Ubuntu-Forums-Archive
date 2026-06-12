---
title: "Removed gui file, got black screen now."
date: 2009-08-31
forum: New to Ubuntu
---

### Post by John Teisberg on 2009-08-31
I thought I could get my sound to work by uninstalling and reinstalling all the ALSA files using Synaptic. Bad idea. One of those files must have been for my gui. I can log in but only get a black screen with a live mouse arrow. 
I do not want to reinstall since I have my Wacom tablet working now and that took forever to get going. I'm afraid I'll loose those settings.
Thanks in advance for any help.
Ubuntu 9.04, dual boot to XP Pro.

---

### Post by NoaHall on 2009-08-31
Can you boot into recovery mode or get into a terminal by doing "ctrl + alt + 1" ?

---

### Post by John Teisberg on 2009-08-31
Good Evening NoaHall,

Thanks for your quick reply.

cntrl + alt + 1

did not do anything.

---

### Post by John Teisberg on 2009-08-31
I also tried all the recovery permutations of trying to get going again, but no luck yet. Nuts.

---

### Post by NoaHall on 2009-08-31
Have you tried choosing booting into recovery mode at grub yet?

---

### Post by John Teisberg on 2009-08-31
Yup. No luck. The white arrow is still under the control of the Wacom tablet. At least that's fun to watch move around. Kind of like a broken etch-a-sketch.

---

### Post by NoaHall on 2009-08-31
Try disconnecting the tablet and booting again. See if anything has changed.

---

### Post by John Teisberg on 2009-08-31
Hmm, that didn't work either. I was hoping I could get to a command line somehow and be able to get that gui kick started somehow. Wish I knew more about Linux. I guess this is my learning path.

---

### Post by NoaHall on 2009-08-31
Yeah, you really need to get to the prompt. 

Try disconnecting everything but the keyboard, and see what happens.

What graphics card do you have? Do you have a spare(or on-board one)?

---

### Post by John Teisberg on 2009-08-31
I'll unhook everything except the keyboard.

Meanwhile, I've got an onboard graphics card
Intel G33/G31 Express Chipset Family

It's working great in Windows and, until I killed Ubuntu, great in Linux.

Here are some other details:

OS Name    Microsoft Windows XP Professional
Version    5.1.2600 Service Pack 3 Build 2600
OS Manufacturer    Microsoft Corporation
System Manufacturer    INTEL_
System Model    DG33TL__
System Type    X86-based PC
Processor    x86 Family 6 Model 15 Stepping 11 GenuineIntel ~2666 Mhz
BIOS Version/Date    Intel Corp. DPP3510J.86A.0293.2007.1002.1519, 10/2/2007
SMBIOS Version    2.4
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "5.1.2600.5512 (xpsp.080413-2111)"
Time Zone    Central Daylight Time
Total Physical Memory    2,048.00 MB
Available Physical Memory    1.27 GB
Total Virtual Memory    2.00 GB
Available Virtual Memory    1.96 GB
Page File Space    3.82 GB

---

### Post by John Teisberg on 2009-08-31
No change after pulling all the wires except the keyboard. Windows got excited when it found some new toys when it got fired up again. Windows seems to take forever to get started after messing around with linux.

---

### Post by nothingspecial on 2009-09-01
Can you remember _exactly_ what packages you removed?

---

### Post by John Teisberg on 2009-09-01
When in Synaptic I did a search for ALSA. All of the files that came up are the ones I deleted. I foolishly assumed that they were all for sound.
So, I don't remember the names of all the files, but that's how I chose them.

---

### Post by nothingspecial on 2009-09-01
I don`t tend to use synaptic so I`m not sure how the search function works.

If you use apt-cache to search it will give any package that alsa is mentioned in, even the description. If that`s the case, and you deleted everything you may have major problems.

I`ll have to check when I get home in an hour or so.

---

### Post by John Teisberg on 2009-09-01
Thanks so much. I've got to head out for work in a few minutes. 
I'm looking forward to seeing what you have to say when I get back.
Have a fine day.

---

### Post by NoaHall on 2009-09-01
I'm afraid your best bet is probably reinstalling, as you can't access a terminal. You can use the live disk to copy files so you don't lose them. (sudo nautilus or sudo cp /media/disk/home /media/disk-1)

---

### Post by nothingspecial on 2009-09-01
Unfortunately removing alsa-utils also removes ubuntu-desktop. This in itself is not unfixable.

Unfortunately you seem to have your tablet set up to control your pc. I know nothing of these things.

The first thing I would try is to log in to your computer remotely using ssh if it is installed on your borked one. If you need help doing that, post back, although it sounds like we`re on different work/sleep pattern`s here. There`s plenty of online docs though.

From there you can install ubuntu-desktop and hope that fixes it.

There are 2 other options - 
 Create a seperate home partition and reinstall, that way you keep all your settings, not sure about the tablet ones though, I`m talking about your personal settings. It seems, from your problem, that this tablet is configured system wide. Here`s how to do that - 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)



Or chroot from a live cd and install ubuntu-desktop that way. I`ve never tried this so only do this as a last resort -  it might work, no garuntees.

Boot a live cd.

```
sudo fdisk -l
```

This will determine which partition your ubuntu install is listed as.

```
sudo mkdir /media/ubuntu
```
```
sudo mount -t ext3 /dev/[COLOR="Red"]sda1[/COLOR]/ /media/ubuntu
```

Substitute /dev/sda1 for your ubuntu partition.

```
sudo chroot /media/ubuntu/
```

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

See if that fixes it.

---

### Post by John Teisberg on 2009-09-01
Thanks for the ideas and link.

It is tantalizing to launch Ubuntu with the CD and see all my linux directories and files.
Everything is there, but I don't know what to do.
I can see but I cannot touch.
I tried the code you supplied in the terminal but it does not do anything.
Using the terminal I tried to log in using my password etc, but no luck.
I was hoping that I could reinstall the alsa stuff I ripped out using the temporary session.

I went to the site you recommended and read that I can install a new Home folder, but I already have one.
I also read about installing Ubuntu in Windows using Virtualbox.
I expect I'll get the same results as running off the CD.

I'm about ready to reinstall Ubuntu off the CD.
It looks like there is a way I can do that without reformatting that part of my drive.
I get right to the edge but stop just before pushing the button.

When I reinstall will my existing Home directory get overwritten?
Will I loose my emails?
I expect I'll loose my precious Wacom settings when I do this.

Thanks again for your help.

PS. I tried to copy the etc. file using Natulis but it would not let me.
I did not try the Home file.
I'll reboot and try that now.

---

### Post by NoaHall on 2009-09-01
Yes, you'll lose anything not backed up, unless you do a side by side install, then you'll lose nothing(unless interrupted), but then you'll have two partitions half the size.

---

### Post by John Teisberg on 2009-09-01
Good evening.
I just tried to copy then make an archive of my Home folder, no permission to do those things.

To do a side by side install, can I eat up half of my linux partition?
I don't have a lot of unused space on there.
I expect to do that using the 'manual' part of the installation.

I can see the linux partition /dev/sda5, it says it has 20% of my hard drive.
The other partition is /dev/sda1, I believe that is all the Windows stuff.

Hmm, if I do a side by side install I assume I can visit my old folders and get everything out of them.
Is that true?

Also, would I be able to claim that old part of the partition for the new install of Ubuntu?

Thanks.

---

### Post by NoaHall on 2009-09-01
Yes, you can visit them and get everything out of them.
You would be able to claim it as part of the media, but not use it as /home/

---

### Post by John Teisberg on 2009-09-01
Excellent,
This sounds good.

My son's teacher just showed up for our parent teacher conference.
I'd better tend to that for now.

I'll get back on this later this evening.

Thanks.

---

### Post by NoaHall on 2009-09-01
Great, let us know how you get on.
Note - if there is a unexpected shutdown/loss of power, then your files will most likely be completely corrupt, and you won't be able to access anything on it. So, be careful while doing it!

---

### Post by nothingspecial on 2009-09-02
The link is not asking you to create a new home directory, rather place it on a different partition. I have all my systems set up this way. It means ,when you reinstall, as I like to do every 6 months, instead of updating, everything is set up the way it was. Also if you dual boot 2 different linux distros you can use the same home.

The link explains how to shrink your existing ubuntu partition. I use about 8 gigs to be on the safe side.

Then create a new partition and copy your home directory on to it.

You can then reinstall setting this new partition as home. Everything will bve the same. Your wallpaper, your theme, your firefox settings, your music library etc etc etc

First I would back everything up to some removable media though. I really would try this first rather than just nuking what you have. The way it stands you have nothing to loose.

---

