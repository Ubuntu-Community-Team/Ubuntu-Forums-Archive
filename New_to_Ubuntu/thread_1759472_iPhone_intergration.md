---
title: "iPhone intergration"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by Missi0n on 2011-05-15
when i installed Ubunut 11.04 as soon as i plugged in my iPhone it recognised it and i was able to access the folders

is there a way of getting this same intergration in Xubuntu?

Thanks
missi0n

---

### Post by iowabeakster on 2011-05-15
Are you just trying to have it auto-mount the file system (like a disk drive) when you plug it in?  Or some other specific software synchronization?

Try opening up applications>settings>removable drives and media.   Check off so that it automatically mounts drives when hot plugged and  removable media when inserted.

I don't know about the iphone (i have android).  My phone also has settings to determine how to react when plugged into the computer.  I need to select "mount as disk drive" if I want to move files between the phone and computer.

---

### Post by Missi0n on 2011-05-15
im trying to mount what even can be mounted, the iPhone is more locked down than android phones, when i booted into Ubuntu it automatically picked up the fact that there was photos and mp3's on the device that it could use and on Xubuntu it just feeds it power without even recognizing it or mounting it?

---

### Post by marvimoto on 2011-09-30
I have exactly the same problem even if I first installed ubuntu and after that installed xubuntu-desktop out of it.

there must be more people out there having the same problem.

isnt there a solution yet?

---

### Post by CVGH on 2011-09-30
Have you checked here:

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by bob12564 on 2011-12-16
Did anyone find a solution to this?  The thread ended without one.

My IPhone was instantly recognized with Ubuntu 10.10 with full access to the folders on it and with full integration to Rhythmbox.  I later did a clean install of Xubuntu 11.10 to escape Unity and found that Xubuntu does not recognize the Iphone.  I installed libimobiledevice2 per other posts but that didn't help.  Ubuntu 10.10 uses libimobiledevice1.  Xubuntu is supposed to be a leaner installation than Ubuntu so it's probable that Ubuntu installs Apple support by default while Xubuntu requires you to load it manually if you can figure out what to install.  The Iphone is also instantly recognized when I boot from the Ubuntu 11.10 live CD.

I compared the modules installed in Ubuntu vs. Xubuntu. Some posts recommended Ifuse but Ubuntu works without it so I doubt that's the problem.  If someone figured it out I'd appreciate the help!

---

### Post by d4m1r on 2011-12-16
> **Missi0n said:**
> when i installed Ubunut 11.04 as soon as i plugged in my iPhone it recognised it and i was able to access the folders

Never happened for me....In general, iPhone support is still spotty on Ubuntu, even on the newest versions and chances are you'll have to try various packages before it is even recognized (syncing is a whoooole other ball game).

---

### Post by bob12564 on 2011-12-17
I tried 3 computers running Ubuntu 10.10 and the phone was instantly recognized.  That surprised me but the Ubuntu community has been working hard on it and things are better than a few years ago.

I also tried Ubuntu 11.10 Live CD and that picked it up too.

The issue is with Xubuntu.

---

### Post by d4m1r on 2011-12-18
> **bob12564 said:**
> I tried 3 computers running Ubuntu 10.10 and the phone was instantly recognized.  That surprised me but the Ubuntu community has been working hard on it and things are better than a few years ago.

I also tried Ubuntu 11.10 Live CD and that picked it up too.

The issue is with Xubuntu.

I am using 11.04 (32 bit) and have an iPhone 4 running 4.x and it does NOT mount properly. What iPhone and iOS do you have? Were you able to read/write your pictures from a single mounted volume as "iPhone x"?

