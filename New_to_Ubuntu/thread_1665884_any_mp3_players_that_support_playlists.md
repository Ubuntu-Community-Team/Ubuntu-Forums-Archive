---
title: "any mp3 players that support playlists?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-12
hi again!

I'm currently searching for a linux compatible mp3 player that supports a wide variety of playback formats. (ogg, FLAC, etc.)

I'm aware that players such as the sansa clip+ can be used with linux operating systems, but as a "USB mass storage device", meaning that to add music you simply drag-and-drop.

I rely very heavily on playlists; the order of the songs is important. Is there a way to sync playlists with the clip (would installing rockbox do this?), or are there any mp3 players that are linux and playlist compatible? 

I'm currently using banshee as my default media player, if that makes a difference. 

Thanks in advance for any info. :D

---

### Post by Chronon on 2011-01-12
Most mp3 players support some sort of playlist.  Rockbox supports standard m3u playlists, so you can certainly install that and use computer-generated playlists (as long as the path on your player is a subpath of the path stored in the playlist).

Rockbox doesn't provide any capacity for syncing.  It is a firmware for mp3 players.  How you get playlists and other files to your player is up to you.  You can drag and drop with a file browser, use a desktop media player (like amarok) to transfer files from your library to your player, or any other method you find convenient.

---

### Post by maryalesia on 2011-01-12
> **Chronon said:**
> Most mp3 players support some sort of playlist.  Rockbox supports standard m3u playlists, so you can certainly install that and use computer-generated playlists (as long as the path on your player is a subpath of the path stored in the playlist).

... what on earth does that last part mean? Because it sounds daunting.

---

### Post by maryalesia on 2011-01-12
hokay so in banshee there is the option to export playlists as m3u ... but where do I export it TO?? (and after that, how do I get it on the device?)

I realize this would probably be easier if I actually had the device to try it on ... :(

---

### Post by Chronon on 2011-01-13
> **maryalesia said:**
> ... what on earth does that last part mean? Because it sounds daunting.

I just mean that the path to the file on the player has to match the ending part of the path listed in the m3u file.  For example, I have a file at 
[FONT="Courier New"]/home/username/Music/Tool/[1993] - Undertow/09 - Flood.ogg[/FONT].  If I make an m3u playlist containing this track then one of the lines of the file will contain this path.  

Rockbox should find it as long as the path to the file on the player matches the rightmost part of the path in the playlist.  For example, Rockbox should find and play any of the following, given the above path:
[FONT="Courier New"]/Music/Tool/[1993] - Undertow/09 - Flood.ogg
/Tool/[1993] - Undertow/09 - Flood.ogg
/[1993] - Undertow/09 - Flood.ogg
/09 - Flood.ogg[/FONT]

> hokay so in banshee there is the option to export playlists as m3u ... but where do I export it TO?? (and after that, how do I get it on the device?)
You can save it directly to the portable player if you like.  Or save it to any convenient location and transfer it to the player later.

---

### Post by Chronon on 2011-01-13
Rockbox is by no means your only option either.  SanDisk's firmware supports FLAC, Ogg Vorbis and playlists (.pls rather than .m3u, I believe).

---

### Post by -kg- on 2011-01-13
A lot of times (probably most of the time) it's easier to load the music on the mp3 player, then generate the playlist on the mp3 player.

Otherwise, most players will generate m3u playlists.  As Chronon said though, the path has to match.  It does no good to generate a playlist that points to an mp3 file on your hard drive...it has to point to the file on your mp3 player, which is why it's easier to generate the playlist on your mp3 player.

I have a Sansa View, and though I haven't as of yet, I intend to make some playlists for various purposes.  968 songs is quite a few, and I'd like playlists for various purposes.  Rather than jump through all those hoops, I'll just create them using the Sansa and be done with it.

---

### Post by Chronon on 2011-01-13
> It does no good to generate a playlist that points to an mp3 file on your hard drive...it has to point to the file on your mp3 player, which is why it's easier to generate the playlist on your mp3 player.
That's generally true, though there's the exception to this that I mentioned if you use Rockbox.

---

### Post by -kg- on 2011-01-13
Guess I didn't read closely enough...my Sansa View doesn't play .ogg files, and definitely uses m3u playlists.  As matter of fact, everything I've read (and I've done extensive research) says that playlists are much better and easier to create on (my) Sansa View.  Idiosyncrasies of my player...I'm not extremely familiar with others.

Still, seems easier to create playlists on the mp3 player itself, no matter what kind it is.  As you say...

*"...generally true..."*  :D

---

### Post by Chronon on 2011-01-13
I do create most of my playlists on the player too, but some users have a lot of pre-existing playlists that were generated using their main library.  Rockbox at least has some facility for dealing with partially matching paths.

It's odd that the View doesn't support Ogg.  I have an e280 and a Clip and both support Ogg.  I believe the Clip also supports FLAC but I haven't checked this as I almost never boot SanDisk's firmware.

@maryalesia Here's a useful page:
[http://wiki.xiph.org/index.php/PortablePlayers](http://wiki.xiph.org/index.php/PortablePlayers)

---

### Post by maryalesia on 2011-01-13
> **Chronon said:**
> 
You can save it directly to the portable player if you like.  Or save it to any convenient location and transfer it to the player later.

if I do this without rockbox installed, will it work? I find this all very confusing. I dont think the clip supports playlist creation in the player.:confused:

---

### Post by maryalesia on 2011-01-13
I guess my main issue is that I don't use multiple small playlists but one large one that has all my music but in a specific order, and it evolves as I get new music in my library.

---

### Post by maryalesia on 2011-01-13
I marked this thread as solved because I've bought the clip, and in player playlist creation is supported. :D

---

### Post by Chronon on 2011-01-14
maryalesia: most portable audio players have some method of creating playlists.   

If you want to see more of what Rockbox does you can find out more over at [http://www.rockbox.org](http://www.rockbox.org)

In the meantime, I hope you enjoy your new Clip!  :guitar:

---

