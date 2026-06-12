---
title: "How would I setup an mp3 server?"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by nicholaspaul on 2007-02-01
On my wireless network I have an Ubuntu machine (Ubuntunes - PIII, 384Mb RAM, 40Gb + 10 Gb HDs) that holds my CD collection ripped as mp3s. About 2,500 in all. That machine is upstairs, in the living room. It quite happily plays mp3s all day, waiting for me to turn up the volume when i want to hear music!:guitar:  I often want to listen to music downstairs, as well, in the family room, where I have the TV, DVD player and stereo. 
I would like to setup another Ubuntu computer (let's call it #2) in the family room so that I can play mp3s from Ubuntunes, without downloading them first - preferably wirelessly.

How would I set it up so that Ubuntunes can stream to #2 without duplicating the mp3s? I would also like to be able to control #2 from a laptop, wirelessly, via ssh. 
How should I go about this? What kind of services would I need on #2? How much processing power/RAM would #2 need? Xubuntu sounds like a good idea. 

Any ideas or pointers would be greatly appreciated! Thanks!

---

### Post by kidders on 2007-02-01
Hi there,

Would DAAP be any use to you? I use mt-daapd to share my music. It advertises itself with mDNS, and streams over HTTP.

---

### Post by cstudent on 2007-02-01
I have all my mp3's on one Ubuntu machine running Dapper I use as a server. On my desktop, (running Edgy) I have the server's drive mounted using nfs. I use Banshee and I just pointed it to use the mp3 directory of my server as the main library folder. It plays my music just fine that way.

---

### Post by nicholaspaul on 2007-02-01
I'm not familiar with DAAP, but I can always Google. 

How exactly would I mount a drive using NFS? Should I also make changes in fstab on the 'served' machine?

---

### Post by nicholaspaul on 2007-02-01
I Googled DAAP and found this tutorial: 

[http://dotnet.org.za/matt/articles/48417.aspx](http://dotnet.org.za/matt/articles/48417.aspx)

My server, Ubuntunes, now appears in iTunes by default. I followed the instructions to the letter, and (for a change!) it worked perfectly!

Wow!

Ok, now I have to get it working from Ubuntu, instead of OSX so I can set up a new machine just for this.

---

### Post by btdown on 2007-02-01
I use Slimserver....They have a debian repository that has more up to date versions than Universe repository at:

[http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage)

More info on it here:
[http://wiki.slimdevices.com/index.cgi?SlimServer](http://wiki.slimdevices.com/index.cgi?SlimServer)

Basically it runs its own small webserver on port 9000 (port can be changed). So,  you point your browser to [http://yourserver:9000](http://yourserver:9000), and then point winamp (or any other streaming mp3 client) to [http://yourserver:9000/stream.mp3](http://yourserver:9000/stream.mp3)
you can now select songs/playlist/etc which will be streamed over your winamp session.

It's pretty slick and very customizable.

BT

Its by far the best remote streaming solution for your collection.

---

### Post by nicholaspaul on 2007-02-02
Woweez. I played a bit more with audio players and got Amarok to work very nicely! I just clicked on 'link to server' and that was it! Almost as easy as iTunes. 
Now my next question is, in order to play mp3 from OUTSIDE the LAN would I simply poke a hole in the router at port 3689, or is it more complicated than that? 
Obviously a little security would be nice (I have WEP for those nosey neighbours, which I know is not perfect, but it helps).

---

### Post by kidders on 2007-02-02
Glad to see you're having success. :-)

Exposing MP3s to the world might not be a good idea, given the amount of bandwidth a successful malicious user could eat up. Depending on various things, it might also be illegal.

Lots of good sharing solutions are posted here, but since you asked about port 3689 (DAAP's default port), it might be worth noting that mDNS (the protocol used to advertise the presence of the music server) won't function properly outside a LAN, so you might have connection difficulties client-side. DAAP itself is HTTP-based, though.

A safer music sharing solution would be a VPN, but it wouldn't be worth the trouble unless you found having one useful for other reasons too. If you really want to let the whole world see your music (rather than just another personal computer that happens not to be local), a VPN wouldn't help you though.

---

### Post by MockY on 2007-02-03
Try [Vibe Streamer]("http://www.vibestreamer.com/")

Its completely magnificent.

---

