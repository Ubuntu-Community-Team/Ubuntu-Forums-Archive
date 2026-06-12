---
title: "mp3 players"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-24
We have two mp3 players that both recommend using Windows media player to access the player to load music, etc. Now, they don't say that Only windows media player will work.. 

Anyone using other than Windows media player for their mp3 players? I'm up for recommendations, suggestions, etc. Thought I should ask before I do something desperate since I Lost the music off Windows, the only copies I have are on my player :)

myst - who hopes you're not heartily sick of her yet!

---

### Post by SuperSonic4 on 2009-04-24
Without knowing what mp3 players you're using it's pretty much impossible to tell you if you'll have success. Most of the current linux media players support devices now - for example I use amarok to sync my iPod

---

### Post by MyR on 2009-04-24
I've used my Dell DJ on linux.

peace

---

### Post by mystmaiden on 2009-04-24
Oops, you make a very good point. 

One is a Phillips GoGear 1 gig the other is a Sansa

---

### Post by MyR on 2009-04-24
> **mystmaiden said:**
> Oops, you make a very good point. 

One is a Phillips GoGear 1 gig the other is a Sansa

[http://opengogear.sarovar.org/](http://opengogear.sarovar.org/) this might help

peace

---

### Post by Dileeshvar on 2009-04-24
Hi you can rhythmbox this will help you.

---

### Post by mangurt on 2009-04-24
I have a COWON A3, and it absolutely rocks!

---

### Post by llamabr on 2009-04-24
My sansa e280 mounts with no trouble.  I've also installed rockbox on it, which, in my opinion, has a cleaner filesystem manager.

---

### Post by mystmaiden on 2009-04-24
Thanks for the link MyR that may be what I need. I tried  my gogear on Rhythmbox with it but it didn't give me sync options.

It occurred to me that watch instantly on Netflix requires Windows Media Player as well. - Anyone had any luck with watching that on linux with something other than Windows Media Player. (wonder if I can get it going with wine..) edited to add the system requirements actually say it requires Internet explorer.. but I'm pretty sure when you try to play the movies it tells you windows media player, too

I think I've highjacked my own thread, heh.

---

### Post by mystmaiden on 2009-04-24
To get back to my original topic here. I looked at the page MyR gave the link to and it offers: 


[LIST]
[*]openGogear 0.01 [source code]("http://sarovar.org/download.php/516/openGogear-0.01.tar.bz2")
[*]openGogear 0.01 [debian package for i386]("http://sarovar.org/download.php/524/opengogear_0.01-1_i386.deb")
[*][JGoGear 0.01]("http://sarovar.org/download.php/633/openGogear_java-0.01.tar.bz2")
[*][gogear_mgr 0.01]("http://sarovar.org/download.php/632/gogear_mgr-0.01.tar.bz2")
[/LIST]
I chose the debian package but got this error - 

error: dependency is not satisfiable: libid3-3.8.3

---

### Post by mystmaiden on 2009-04-24
I tried rhythmbox again, this time it did not even recognize the player, but searching around in rhythmbox help I found a section that says it does not work to delete files from the player or copy them to it, so its definitely not going to be helpful.

---

### Post by durand on 2009-04-24
You might have more luck with amarok, another music player.

```
sudo aptitude install amarok
```

It should then be in Applications > Sound & Video

---

### Post by mystmaiden on 2009-04-24
I installed anarok and it helped some, as it reads and plays the .alb files but I may be doing something wrong still. When I plug in my Phillips gogear, nothing happens in anarok but a phillips file opens. Maybe I am missing a step. I have the cd that came with it, do I need to run it. I was a little leery of doing that before I snagged the music off the player because it reformats the thing and wipes it clean.

mystmaiden

---

### Post by ymra on 2009-04-24
Have you tried using the file manager to access them?  That is how I have always updated my mp3 player.

---

### Post by durand on 2009-04-24
Well, if you're worried about loosing your music, you could back it up first:
[http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd](http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd)

With a google search, I found this thread: [http://ubuntuforums.org/showthread.php?t=570121](http://ubuntuforums.org/showthread.php?t=570121) Basically, you need to install a program called gnomad.

```
sudo aptitude install gnomad
```

I think the problem with your mp3 player is that it's a propreitary one and it has it's own way of doing things rather than the standard usb file system method.

---

### Post by jimmy the saint on 2009-04-24
If you add the file .is_audio_player to the root of the mp3 player to allow rhythmbox to recognize it as an audio player.  You will need to put a few simple lines in the file to tell rhythmbox how to use the device. It is actually very easy.  Just use gedit (text editor) to make the file and save it as .is_audio_player (the . is important)

Please read this page before you do it so that you understand. It is incredibly easy, but if you don't see why you are doing it, you can make a mistake and never figure it out!

[http://michael-peeters.blogspot.com/2008/06/rhythmbox-meets-mp3-players.html](http://michael-peeters.blogspot.com/2008/06/rhythmbox-meets-mp3-players.html)

---

### Post by mystmaiden on 2009-04-24
I'm not sure I understand how you're doing that, what I do not seem to have is some sort of interface. When I click on phillips, it just opens a file. Are you dragging and dropping or ?

---

