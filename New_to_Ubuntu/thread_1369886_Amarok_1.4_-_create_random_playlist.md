---
title: "Amarok 1.4 - create random playlist"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-01-01
First a little bit of background. I use Amarok 1.4 in ubuntu as I have found it offers me the ability to create compilation albums that no other music player seems to support. This is where an album is made up of different artists (e.g. a soundtrack to a film). In most other apps the artists are all shown separately creating confusion (as sometimes I may not even know who the artist is!). Anyway this isn't really relevant to my problem.

I have both a 80gb iPod Classic and a **HTC Magic** with an **8gb SD card**.

I have a total of about **10000 songs (75gb)**. Out of this I have made a playlist of about **2500 songs (20gb)**.

Obviously I cannot simply transfer the 20gb playlist onto my Android phone as it only has 8gb of space (and I have used about 2gb of space with photos and other junk). 

So, here is what I would like to do, and I don't mind using any method to do this.

I somehow want to take my 2500 song playlist and have Amarok generate a random playlist that is about 4gb in size. So, essentially Amarok should pull about 400-500 songs from my 2500 song playlist and make a new random playlist that I can then transfer to my phone. I would like this new playlist to be random so that every month or so I can re-generate this playlist and have a new set of 400-500 songs (out of my original 2500 song playlist).

I have looked at the "Smart Playlists" and "Dynamic Playlist" but none of them seem to support this feature (of creating a playlist out of another playlist and setting it to a certain size).

I wouldn't mind if there was a method outside of Amarok, but, since I use Amarok to transfer the music to both my iPod and HTC it would be preferable if it was all Amarok based.

Thanks for reading!

---

### Post by Daveth on 2010-01-02
this any good?

