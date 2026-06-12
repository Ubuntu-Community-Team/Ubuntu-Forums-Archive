---
title: "Difference between Eject, Unmount &amp; Safely Remove?"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by ashwinhgtx on 2009-10-26
When I right click on a mounted drive in the desktop I get the option to Unmount, Safely Remove and Eject. Could anyone explain the difference between these three options?
I'm on Karmic RC btw, it rocks.
Thanks in advance.

---

### Post by jacksaff on 2009-10-26
Unmount removes the disk from the file system. It makes sure any information waiting to be written to the disk gets written.
Safely remove is just a non-techy way of saying unmount.
Eject unmounts and then ejects the media.

---

### Post by ashwinhgtx on 2009-10-26
> **jacksaff said:**
> Unmount removes the disk from the file system. It makes sure any information waiting to be written to the disk gets written.
Safely remove is just a non-techy way of saying unmount.
Eject unmounts and then ejects the media.

Thanks for the prompt answers. But may I know why all three are being displayed for an external hard drive? Can't it be context sensitive and display Eject only for a CD drive and Safely Remove for everything else?

Isn't it a more user friendly way of doing things? It would also reduce the clutter.
Anyone else have any similar thoughts? Please correct me if I'm wrong about these options.

---

### Post by philinux on 2009-10-26
On a mounted internal drive I'm only offered unmount, maybe its a to do with external drives like usb sticks/drives and so forth.

---

### Post by ashwinhgtx on 2009-10-26
> **philinux said:**
> On a mounted internal drive I'm only offered unmount, maybe its a to do with external drives like usb sticks/drives and so forth.

But why have all three options for an external hard drive or a USB pen drive? Wouldn't that confuse new users?

---

### Post by alphaniner on 2009-10-26
Having the option to Unmount or Eject is intended for CDs & DVDs.  Safely Remove may be something new to Karmic, I've never seen it.  It's probably a bug that you're seeing all the options.

---

### Post by mcduck on 2009-10-26
"Unmount" unmounts a single partition, "Safely Remove Drive" unmounts all partitions of that device.

For example if you have a removable hard drive with 2 partitions selecting "Safely Remove Drive" for one of them would unmount both partitions, so that the device can be safely unplugged from your computer.

"Eject" is for media that can actually be ejected, like CD/DVD drive. So it unmounts the media and then ejects it (quite important if you happen to have a slot drive without a physical eject button).

Which ones appear in the right-click menu depends on what type of device/media it is. For some devices even having all three options would make perfect sense.

---

### Post by ashwinhgtx on 2009-10-26
> **mcduck said:**
> "Unmount" unmounts a single partition, "Safely Remove Drive" unmounts all partitions of that device.

For example if you have a removable hard drive with 2 partitions selecting "Safely Remove Drive" for one of them would unmount both partitions, so that the device can be safely unplugged from your computer.

"Eject" is for media that can actually be ejected, like CD/DVD drive. So it unmounts the media and then ejects it (quite important if you happen to have a slot drive without a physical eject button).

Which ones appear in the right-click menu depends on what type of device/media it is. For some devices even having all three options would make perfect sense.

How does having all three for a USB flash drive make sense? I'm just curious as I'm don't know much on how *nix handles partitions.

---

### Post by Primefalcon on 2009-10-26
> **alphaniner said:**
> Having the option to Unmount or Eject is intended for CDs & DVDs.  Safely Remove may be something new to Karmic, I've never seen it.  It's probably a bug that you're seeing all the options.
It is new to karmic, I think its just for familiarity with windows users, I could be wrong though

---

### Post by mcduck on 2009-10-27
> **ashwinhgtx said:**
> How does having all three for a USB flash drive make sense? I'm just curious as I'm don't know much on how *nix handles partitions.

Perhaps "Eject" will spit out the flash drive automatically? :D

No, I agree that having the "Eject" option for a USB flash drive doesn't make much sense..

---

