---
title: "Accessing files on USB external drive"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Garthhh on 2009-11-18
Up & running w/8.04 on celeron3 desktop
I have a Seagate go 250g with Itunes & 10k songs that I use for library/backup & shuttle between  vista & XP lap tops
when I plug it in I can see all the music files [nested inside a itunes music folder] in the file browser how do I find them in rythymbox?
I'm still trying to get a handle on the mounting stuff?

---

### Post by herbertportillo on 2009-11-18
When you go to Places -> Computer, do you see the external hard drive when it's plugged in?

---

### Post by Garthhh on 2009-11-18
yes I can even go to individual folders, songs, but not in rythymbox[which I'm not attached to]
I want to be able to add files to my libirary on the external as I convert more lp's to mp3
I also need to deal with my ipod , which I can do from one of the windows machines if needs be but I'm not attached to itunes either

---

### Post by Charlietje on 2009-11-18
Can you find your usb stick under 
```
/media/*name_of_usb_stick*
```

---

### Post by Garthhh on 2009-11-18
I can see the files I just can't play them from file browser
I guess I'm asking a rythymbox question, I couldn't find anything about it in the manual that helped me understand.
I can't just import everything the HDD [internal] wouldn't hold it all & I'm trying to keep the music all on the external HDD

---

### Post by sgosnell on 2009-11-18
If you want to rip files to mp3, you can rip them directly to the external drive, to whatever directory you want.  Whatever program you're using to do the conversion should see the drive.  What are you using - Audacity?  Should be no problem at all to rip directly to the drive, or you can rip to an internal drive and then copy to the external drive, your choice.  I'm not a fan of Banshee either, but it's the most capable I've found for dealing with players if you want synchronization.  Personally, I just copy the files, or else use rsync to do the sync.  It doesn't have the same interface as something like Windows Media Player or whatever, but it works.  You can use rsync to sync any sets of directories you want.

---

### Post by JBAlaska on 2009-11-18
When you click on "import folder" in rythymbox, it just indexes your songs, not "import" them to another drive...kinda confusing I know, nevertheless, just click on "import Folder" then point to your itunes folder on your external drive and you should be good.

---

### Post by Shpongle on 2009-11-18
you could always point rhythmbox to the directory on your hdd , that should add them all to your library , and youll be able to play as long as its connected,  you can set your library location in the preferences of rhythmbox

---

### Post by Garthhh on 2009-11-18
Ok i get it I'm just defining the path..

I haven't installed audacity yet, I also liked MP3 direct cut to edit with [more straight forward than audacity] & finally ID3renamer or Itunes to fix up the info.  this was the process in XP, I'll figure out what makes sense,for unbuntu  
any more suggestions?
Most of my 10,000 songs are from lp's.  I like all the album info to be right, but don't care so much about song titles.

Any insight into how to deal with my ipod?  there's 30 or 40 songs that aren't in my library, I need to recover?

---

### Post by sgosnell on 2009-11-18
There are a number of apps that will deal with the mp3 files, so use what you like.

I can't help much with an ipod, I've never owned one and never will.  Can't you copy files from it to a local drive?  Is itunes the only way to transfer files?  If so, that's a piss-poor implementation, but it certainly makes sense from an Apple point of view - make the masses use your hardware and software.  I use neither.  If you can copy files from the ipod, it should be easy to put them on any HDD, but I have no idea how to do that.

---

### Post by Garthhh on 2009-11-18
the whole itunes package works fine in windows the way I was using it, none of my files were "protected"
as soon as you buy tracks from them you only have limited rights to copy [those files] & such.
I can always bring em in as straight audio, just like I do LP's
having 5000 songs plugged into my car stereo for a $20 cable is cool, keeps it charged, full access to playlists thru the carstereo interface not something the other players [mp3] did at the time i bought the pod...
mp3 encoded CD's are fine too

---

