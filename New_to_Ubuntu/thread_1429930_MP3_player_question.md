---
title: "MP3 player question"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by Crossbow on 2010-03-14
I'm running Ubuntu 9.10. My MP3 player is a Creative MuVo TXFM. I can't seem to run the software that came with it, and I don't know what else I can use. I tried Gnomad 2 and KZenExplorer, but neither of them could see my player. I was hoping the original software would work with Wine, but Wine doesn't seem to see it either. 

I can actually just do this on my roommate's Windows machine, it just takes **forever.** If I can do it on my machine, it will just be easier.

---

### Post by cap'n leaky on 2010-03-14
I'm not sure I understand the problem. Doesn't it show up as a USB drive when you plug it in, so you can just drag-n-drop?  Why do you need to use the software?

I have a Creative MuVo V100 which just shows up just like a thumb drive.  I also have a Creative Zen Nano which does the same thing.  Never used the software that came with either on Linux or Windows.

---

### Post by colobix on 2010-03-14
Well, If I understand you correctly, it comes up as a usb driver but doesn't work because the windows installation comes up instead of the music folder, right? Well, in that case it will appear in rhythmbox and most of the other music programs.
So all you have to do is to drag and drop music files from your music library to the mp3 player.

---

### Post by Crossbow on 2010-03-14
I tried dragging and dropping. It appeared to work, but when I removed the USB drive, none of my changes were on it.

ETA: Yes, it shows up like any other thumb drive. I can add and remove files like normal. BUT, when I remove the drive, I find that nothing I've done has been saved.

---

### Post by sandyd on 2010-03-14
have you tried connecting the mp3 player in msc mode?

---

### Post by Crossbow on 2010-03-14
> **carlee said:**
> have you tried connecting the mp3 player in msc mode?

I don't know what that means.

---

### Post by mcoleman44 on 2010-03-15
Did you unmount the device before you removed it?

---

### Post by TracyO on 2010-03-15
I'm also having Gnomad issues.  I've used it with my Creative Zen Sleek since Hardy with no problems.  I recently upgraded to 9.04, and I have that same problem that the original poster does.  It recognizes it as a USB device, but cannot find the contents within Gnomad.  

The last time I played around with it, I somehow got it to work (after trying and fiddling many times), but this time, I'm stuck, too.  I think what happened was that I attempted to drag and drop files, it got confused and froze, and then the next time I started Gnomad, it found the Jukebox.  Something like that.

Update:
I got it to work.  This may not be the only way, but it worked for me.  I plugged in the mp3 player, logged out, logged back in, and when I started Gnomad, it scanned the data/tracks.  Good luck!

---

### Post by quantumspiral1919 on 2010-03-15
You should be able to use rythembox to manage your device, dose the software recognize your mp3 player?

---

### Post by cap'n leaky on 2010-03-15
I think mcoleman44 is correct: make sure you unmount it before you unplug it.  If you don't, the changes won't stay, and you may mess things up.

Just right click on it's icon (it should be on the desktop if you use Gnome) and choose "unmount".  Don't unplug until the icon disappears.

---

### Post by kekkrasta on 2010-03-16
I have the same problem and rhythmbox doesn't recognize my creative zen!

---

### Post by cap'n leaky on 2010-03-16
I don't know how to help with having the music player software recognize the Zen, as I don't "sync" with the player.

I usually use Rhythmbox as well to listen to my collection on my PC (or other network shares), but I don't connect to my MuVo through it.

I just plug it in like a thumb drive and drag-n-drop whatever I feel like listening to at the time from my music folders.

I've just tried Rhythmbox, Banshee, and Exaile and none of them seem to recognize when I plug in my player.

---

### Post by kekkrasta on 2010-03-17
I usually use the drag'n'drop mode but after the drop and the correct unmount of the creative zen,i can't find the songs in the player.
And on the other side rhythmbox and gnomad2 don't recognize it.

---

### Post by Seamyst on 2010-03-17
In order to get gnomad2 to recognize your player, you need to plug it in, unmount it (leave it plugged in!), and then open gnomad2.  That should get it working.

---

### Post by kekkrasta on 2010-03-18
Ok it's functioning thatway Seamyst,but do I have to put necessarily one song at a time?

---

### Post by kekkrasta on 2010-03-18
In the sense is it possible to put the all folder in the mp3 player?

---

### Post by Seamyst on 2010-03-18
You can transfer the contents of one folder at a time.  You could also, I imagine, copy or move all of your songs to one folder, then just highlight and transfer everything to the player in one go.  (I wouldn't really recommend this, though, as it would make things confusing if gnomad2 froze or otherwise had problems transferring something.)

---

### Post by admiralspark on 2010-03-18
Software problems with Creative Zen's is a known problem, though there's not much here in the Forums about it. Ubuntu mounts the Zen's as a USB and transfers files as if it was a thumbdrive. I own a Creative Zen 2gb, and I've had to resort to using windows for the file transfers so far. The filesystem of the Zen's is different than a simple file transfer--each artist has their own folder, and the Zen's software has to be updated after a transfer.

All in all, it's easier on windows (for now). Oh well :-(

---

### Post by TracyO on 2010-03-20
With my Zen Sleek, I've been having much better luck for years in Ubuntu than in Windows.  I don't transfer huge amounts of files at once in Gnomad, but it can definitely handle multiple files.  

Personally, I never liked the Windows software, but everyone's using these devices according to their own needs.  It didn't work for me, but it looks like it works better for you.

Good luck--I hope you get it going as you'd like!

---

