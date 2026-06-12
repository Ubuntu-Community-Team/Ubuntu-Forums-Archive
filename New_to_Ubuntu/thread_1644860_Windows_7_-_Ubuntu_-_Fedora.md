---
title: "Windows 7 - Ubuntu - Fedora"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by hmsiegel on 2010-12-13
I am brand new to Linux in general and Ubuntu in particular.  I installed 10.10 on Friday using Wubi and spent most of yesterday learning.  A friend of mine suggested that I use Fedora instead of Ubuntu.  I wouldn't mind trying it.  Is there a way to have all three loaded on my system.  I'm not going to give up my Windows just yet (though I may at some point in time), but I would like to be able to try both Distros.  Any help is appreciated.

Thanks

Harlan

---

### Post by Hippytaff on 2010-12-13
The ubuntu install (with Wubi) is inside windows, so it's not an actual partition. You could install Fedora as a dual boot with windows and have all three that way, but the only limit to the amount of distros you have on a pc is space.

---

### Post by snowpine on 2010-12-13
You can burn a Fedora Live CD and try it with no change to your computer.

Fedora and Ubuntu are very similar, so I don't see much advantage to installing them both.

---

### Post by hmsiegel on 2010-12-13
Say I wanted to stay with Ubuntu.  I would then uninstall the wubi, download and install Ubuntu (which would then have it's own partition) and then download and install Fedora (which would also have it's own partition).  Or I could keep Ubuntu as it is (installed inside Windows) and then install Fedora.  Does this seem about right.  If I were to uninstall the Wubi, what is the best order to install the distros?

Harlan

---

### Post by Hippytaff on 2010-12-13
I think you might be better of taking Snowpine's suggestion of trying the liveCD's of a number of distros and checking them out that way. Though maybe LiveUSB would be better, just because its faster than a liveCD, rather than installing and messing around with partitions, grub2, mbr's, seperate /home partitions etc etc

Get a feel for the distros without the messing around until you decide what you want.

---

### Post by theozzlives on 2010-12-13
You can make a live Fedora USB with persistence, then whatever you do will be saved. You already have WUBI so you don't have to worry about that. Welcome to Linux and open source no matter what you choose.

---

### Post by mark2741 on 2010-12-13
I agree in that using a Live CD of the various distributions is the best way to go.

Once a year or so I download and burn a live cd for each of Fedora, SuSe, Mint, Ubuntu, etc. to see what's changed in them.

After a few years of not being able to run Ubuntu (my hardware was no supported), last week I tried Fedora, Mint, etc. They all worked fine but I was thrilled to see Ubuntu 10.10 was working on my system without issue! Happy to be back on Ubuntu!

I don't know if it's changed much (I can't imagine it has), but I always thought Wubi was a dumb idea. I don't see what the point of it is really. For trying out Ubuntu, the live cd is better. And if you need an install of Ubuntu then dual-booting is better. I just don't see the point of Wubi.

---

### Post by Hippytaff on 2010-12-13
> 
 I just don't see the point of Wubi.
I was brought into the world of Linux by Wubi, after about a month, I did a 'real' partition. It is good as a way of introduction to the open source world, but I agree, it can be more trouble than it is worth in the long run, and it is intended to be a short term thing. Now I'm starting to get familiar with the workings of linux I'm dual booting ubuntu (my reliable distro) with all sorts of linux variants.

So hemsigel, I second ozzlives welome! enjoy the linux freedom :-D

---

### Post by matt_symes on 2010-12-13
Hi 

A liveCD/USB is the best way to go to play with the distros. Installations on pen drives are also an excellent choice if your BIOS is set up correctly and don't want to mess with your hard drive.

If you want to use partitions though, this is what i would do.

-1. Check there are no problems by using a live CD/USB. It's not foolproof, but it can highlight hardware and other potential issues.

0. _Backup_ your existing drive. Use Clonezilla, Remastersys or some such.

1. Uninstall Wubi and remove all references to it. Search on the forums  for this. Make sure there are no references in boot.ini or anywhere  else. This will save you pain later. Trust me.

2. Disk cleanup, on the windows partition. defragment the windows partition and use the windows tools to shrink the windows partition to the desired size.

3. Create at least three new partitions using gparted. 1. for Fedora, 1 for Ubuntu and 1 for swap. If you want to hibernate make sure the Swap partition is at least as large as your memory and add a bit extra. (You might want to create others for home partitions or NTFS partitions to share files with windows)

4. I would install fedora first, as it uses Grub.

5. Then install Ubuntu as it uses Grub2.

6. Make both installations use the same swap partition.

Kind regards

---

### Post by ilovelinux33467 on 2010-12-13
If your PC is fast enough you could run Fedora under a Virtual Machine under Windows 7 or Ubuntu

---

### Post by hmsiegel on 2010-12-13
Thanks for all the great replies.  I think for now I am going to stick with the Wubi and try Fedora off of a Live USB.  As I get more comfortable with Linux, I will probably pick one or the other and do a full install with the dual boot.  
I can't get rid of Windows just yet, I use too many Microsoft products for work (Excel, Word, Outlook, Exchange).  I know that the OpenOffice suite does most of the same stuff, but I have to get used to using it.  Also, I've created some Excel programs with VBA, which I'm pretty sure won't run in OpenOffice (though I haven't looked into that yet).  Finally, I can't access my Exchange account through Evolution.  
Anyway, that was a tangent.  I do have another question:  What are some of the differences between Ubuntu and Fedora?
Thanks

Harlan

---

### Post by snowpine on 2010-12-13
> **hmsiegel said:**
> I do have another question:  What are some of the differences between Ubuntu and Fedora?

Ubuntu and Fedora are more alike than different. They are both excellent, cutting-edge distros with releases every 6 months. The biggest difference is that Ubuntu uses .deb packages and the APT package manager, while Fedora uses .rpm packages and the YUM package manager.

---

### Post by matt_symes on 2010-12-13
Hi

They both use gnome so they look similar. Fodora uses an older boot loader.

If you do most things through the GUI (graphical user interface) then the differences are small.

It's only if you look under the bonnet (CLI) you will notice them.

If you want to see differences then install Ubuntu and Kubuntu (Gnome and KDE).

I suspect your friend is an old red hat hand :)

Kind regards

---

### Post by amjjawad on 2010-12-14
> **matt_symes said:**
> Hi 

A liveCD/USB is the best way to go to play with the distros. Installations on pen drives are also an excellent choice if your BIOS is set up correctly and don't want to mess with your hard drive.

If you want to use partitions though, this is what i would do.

-1. Check there are no problems by using a live CD/USB. It's not foolproof, but it can highlight hardware and other potential issues.

0. _Backup_ your existing drive. Use Clonezilla, Remastersys or some such.

1. Uninstall Wubi and remove all references to it. Search on the forums  for this. Make sure there are no references in boot.ini or anywhere  else. This will save you pain later. Trust me.

2. Disk cleanup, on the windows partition. defragment the windows partition and use the windows tools to shrink the windows partition to the desired size.

3. Create at least three new partitions using gparted. 1. for Fedora, 1 for Ubuntu and 1 for swap. If you want to hibernate make sure the Swap partition is at least as large as your memory and add a bit extra. (You might want to create others for home partitions or NTFS partitions to share files with windows)

4. I would install fedora first, as it uses Grub.

5. Then install Ubuntu as it uses Grub2.

6. Make both installations use the same swap partition.

Kind regards

+1

I have 9 OS's installed, Fedora is one of them. I have it on my both PCs along with Windows XP and Ubuntu.

---