### Post by Aearenda on 2009-10-27
It's [bugged in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/453072"), and [upstream]("https://bugzilla.gnome.org/show_bug.cgi?id=598690").

---

### Post by ashwinhgtx on 2009-10-27
> **Aearenda said:**
> It's [bugged in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/453072"), and [upstream]("https://bugzilla.gnome.org/show_bug.cgi?id=598690").

Thanks for pointing it out. I hope they resolve the issue soon. 

But these reports seem to be for the U3 flash drives. The three options appear for almost any pen drive not just the U3 ones. This has been pointed out in some of the comments.

The GNOME bugzilla guys seem to be disagreeing with themselves. Can this be fixed just for Ubuntu? I don't know much about the development behind the pretty and usable desktop I see, I'm just curious.  ;)

BTW, is it time to mark this thread as solved even though it's not? :)

---

### Post by Penguin Guy on 2009-11-02
> **mcduck said:**
> Perhaps "Eject" will spit out the flash drive automatically? :D

No, I agree that having the "Eject" option for a USB flash drive doesn't make much sense..
Personally I think it sounds a lot better than 'Safely Remove Drive', even if it is technically incorrect.

---

### Post by artheon on 2009-11-03
For that matter, 'Safely Remove Drive' isn't correct either. This command does not remove the "drive" at all, safely or otherwise. It may make that possible, but the same goes for 'eject'. The qualifier 'safely' is superfluous. Who would want to remove their drive in a dangerous manner? We can safely (pun not intended) assume that a user would want to remove it without damage to their equipment. As far as I can see, windows terminology compatibility is the only thing in favor of 'Safely Remove Drive'. That's substantial, though not necessarily sufficiently so.

---

### Post by nata.loko on 2009-11-03
I have an external hard drive and when I click "Safely Remove Drive", it spins down and I can detach it without hear a worrying noise. This didn't happened in previous versions.
I'm very happy with this new option.

---

### Post by 3rdalbum on 2009-11-03
I agree, it's a bit daft to have all three options for hot-plugged storage. There should be one: Eject.

Unmount is the correct language (but surprisingly a lot of Windows users don't know this word). Safely Remove is too Windows-y for me. Eject is a newbie-friendly word because everyone is familiar with the concept from tape recorders.

---

### Post by praveesh on 2009-11-03
> **ashwinhgtx said:**
> But why have all three options for an external hard drive or a USB pen drive? Wouldn't that confuse new users?

The people coming from windows will automatically click on safely remove . People familiar with linux will click on unmount . No offence .

---

### Post by 3rdalbum on 2009-11-03
> **praveesh said:**
> The people coming from windows will automatically click on safely remove . People familiar with linux will click on unmount . No offence .

The people familiar with Linux will look at the three options in confusion and wonder what the difference is. At least, I did.

---

### Post by Arup on 2009-11-04
The word safely should be safe enough for most. :)

---

### Post by sambita on 2009-11-04
> **nata.loko said:**
> i have an external hard drive and when i click "safely remove drive", it spins down and i can detach it without hear a worrying noise. This didn't happened in previous versions.
I'm very happy with this new option.

+1

---

### Post by ashwinhgtx on 2009-11-06
The 'Eject' option should appear only for CD/DVD drives.

The 'Safely Remove Drive' option for external hard drives and pen drives.

The 'Unmount' option only for individual partitions in a hard drive. It could be changed to 'Unmount Partition'.

Plus a tool tip describing what the option does could appear when you hover over the option with your cursor.

Will this work?

---

### Post by bennachie on 2009-11-06
I can think of at least one one situation when "eject" makes perfect sense with a USB drive. That is when you are dealing with one of that group of 3G wireless broadband modems which want to self-install software on Windows or Macintosh systems. 

The "drive" containing the software appears on Ubuntu (or other recent Linux distros, such as Fedora), and blocks recognition by  Network Manager of the actual modem. Ejecting the mounted drive (and sometimes using "edit connections" to encourage Network Manager to find and identify the modem) allows you to use the device normally and connect to the Internet.

---

