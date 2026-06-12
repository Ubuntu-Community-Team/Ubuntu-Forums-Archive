---
title: "Trying to put music on an ipod"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Falc7 on 2009-02-02
I am trying to put music on my ipod, and having real difficulties.
I have very little experience with ipods, but here goes.

I moved the music (mp3 file), which was in a folder into the ipod using nautilus. I then unmounted the ipod, and tried to play music, the ipod would reset when i went into the music file. 

I have tried for ages to get this working and am a little sick of it tbh. I don't know if my ipod has a problem or what.

---

### Post by Crafty Kisses on 2009-02-02
What kind of iPod do you have?

---

### Post by Falc7 on 2009-02-02
I believe it is an ipod nano 2gb, i can take a pic if its useful. Its pretty small, the same width but not as long as a credit card. It was given as a present so i don't know much about it.

---

### Post by delta_one_ on 2009-02-02
> **Falc7 said:**
> I am trying to put music on my ipod, and having real difficulties.
I have very little experience with ipods, but here goes.

I moved the music (mp3 file), which was in a folder into the ipod using nautilus. I then unmounted the ipod, and tried to play music, the ipod would reset when i went into the music file. 

I have tried for ages to get this working and am a little sick of it tbh. I don't know if my ipod has a problem or what.
Copying the mp3 onto the ipod with nautilus will not add the song to the ipod's database so the ipod will not be able to play it. You need to use a program like gtkpod or songbird. I would recommend songbird ([http://www.getsongbird.com/](http://www.getsongbird.com/)).

---

### Post by Falc7 on 2009-02-02
okay thanks i will try that tomorrow and report back (going to bed now), is songbird preferable to rythembox or amarok?

---

### Post by delta_one_ on 2009-02-02
I have tryed all three and I found that songbird was the easiest to use. The interface is quite similar to iTunes. But rythmbox and amarok are also able to add songs to an ipod.

---

### Post by pHreaksYcle on 2009-02-02
It's all about Banshee right now, get the newest version from their repo they have set up. iPod is amazingly supported.

---

### Post by delta_one_ on 2009-02-02
> **pHreaksYcle said:**
> It's all about Banshee right now, get the newest version from their repo they have set up. iPod is amazingly supported.
Looks interesting. But it says it is "Unable to read your iPod" for my ipod. Songbird doesn't have a problem with it.

---

### Post by Falc7 on 2009-02-04
Okay I am trying with songbird first, i installed the addon 'ipod device support', but in his picture there is an option with ipod on the left menu. I don't get that, however i know ubuntu is seeing the ipod because it has it listed as 2.1GB media as a mounted drive. What should i do?

---

### Post by nothingspecial on 2009-02-04
While I have no problem with Amarok, Songbird, Rhythmbox etc and love Banshee, there is no easier way of managing your ipod than gtkpod.

That`s all it does, manage your ipod - no bells, no whistles. Just drag and drop the new tunes in and right click remove the tunes you don`t want.

If you want video, install gtkpod-aac.

---

### Post by 4MD D4D on 2009-02-05
If your still having an issue with this hit me back i also have a nano and have solved the issue may be able to help

---

### Post by GonZo on 2009-02-05
Hello everyone,

at home I can connect my jailbroked ipod touch 2g on linux through wifi with Openssh. But at work we have Ubuntu linux 8.04 machines without wifi. I would like to mount Ipod device through USB, in the same way that "Iphone Tunnel Suite" (just for windows) does it.
I've tried to reach the ssh port but I don't know how to create a tunnel through USB.

Any ideas?

---

### Post by Falc7 on 2009-02-07
Still no luck with gtkpod, i press load ipod, and nothing happens :/

---

### Post by nothingspecial on 2009-02-07
Try dragging your music directory straight onto the ipod icon in gtkpod.

---

### Post by Falc7 on 2009-02-12
The only ipod-like icon in for the 'load ipod' button, which unfortunately, won't let me drag onto it, i will make a small video and upload it to youtube showing what happens once i put the ipod in

---

### Post by rgb96 on 2009-02-12
I'm pretty sure Ipods play MP4s, not MP3s. That could be your problem.

---

### Post by kanikilu on 2009-02-12
iPod's have no problem playing MP3's. From Apple's site:

> Audio formats supported: AAC (16 to 320 Kbps), Protected AAC (from iTunes Store), MP3 (16 to 320 Kbps), MP3 VBR, Audible (formats 2, 3, and 4), Apple Lossless, AIFF, and WAV

Personally, I have an iPod Classic and find that amarok is the best app for me, but Banshee and Songbird (with some quirks) work as well. Haven't had a need to try gtkpod, but have heard of it...

---

### Post by Falc7 on 2009-02-18
Here is the vid, hope it is clear enough:
[http://www.youtube.com/watch?v=wF5t5hR3hZs&feature=channel_page](http://www.youtube.com/watch?v=wF5t5hR3hZs&feature=channel_page)

---

### Post by nothingspecial on 2009-02-18
There should be an ipod icon underneath the two on the left.

[[IMG]http://www.picamatic.com/show/2009/02/18/09/13/2258291_bigthumb.png[/IMG]](http://www.picamatic.com/view/2258291_Screenshot-gtkpod/)

What sort of ipod do you have?

---

### Post by Dougie187 on 2009-02-18
If this is the first time you have used this iPod you have to format the storage space it uses. 

DON'T Just go and format it with gparted. There are some steps for it to make sure you don't mess up your iPod.

when you first buy an iPod they are formatted with HFS+ which is a Mac only format. If you plug it into a windows machine it will format to NTFS automatically, but there are some ways you can go about doing it on linux too. If you have a windows machine I would recommend connecting it to iTunes in that first, and then try any of the solutions provided to you in moving songs onto it. If you don't have a windows computer, and this is a brand new ipod, post back and I'll see if I can find you a walkthrough on formatting it.

I would recommend using gtkpod or rhythmbox just to start, then after that move on to what ever you want to use.

---

### Post by nothingspecial on 2009-02-18
You may be right but I really don`t remember formatting my ipod which has never met itunes, windows or a mac.



But then I have an awful memory.:D

---

### Post by Dougie187 on 2009-02-18
Heh, my mom just got a new ipod this weekend, and her's had to be formatted. Thats the only reason I know this.

---

### Post by bostonaholic on 2009-02-18
I've had iPod issues with both Amarok and Rhythmbox, I will try songbird tonight.

I have done some research on Songbird and I saw there is a plug-in to import an existing iTunes Library file!  This is HUGE for me because I have missed my playlists that I created on iTunes.  When I did the full XP > Ubuntu switch not too long ago, I saved the playlist files that keep all that data.  So I'm very excited to try out the import (once I do a global find/replace of the file locations of course).  :woot:

---