Sometimes it does mount, and I can copy photos over, but it often crashes and many a times I just get that "-12 mount error" or whatever :(

I really just wish Apple ported over iTunes to linux, as it would be a more native environment than Windows anyway and I like the interface, and it syncs just fine in my Windows 7 partition...

---

### Post by bob12564 on 2011-12-18
It's an IPhone 4 IOS v 4.1.

When I plug into an Ubuntu 11.10 computer I get a popup panel telling me that I plugged in a device that contains music or digital photos.  I can then open Nautilus and see the entire directory structure.  When I open Rhythmbox the phone is listed and I can open the music folder that contains the MP3s that I installed via ITunes on Windows.  I'm only adding MP3s at this time.  I can click one of the songs and it begins playing.  I also did a drag/drop from Rhythmbox to the desktop and the song was quickly copied.  I was able to then play the song from the desktop.

I've done some reading via Google and many seem to say that Ubuntu can handle Apple devices as of 10.04.  I did see a few Xubuntu users with the same issue I'm having.  The consensus is that libimobiledevice etc. is Gnome based and that there might be a Gnome module that needs to be added if anyone could figure out which one it is.  I also read that Thunar will not automount the IPhone and other devices unless GVFS is installed.  I did that already.  The mystery remains...

---

### Post by d4m1r on 2011-12-18
> **bob12564 said:**
> It's an IPhone 4 IOS v 4.1.

When I plug into an Ubuntu 11.10 computer I get a popup panel telling me that I plugged in a device that contains music or digital photos.  I can then open Nautilus and see the entire directory structure.  When I open Rhythmbox the phone is listed and I can open the music folder that contains the MP3s that I installed via ITunes on Windows.  I'm only adding MP3s at this time.  I can click one of the songs and it begins playing.  I also did a drag/drop from Rhythmbox to the desktop and the song was quickly copied.  I was able to then play the song from the desktop.

I've done some reading via Google and many seem to say that Ubuntu can handle Apple devices as of 10.04.  I did see a few Xubuntu users with the same issue I'm having.  The consensus is that libimobiledevice etc. is Gnome based and that there might be a Gnome module that needs to be added if anyone could figure out which one it is.  I also read that Thunar will not automount the IPhone and other devices unless GVFS is installed.  I did that already.  The mystery remains...


Interesting....Well, I can't on 11.04 (the majority of the time) and I get the infamous "-12 unable to mount volume" error....On a side note, 11.04 and I am pretty sure 11.10 both come with Banshee installed by default which doesn't support syncing with iDevices so you installed it later on for compatibility?

---

### Post by midden on 2012-03-14
I also miss the iPhone integration I had with Ubuntu 10.10. Now that I am running Xubuntu 11.10, I cannot get any automount of the camera or music. That said, Clemetine does allow me to manage music, but the iPhone never shows up as a drive. This is less than ideal, because I used to be able to manage my iPhone using iTunes in a Windows VM. Now, Virtual Box never sees the USB device and cannot do anything (that said, when I boot into my 10.10 partition, the same VM deals with the iPhone just fine).

Any further help will be appreciated.

---

### Post by bob12564 on 2012-03-14
You can get access in Xubuntu if you load the Nautilus file manager.  Once loaded it takes control and it'll work the same as in your Ubuntu 10.10 system.  Xubuntu defaults to the Thor file manager which doesn't handle the Iphone.

I solved my issue by deleting Xubuntu and going back to Ubuntu 11.10.  To get around Unity, I loaded the XFCE desktop (not the full system, just the desktop) that does not include Thor.  I also tried gnome-fallback-session.  Cinnamon is another up and coming desktop if you have 3D video support.

Good luck to you.

---

### Post by midden on 2012-03-14
I will give that a try, but I never liked how XFCE acted when I installed it on top of Ubuntu in the past. Xubuntu has been great except for the few little details that are mostly tied to Thunar (I admit 11.10 is my first attempt at a bare-metal install of Xubuntu, so maybe xfce4 works better over Ubuntu now).

Thankfully, I have learned the hard way and always keep a spare 15 GB partition around just to try out clean OS installs. I will let you know how it goes.

---

### Post by bob12564 on 2012-03-15
Unfortunately I can't remember which module I installed.  I dug deeply into Google posts to find it but I can't find it now.  You only want to load the basic desktop, not Xubuntu or the full XFCE package that will leave you with Thunar and probably make a mess of your Ubuntu setup.  You might have to research this one yourself if I can't find it.  I'd do the install from Synaptic and review the complete list of dependencies before actually installing anything.  If you see Thunar don't go further.

I went back to Ubunto for a few reasons: I found Xubuntu a bit buggy and I didn't like Thunar.  As you just discovered, Nautilus is more powerful even if it is bloated as some people say.  Also, just look around these forums and see how much Xubuntu support there is compared to Ubuntu support.

Windows 8 is also going the way of a touchpad menu system ("Metro") and it's split the Microsoft camp the same way Unity split the Ubuntu users.

Good luck.

---

### Post by bob12564 on 2012-03-15
Maybe this is the thread I used:

[http://ubuntuforums.org/showthread.php?t=1260279](http://ubuntuforums.org/showthread.php?t=1260279)

---

### Post by chrisfrench on 2012-05-27
I was able to grab file from the iPhone as a drive by navigating to this location: /home/[user folder]/.gvfs/[iphone name]

---