### Post by ashwinhgtx on 2009-11-06
> **bennachie said:**
> I can think of at least one one situation when "eject" makes perfect sense with a USB drive. That is when you are dealing with one of that group of 3G wireless broadband modems which want to self-install software on Windows or Macintosh systems. 

The "drive" containing the software appears on Ubuntu (or other recent Linux distros, such as Fedora), and blocks recognition by  Network Manager of the actual modem. Ejecting the mounted drive (and sometimes using "edit connections" to encourage Network Manager to find and identify the modem) allows you to use the device normally and connect to the Internet.

Isn't that a problem with Network Manager? Shouldn't it be able to recognise the modem when plugged in?

---

### Post by BigBananaMan on 2009-11-17
I typically use Unmount on flash drives and Eject on optical disks because that's what I want to do.  I want the flash drive unmounted from the filesystem and the disk unmounted and ejected from the drive so I can put it back in it's case.  Personally I would prefer that they just have Unmount for drives and Eject for disks.  There is no instance I can think of where I want a disk to be unmounted but still stuck in the drive and I could just use umount /media/cdrom0 if that's what I wanted.  Safely Remove Drive seems to do nothing more than Unmount.

Now for a little fun I tried to set up another useless "Dangerously Remove Drive" option in Nautilus Actions Configuration that will make an annoying system beep to startle and prompt the user to yank the device out without unmounting it (I know I know, but somehow it makes sense to me).  Unfortunately, Beep, Echo, and even the mighty Python have failed to invoke a system beep :confused:

---

### Post by RJ12 on 2009-11-17
> **BigBananaMan said:**
> I typically use Unmount on flash drives and Eject on optical disks because that's what I want to do.  I want the flash drive unmounted from the filesystem and the disk unmounted and ejected from the drive so I can put it back in it's case.  Personally I would prefer that they just have Unmount for drives and Eject for disks.  There is no instance I can think of where I want a disk to be unmounted but still stuck in the drive and I could just use umount /media/cdrom0 if that's what I wanted.  Safely Remove Drive seems to do nothing more than Unmount.

Now for a little fun I tried to set up another useless "Dangerously Remove Drive" option in Nautilus Actions Configuration that will make an annoying system beep to startle and prompt the user to yank the device out without unmounting it (I know I know, but somehow it makes sense to me).  Unfortunately, Beep, Echo, and even the mighty Python have failed to invoke a system beep :confused:

Lol!!

---

### Post by 3rdalbum on 2009-11-17
> **bennachie said:**
> I can think of at least one one situation when "eject" makes perfect sense with a USB drive. That is when you are dealing with one of that group of 3G wireless broadband modems which want to self-install software on Windows or Macintosh systems. 

The "drive" containing the software appears on Ubuntu (or other recent Linux distros, such as Fedora), and blocks recognition by  Network Manager of the actual modem. Ejecting the mounted drive (and sometimes using "edit connections" to encourage Network Manager to find and identify the modem) allows you to use the device normally and connect to the Internet.

Usbmodeswitch should just do it's job regardless, I think. I can get an HSDPA connection without unmounting the fake flash drive.

---

### Post by wilee-nilee on 2009-11-17
Safely remove turns off the power to the USB device, not necessarily needed But that is my choice with a ext HD.

---

### Post by TokyoYank on 2009-12-09
> **wilee-nilee said:**
> Safely remove turns off the power to the USB device, not necessarily needed But that is my choice with a ext HD.
me too, I like to see the LED turn off.  Also it seems required for rockbox ipods & cameras & camcorders..

OP Hope this post gets updated when there's a fix for 9.04 users  (no, I'm too lazy to go 9.10)

---

### Post by apalacheno on 2009-12-19
Does any of you know what command is actually triggered by the "Safely Remove Drive" option?

Cheers,
Robert

---

### Post by Hagen99 on 2009-12-25
> **apalacheno said:**
> Does any of you know what command is actually triggered by the "Safely Remove Drive" option?

Cheers,
Robert

