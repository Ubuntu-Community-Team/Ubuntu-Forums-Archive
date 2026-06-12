---
title: "How can I get an IPOD to work as a rockbox, not an IPOD?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by w.g.hanna on 2008-12-27
I run ubuntu hardy heron, and have been doing so for about six months.  I have rhythmbox and banshee - i try to avoid dowloading kde programs so i don't have amarok.  

I installed rockbox on a gen 5 ipod video pursuant to the instructions found here:  [http://mikesubuntu.blogspot.com/2007/10/how-to-install-rockbox-and-extras-on.html](http://mikesubuntu.blogspot.com/2007/10/how-to-install-rockbox-and-extras-on.html)

rockbox seems to work fine - i get a blue bootloader screen where i can select rockbox, rockbox loads, and i can surf various menus - even load doom.  now i need to get music on.

i plug it in via usb, and at first rockbox has a screen showing a usb plug - but then the apple logo appears and it switches to the ipod screen "do not disconect"  both rhythm box and banshe recognize it as an ipod.

as advised in a forum, i create a folder .is_audio_player  in the ipod.

same thing happens

i edit the contents of that folder to read:  audio_folders=iPodControl/Music (copied and pasted from a forum)

same thing happens

then i disable ipod plugins in both banshee and rhythmbox

basically, the same thing happens - but i can't write onto the ipod on rhythmbox and banshee doesn't recognize anything

then i use synaptic to remove several ipod related packages - and it ends up removing rhythmbox itself!  when i hook up the ipod, it still switches to ipod mode.  banshe doesn't recognize it.  

one forum siad you have to modify the hal file to take out ipod recognition, but (a) i don't know what the hal file is, and (b) googling hal file gives me the impression it is a pretty important system tool a novice like me runs a good chance of botching up

i'm kind of at a lass.  i'm running out, so i can't post any quick follow ups, but i hope somebody has a suggestion.  i'm about to load a mandriva disk that came with a magazine i got for christmas just to see if it works - actually, i'm curious to try it anyway.  but ubuntu is my long term desk top and i'd like to get it to work.

---

### Post by jimmy the saint on 2008-12-27
If Rockbox works, why are you trying to transfer music that way at all?  The beauty of rockbox is that you can just transfer your music over just like the ipod was a harddisk.  You just drag and drop your music into your music file and rockbox will recognize it.  You can have rockbox build its own music database as well so that itunesdb is not needed at all. 

Remember, when you buy an apple product you are buying locked hardware.  Any linux program that works with it only does so becasue someone found a way to get around apple's lockouts.  Apple does not want you using an ipod without buying a macbook, an apple router, an apple this and and an apple that some apple flotsum and some apple jetsom.  Rockbox allows you to get around that by simply loading an alternate OS altogether.

Have a look through this manual to learn more about getting music on and off of a rockbox ipod.
[http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html](http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-build.html)

---

### Post by w.g.hanna on 2008-12-27
The reason I want to use an interface like Rhythmbox or Banshee to manage my Rockbox Ipod is because those programs organize my music for me.   For example, sometimes I like to listen to every song that starts with the letter L by every band in my collection.  You know what a hassle that is when your managing a device via drag and drop?  

At any rate, rhythmbox and banshee are tools that I'd like to use to manage my audio devices, including a rockbox ipod i'm experimenting with.  Is this not possible in ubuntu?

---

### Post by w.g.hanna on 2008-12-28
i figured out a work around, in case anyone is interested.  use rhythmbox to transfer the music you want to the ipod.  the music finds itself in a folder named "ipodcontrol" and then inside a subfolder named "music".  cut and paste the music into the root folder of the ipod.  that made the music accessible to rockbox, only adding a couple simple steps.  

thanks!

---

### Post by jimmy the saint on 2008-12-28
make sure to mark this as sloved so that everyone knows there is a solution here

---

