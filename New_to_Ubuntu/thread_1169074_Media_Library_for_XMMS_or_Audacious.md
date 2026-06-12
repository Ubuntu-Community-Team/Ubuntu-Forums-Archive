---
title: "Media Library for XMMS or Audacious?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-24
I've been looking for a good replacement for Winamp now for the past 2 years and can't seem to find anything that comes close.

I've tried Amarok, Rhythmbox, XMMS, Quod-Libet, Songbird (it's getting there), VLC, mPlayer, Kaffeine, Audacious, Banshee, Helix Player, Exaile, Elisa, and more.

What I'm really looking for is Audacious or XMMS (Winamp-Like) with a "Media Library" managing tool. If I can find that, ill be set. 

If you look at Winamp, it has a Media Library Managing tool.

Is there a media library plugin for XMMS or Audacious???

---

### Post by kellemes on 2009-05-25
> **asuastrophysics said:**
> I've been looking for a good replacement for Winamp now for the past 2 years and can't seem to find anything that comes close.

I've tried Amarok, Rhythmbox, XMMS, Quod-Libet, Songbird (it's getting there), VLC, mPlayer, Kaffeine, Audacious, Banshee, Helix Player, Exaile, Elisa, and more.

What I'm really looking for is Audacious or XMMS (Winamp-Like) with a "Media Library" managing tool. If I can find that, ill be set. 

If you look at Winamp, it has a Media Library Managing tool.

Is there a media library plugin for XMMS or Audacious???

What you're saying is you want WinAmp for Linux.
You won't find it..

Personally I'm using Amarok 2.0.96, don't really see what makes WinAmp's media management better. But it's a long time ago I've used WinAmp anyway..

Maybe if you explain what's wrong with all the packages you tried we can help you find an alternative for WinAmp.

---

### Post by kimda on 2009-05-25
I would stick with Audacious. It's probably the most similar player to winamp.  Maybe you can get someone to write a plugin to provide this functionality.
Another option would be installing winamp in wine if you really cannot live without this media library.

---

### Post by jocko on 2009-05-26
The reason audacious exists is to provide a simple, no-nonsense music player.
It was started as a reaction to the decision to change it's predecessor (beep media player) from a simple music player (like xmms and old winamp2) to more of a media library manager (like rhythmbox, listen, songbird, itunes, winamp5 and so on...).
I doubt you'll find any media library plugin for audacious, as I guess most people that prefer audacious over the other media players do so *because* it's simple and see no reason to make it into a clone of the others with media managers and database engines.
Forget about xmms. It was discontinued several years ago.

I like audacious because it behaves the way I want it to. I want to be able to drag and drop files into the playlist editor to make a playlist of hundreds or thousands of songs without first having to build a huge database of the files (which may take several hours with my mp3 collection). I know where I store my mp3 files, and don't want to have the computer waste a lot of memory, cpu cycles and disk space on making a database of what I already know.
The only thing I find missing is the ability to search in the playlist.

---

### Post by BoyOfDestiny on 2009-05-26
> **jocko said:**
> The only thing I find missing is the ability to search in the playlist.

Good news for you, press j
It brings up the playlist search :)

As for the original poster, Audacious has everything you'll need but that Media management type thing. 

My suggestion, save multiple playlists, and it's easy to load the one you want.

Or, add the whole directories to a playlist, and use "jump" (press j) to get the songs you want on the fly. 

Audacious can handle thousands upon thousands of entries in the playlist (more so in the new release 2.0.1)

Lastly, someone may indeed write a plugin use what you need. Of course, you can use more than one media player too...

---

### Post by jocko on 2009-05-26
> **BoyOfDestiny said:**
> Good news for you, press j
It brings up the playlist search :)
Dude! Thanks, I have checked the manual several times and never seen it. Must be getting blind.

---

### Post by asuastrophysics on 2009-05-27
> **jocko said:**
> The reason audacious exists is to provide a simple, no-nonsense music player.
It was started as a reaction to the decision to change it's predecessor (beep media player) from a simple music player (like xmms and old winamp2) to more of a media library manager

but it doesnt seem to be any different from XMMS or Winamp2 (actually, it's winamp3). what media library manager does it have? it can build playlists, yes. but so could XMMS and Winamp2. I'm really surprised that in the 7 years since Nullsoft's source code was released, nobody could figure out how to make a media library plugin.

it's a shame. winamp was my favorite music player and i lost it in the linux transition :(

---

### Post by Karaden on 2009-05-27
Hi - I've been having the same thoughts as you, really. Seems everyone either wants a huge, screen-dominating iTunes-like type app, or a tiny little pretty thing with no real power. 

Amarok and Rhythmbox have nice media libraries nice and all, but for me, they're just too unwieldy. I prefer my music players to be as small and inconspicuous as possible. Audacious fits that part beautifully, but the lack of a library (intentional or not) was just a killer. Guess I'm just too picky for my own good ;)

The closest I've found so far to a media library plugin for Audacious is the methlab library. I've only just started playing with it, so I can't really say if it's any good yet, but it's worth a look, right?

Instructions here: [http://ubuntuforums.org/showthread.php?t=680736](http://ubuntuforums.org/showthread.php?t=680736) 

They seem to be pre-Gutsy, but they worked alright for me, other than one line - you'll need to use "svn checkout" instead of "svn co"

Methlab homepage is here: [http://methlab.thegraveyard.org/wiki](http://methlab.thegraveyard.org/wiki) 

Hope that helped!

---

### Post by NESFreak on 2009-05-27
> **Karaden said:**
> Hi - I've been having the same thoughts as you, really. Seems everyone either wants a huge, screen-dominating iTunes-like type app, or a tiny little pretty thing with no real power. 

Amarok and Rhythmbox have nice media libraries nice and all, but for me, they're just too unwieldy. I prefer my music players to be as small and inconspicuous as possible. Audacious fits that part beautifully, but the lack of a library (intentional or not) was just a killer. Guess I'm just too picky for my own good ;)

The closest I've found so far to a media library plugin for Audacious is the methlab library. I've only just started playing with it, so I can't really say if it's any good yet, but it's worth a look, right?

Instructions here: [http://ubuntuforums.org/showthread.php?t=680736](http://ubuntuforums.org/showthread.php?t=680736) 

They seem to be pre-Gutsy, but they worked alright for me, other than one line - you'll need to use "svn checkout" instead of "svn co"

Methlab homepage is here: [http://methlab.thegraveyard.org/wiki](http://methlab.thegraveyard.org/wiki) 

Hope that helped!

The methlab part from that ubuntuforums link is still valid

---