Yes I am interest knowing which command do that I while researching a little about this topic and I am not able to find the proper command.


Thanks

---

### Post by littlepeon on 2010-01-01
part of the same thread...have installed palimpsest disk utility in jaunty
palimpsest gives you three options for usb disks... unmount, eject and detach
unmount and eject are basically the same.... except if you do not remove your drive, you can use eject -t  and it will now think that u re-plugged it in.....
detach not only unmounts the drive but it powers it down...
this is preferable to me as i feel that unplugging even a spinning unmounted drive (usb hard drive) cant be a good thing
now my question to the group is what command does palimpsest use to detach a drive?

any responses are welcome

-Peon

---

### Post by Iyunkateus on 2010-01-01
Looked at this thread, and I'd like to share something interesting: When my Amazon Kindle 2 is plugged into my computer via USB, it says "If you want to use your Kindle and continue charging, please eject your Kindle from your computer." Additionally, an iPod nano says "Connected - Eject before disconnecting." It's unlikely that the Kindle could continue charging if it was disconnected, and the iPod makes a distinction between ejecting and disconnecting, so wouldn't "eject" need to be a valid option, at least in these cases?

---

### Post by ashwinhgtx on 2010-01-05
Well, can anyone here sort this out? Is there a better and simpler way of doing these functions? We should have something more intuitive by Lucid at least. Am i not right?

I haven't tried out the alphas yet. Has it been changed or improved over there?

---

### Post by mvalviar on 2010-01-05
Fascinating. I wanted to ask the same question myself.

---

### Post by joshzam on 2010-01-12
It took me a very long time to learn the difference between these and I suffered for a long time. I have an internal multi-card reader with a built-in USB port. After I was finished with either a media card or a USB device, I would choose "Safely remove drive". WRONG! It took me weeks to realize that this was actually turning off the power to the entire card reader and I was unable to subsequently mount any other cards or USB devices until I did a reboot! I acknowledge that this action is sometimes desired, but this was not what I was expecting given the "friendly" description. Let's hope they see the error of their ways and come up with a more intuitive way of performing these actions.

---

### Post by Marisa H on 2010-01-12
> **joshzam said:**
> It took me a very long time to learn the difference between these and I suffered for a long time. I have an internal multi-card reader with a built-in USB port. After I was finished with either a media card or a USB device, I would choose "Safely remove drive". WRONG! It took me weeks to realize that this was actually turning off the power to the entire card reader and I was unable to subsequently mount any other cards or USB devices until I did a reboot! I acknowledge that this action is sometimes desired, but this was not what I was expecting given the "friendly" description. Let's hope they see the error of their ways and come up with a more intuitive way of performing these actions.

so it should be eject, right?

---

### Post by warfacegod on 2010-01-12
>  Originally Posted by bennachie  View Post
I can think of at least one one situation when "eject" makes perfect sense with a USB drive. That is when you are dealing with one of that group of 3G wireless broadband modems which want to self-install software on Windows or Macintosh systems.


When you use the usb disc creator the usb also then will have eject for an option.

---

### Post by TokyoYank on 2010-01-12
> **Marisa H said:**
> so it should be eject, right?

I've used Unmount in the past without data loss.

.. for those of us who click "Safely Remove" by mistake, besides a full reboot, does anyone know a smart way to get the card reader back?

---

### Post by warfacegod on 2010-01-12
> **TokyoYank said:**
> I've used Unmount in the past without data loss.

.. for those of us who click "Safely Remove" by mistake, besides a full reboot, does anyone know a smart way to get the card reader back?

If it's external then pull the usb and reinsert.

---

### Post by Ankur Dave on 2010-01-12
> **joshzam said:**
> It took me a very long time to learn the difference between these and I suffered for a long time. I have an internal multi-card reader with a built-in USB port. After I was finished with either a media card or a USB device, I would choose "Safely remove drive". WRONG! It took me weeks to realize that this was actually turning off the power to the entire card reader and I was unable to subsequently mount any other cards or USB devices until I did a reboot! I acknowledge that this action is sometimes desired, but this was not what I was expecting given the "friendly" description. Let's hope they see the error of their ways and come up with a more intuitive way of performing these actions.
I agree. Maybe the options could be renamed to be more clear:

[LIST]
[*]"Unmount": syncs the drive and removes it from the file system.
[*]"Unmount and eject": unmounts, then physically ejects the media. Although this is intended for CD drives, apparently it has to show up for USB drives as well; see [the upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5").
[*]"Unmount and power down": unmounts, then cuts power to the USB device.
[/LIST]

---

### Post by joshzam on 2010-01-13
> **TokyoYank said:**
> I've used Unmount in the past without data loss.

.. for those of us who click "Safely Remove" by mistake, besides a full reboot, does anyone know a smart way to get the card reader back?

Yes, I've started using Unmount and haven't had any issues.

And with my internal card reader, I haven't found any other (non-intrusive) way of getting the power back to the device without a reboot. Logging out and back in doesn't help.

---

### Post by joshzam on 2010-01-13
> **Ankur Dave said:**
> I agree. Maybe the options could be renamed to be more clear:

[LIST]
[*]"Unmount": syncs the drive and removes it from the file system.
[*]"Unmount and eject": unmounts, then physically ejects the media. Although this is intended for CD drives, apparently it has to show up for USB drives as well; see [the upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5").
[*]"Unmount and power down": unmounts, then cuts power to the USB device.
[/LIST]

This is a great proposal. Definitely more intuitive.

---

### Post by Marisa H on 2010-01-13
> **TokyoYank said:**
> I've used Unmount in the past without data loss.

.. for those of us who click "Safely Remove" by mistake, besides a full reboot, does anyone know a smart way to get the card reader back?


Hmm... Isn't there a way in xp to disable the USB controllers and then enable them again? Maybe there's something similar in Ubuntu where you can disable the host controller itself and then enable it, so it thinks the device was unplugged and then plugged in again?

---

### Post by spiderbatdad on 2010-01-13
> **BigBananaMan said:**
> I typically use Unmount on flash drives and Eject on optical disks because that's what I want to do.  I want the flash drive unmounted from the filesystem and the disk unmounted and ejected from the drive so I can put it back in it's case.  Personally I would prefer that they just have Unmount for drives and Eject for disks.  There is no instance I can think of where I want a disk to be unmounted but still stuck in the drive and I could just use umount /media/cdrom0 if that's what I wanted.  Safely Remove Drive seems to do nothing more than Unmount.

Now for a little fun I tried to set up another useless "Dangerously Remove Drive" option in Nautilus Actions Configuration that will make an annoying system beep to startle and prompt the user to yank the device out without unmounting it (I know I know, but somehow it makes sense to me).  Unfortunately, Beep, Echo, and even the mighty Python have failed to invoke a system beep :confused:

Perhaps something to do with blacklist pcspkr in /etc/modprobe.d/blacklist.conf

---

### Post by Leoncio on 2010-01-14
> **Ankur Dave said:**
> I agree. Maybe the options could be renamed to be more clear:

[LIST]
[*]"Unmount": syncs the drive and removes it from the file system.
[*]"Unmount and eject": unmounts, then physically ejects the media. Although this is intended for CD drives, apparently it has to show up for USB drives as well; see [the upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5").
[*]"Unmount and power down": unmounts, then cuts power to the USB device.
[/LIST]

Yep.  Amen to that!

---

### Post by ubfu on 2010-01-16
> **apalacheno said:**
> Does any of you know what command is actually triggered by the "Safely Remove Drive" option?

Cheers,
Robert
> **Hagen99 said:**
> Yes I am interest knowing which command do that I while researching a little about this topic and I am not able to find the proper command.

Thanks

Really ,I also wanted to know command to triggered "Safely Remove Drive".So I could implement it on Hardy 8.04.

Hope of it, and thank you very much :D

---

### Post by steve.horsley on 2010-01-16
I just tried this with a USB stick with a light on it, and I find that both Eject and Safely Remove cause the stick light to go out (I'm assuming power down) whereas Eject leaves the power on.

When the light is out, unplugging and re-plugging the stick causes the light to come back on. How can it tell the stick has been plugged in if there's no power to the socket?

---

### Post by joshzam on 2010-01-18
> **steve.horsley said:**
> I just tried this with a USB stick with a light on it, and I find that both Eject and Safely Remove cause the stick light to go out (I'm assuming power down) whereas Eject leaves the power on.

When the light is out, unplugging and re-plugging the stick causes the light to come back on. How can it tell the stick has been plugged in if there's no power to the socket?

If the USB port is directly on the motherboard, I don't believe it can be powered down (you can't power down the motherboard!) so plugging the stick back in will always work. The problem comes when a USB port is part of a peripheral, like an internal card reader. My card reader has a USB port that, once "Safely Removed" will not power back up until rebooted.

---

### Post by specialk1st on 2010-01-31
> **mcduck said:**
> Perhaps "Eject" will spit out the flash drive automatically? :D

That would be awesome!  LOL!!  :D ;)

---

### Post by rickabillie on 2010-10-30
I have a micro sd card reader (identifies as a mass storage device) and when I 'safely remove' it unmounts and then immediately re detects and remounts it.  When I 'Eject' it finally goes away...

---

### Post by Jazzy_Jeff on 2010-10-30
I find that eject always works better than safely remove device.

---

### Post by Ophidion on 2010-11-24
sorry post duplicated.

---

### Post by Ophidion on 2010-11-24
The difference as I experienced is:
"unmount" is like eject as the device still is powered by e.g., USB port, but all bindings to file system are broken.
"eject" will additionally eject a CD, DVD, ...etc.
"safe remove" will unmount and power off.
so for an external USB disk using safe remove will turn of the power so it stops spinning (a better option).

---

### Post by Ophidion on 2010-11-24
The difference as I experienced is:
"unmount" is like eject as the device still is powered by e.g., USB port, but all bindings to file system are broken.
"eject" will additionally eject a CD, DVD, ...etc.
"safe remove" will unmount and power off.
so for an external USB disk using safe remove will turn of the power so it stops spinning (a better option).

---

### Post by Ophidion on 2010-11-24
throughout my practice:
"unmount" and "eject" unmount the media and break any read write association to the file system but keeps the disk powered.
"eject" additionally ejects CD, DVD, etc...
"safely remove" unmount and power off the disk. So this is the best for an external hard disk so it will stop spinning before you unplug the USB.

---

### Post by AlexanderDGreat on 2011-07-18
On A USB Hard drive / thumb drive

Nobody mentioned that EJECT - empties files that you recently deleted on the hard drive.

Here's what I do, eject it first, anything, then go to places > Computer > Safely Remove - something wrong with this?

---

### Post by L a r r y on 2012-05-29
> **rickabillie said:**
> I have a micro sd card reader (identifies as a mass storage device) and when I 'safely remove' it unmounts and then immediately re detects and remounts it.  When I 'Eject' it finally goes away...
For what it's worth, I have a USB XD card reader, which I have been using as a thumb drive to transfer files between my Ubuntu 10.04 and 12.04 computers.

I believe i originally used "Safely remove," which turned off the light and caused the icon to go away.  Nowadays, that option reports that the device cannot be stopped, so I use the eject option.  And the light turns off on the reader and its icon goes away.  Perhaps if I put the card in my camera and format it, I can once again safely remove -- would be an interesting experiment.

I have had no problem using whichever option that works.  I am glad that both options are there.

---

### Post by TheMTtakeover on 2012-05-29
> **3rdalbum said:**
> 
Unmount is the correct language (but surprisingly a lot of Windows users don't know this word)..

Haha. That's very true. I had never heard the term unmount until I tried out Ubuntu

---

### Post by sffvba[e0rt on 2012-05-29
*Old thread is **old **and **closed**.*


404

---