[http://techie-buzz.com/audio-tools/smart-playlist-generator-for-linux.html](http://techie-buzz.com/audio-tools/smart-playlist-generator-for-linux.html)

---

### Post by abhiroopb on 2010-01-03
Thanks for that...had some problems installing the deb package:

```

sudo dpkg -i gjay_0.2.8.3-1_i386.deb 
Selecting previously deselected package gjay.
(Reading database ... 228890 files and directories currently installed.)
Unpacking gjay (from gjay_0.2.8.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gjay:
 gjay depends on libgsl0 (>= 1.4); however:
  Package libgsl0 is not installed.
 gjay depends on xmms; however:
  Package xmms is not installed.
dpkg: error processing gjay (--install):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Processing triggers for man-db ...
Errors were encountered while processing:
 gjay

```

I couldn't find the libgsl0 (in ubuntu 9.10 Karmic) and there was only xmms2. Any thoughts where I can get the appropriate packages?

Thanks

---

### Post by Daveth on 2010-01-04
you could try lobbying this guy!

[http://www.enc.com.au/sees-blog/2009/12/updated-psmisc-gw6c-and-gjay.html](http://www.enc.com.au/sees-blog/2009/12/updated-psmisc-gw6c-and-gjay.html)

or some of these versions

[http://linuxappfinder.com/package/gjay](http://linuxappfinder.com/package/gjay)

or this

[http://ns2.canonical.com/jaunty/libgsl0-dev](http://ns2.canonical.com/jaunty/libgsl0-dev)

---

### Post by mc4man on 2010-01-04
I don't know why you don't just do it in amarok, occasionally do something similar with a ipod. (though the scale is a bit less, 1000 -> 250

Just load the main playlist, have amarok randomize it (shuffle, can do once or more), remove the bottom 4/5's give or take , save as a new playlist and transfer that list over.

---

### Post by abhiroopb on 2010-01-04
> **Daveth said:**
> you could try lobbying this guy!

[http://www.enc.com.au/sees-blog/2009/12/updated-psmisc-gw6c-and-gjay.html](http://www.enc.com.au/sees-blog/2009/12/updated-psmisc-gw6c-and-gjay.html)

or some of these versions

[http://linuxappfinder.com/package/gjay](http://linuxappfinder.com/package/gjay)

or this

[http://ns2.canonical.com/jaunty/libgsl0-dev](http://ns2.canonical.com/jaunty/libgsl0-dev)

Thanks I tried libgsl0-dev. It doesn't work. As in the gjay package still asks for libgsl0.

I'll take another look at the links thanks.

---

### Post by abhiroopb on 2010-01-04
> **mc4man said:**
> I don't know why you don't just do it in amarok, occasionally do something similar with a ipod. (though the scale is a bit less, 1000 -> 250

Just load the main playlist, have amarok randomize it (shuffle, can do once or more), remove the bottom 4/5's give or take , save as a new playlist and transfer that list over.

How do you "shuffle" a playlist? I know there is the "shuffle" button but this doesn't shuffle the songs themselves just the order they are played in. The only way I can see is to organise the songs by some arbitrary characteristic and have them sorted in that way.

Actually, this is pretty much what I have been doing for the past few days! Not ideal, as it takes a lot of time and isn't the cleanest way to do it. If I had a dynamic playlist that was created each time I could just sync it whenever I wanted, much cleaner.

---

### Post by mc4man on 2010-01-04
> How do you "shuffle" a playlist

Maybe it's a diff. in devices, or we're talking something different.

The tracks themselves, because they're all tagged properly, end up in the ipod (if not already) in folder/subfolder in the proper place and order.

What i'm adding (in addition to any new tracks) is a new playlist in the playlist section where the play order was randomly picked back in amarok.

Basically, -  new playlist in amarok, shuffle, save playlist as.., and then add that playlist to the ipod.

---

### Post by abhiroopb on 2010-01-05
Right I get what you are saying but how do I "shuffle" the playlist in amarok? What button do I press to shuffle and then save it?

By the way I am using Amarok 1.4

---

### Post by mc4man on 2010-01-05
Unfortunatly the bigger ipod is with my son on a trip, though I do have a 1gb around if you need some screens. ( and don't know if your device works the same.

If you loaded your tracks into amarok (right side), then just click on the 'playlist' tab -> shuffle. You can shuffle multiple times if you wish.

Then if need be remove 'extra' tracks to reach size, then again in the playlist tab -> save as. Give it a name  (random1 for instance) and save as an .m3u to somewhere else. (save to location
( I keep a folder on desktop that has lots of .m3u's, .pls's, .xspf's

Then  in the device screen drag  the random1.m3u into the device queue box and tranfer.
You should get a new playlist in your device (random1 or whatever

---

### Post by abhiroopb on 2010-01-05
> **mc4man said:**
> Unfortunatly the bigger ipod is with my son on a trip, though I do have a 1gb around if you need some screens. ( and don't know if your device works the same.

If you loaded your tracks into amarok (right side), then just click on the 'playlist' tab -> shuffle. You can shuffle multiple times if you wish.

Then if need be remove 'extra' tracks to reach size, then again in the playlist tab -> save as. Give it a name  (random1 for instance) and save as an .m3u to somewhere else. (save to location
( I keep a folder on desktop that has lots of .m3u's, .pls's, .xspf's

Then  in the device screen drag  the random1.m3u into the device queue box and tranfer.
You should get a new playlist in your device (random1 or whatever

Thanks for the quick response.

The shuffle button is just what I was looking for! Is there any way to delete a certain number? Except by just guessing I mean?

---

### Post by mc4man on 2010-01-05
> Is there any way to delete a certain number
Not that I know in amarok but...

If you save the entire playlist to a .m3u, then open it it a text editor (gedit

Figure 2 lines per track so you can at least quickly narrow it down as to number of tracks - 500 hundred tracks is line 1000.

As far as size, don't know, though back in the device queue amarok should report that.

---

### Post by abhiroopb on 2010-01-05
Thanks! Very helpful :) Syncing now

---

### Post by abhiroopb on 2010-01-05
I think Android is having trouble reading the playlists created by Amarok.

So, I made a playlist with 100 songs (as a test). I did Transfer to Media Device, then I started the transfer. The songs all transfered fine but the playlist wasn't there. So, I created a "Playlists" folder in the "Music" folder in Amarok and copied the .m3u file into it. But, it does not show up under "Playlists" in the music app.

Any suggestions?

---

