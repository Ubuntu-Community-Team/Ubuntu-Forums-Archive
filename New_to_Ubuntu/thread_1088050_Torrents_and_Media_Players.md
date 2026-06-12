---
title: "Torrents and Media Players"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-05
Hello, all. Not entirely sure if this is the right place for this or not, but I think it is. More of a general query than a problem though.

Now that I've finally got my internet working (:D) I've been looking for a good torrent client and media player, but am having trouble due to mainly my own preferences.

Firstly, the torrents - I'm using opera, which seems to come with its own bittorrent client, but this is exceedingly slow (though that could be the torrents in particular, I'm not quite sure) . It also defaults to this automatically, rather than just saving the torrent so I can start it with another program. If I cancel the torrent and try to open it manually with a bittorrent client, I can't get anywhere - the torrent loads as normal, but won't download - it just sticks at finding peers/bits and so on. Does anyone have any recommendations for a good one? I've tried a few from the repositories.

Next, media players. I've sorted out codecs alright, but I can't seem to get comfortable with any of them - I'm used to The KMplayer from windows, and its (very nice IMO) way of doing this, and can't seem to find this amongst the various other ones I've checked from the repositories - either they don't have very nice menus, don't seem to want to adjust screen/video size, etc - does anyone have any recommendations for a good one which is fairly similar, or does all the same sort of stuff?

Again, sorry if this is in the wrong place - I didn't see a general forum for this, though it's entirely possible I'm just blind.

---

### Post by mkvnmtr on 2009-03-05
I like Deluge but I don't use Opera to down load the torrents. If you must use Opera then you will have to get the path right in the client.

---

### Post by Tek-E on 2009-03-05
For torrent clients I use Utorrent. runs exceptionally well for me.
As for media players I would stand behind VLC Media Player.  You dont have to worry about downloading codecs because It already comes with many Codecs previously installed.


:popcorn:

---

### Post by Azhtabak on 2009-03-05
Hmm, after a brief look at that it seems to be fairly close to exactly what I'm looking for - however, is there any way to zoom incrementally (as in just a few % at a time, preferably by a hotkey) and to integrate the control-box-thing into the full screen mode? I mean where some have it as a bar at the bottom which dissapears.

---

### Post by lovinglinux on 2009-03-05
> **Azhtabak said:**
> Firstly, the torrents - I'm using opera, which seems to come with its own bittorrent client, but this is exceedingly slow (though that could be the torrents in particular, I'm not quite sure) .

I don't now about opera, but you could make a test downloading a torrent of the latest release of Ubuntu. They are usually very fast, so if you still get slow connections, then you probably need to forward the required port from your router to your machine and open the port in the firewall to accept connections. There are plenty of tutorials here and on the net about port forwarding.

> **Azhtabak said:**
> It also defaults to this automatically, rather than just saving the torrent so I can start it with another program.

Most torrent clients have an option to monitor a specific folder for torrent files. So if you can't change the option of which application will open a torrent from inside Opera preferences, then simply right click in the torrent link and save it in the folder being monitored by the torrent application. It will automatically add the torrent to the application list.

> **Azhtabak said:**
> Does anyone have any recommendations for a good one? I've tried a few from the repositories.

I recommend Deluge. It has most important torrent features, is easy to configure and has a nice interface.

> **Azhtabak said:**
> If I cancel the torrent and try to open it manually with a bittorrent client, I can't get anywhere - the torrent loads as normal, but won't download - it just sticks at finding peers/bits and so on.

Looks like you need to properly configure the torrent client.

> **Azhtabak said:**
> 
Next, media players. I've sorted out codecs alright, but I can't seem to get comfortable with any of them - I'm used to The KMplayer from windows, and its (very nice IMO) way of doing this, and can't seem to find this amongst the various other ones I've checked from the repositories - either they don't have very nice menus, don't seem to want to adjust screen/video size, etc - does anyone have any recommendations for a good one which is fairly similar, or does all the same sort of stuff?

VLC is the most feature rich, but I don't like it. You could try smplayer, which has a nice interface and a decent amount of configuration options.

Unfortunately, you won't find a player like KMPlayer or GOM Player, which are the best players out there for Windows in my opinion.

---

