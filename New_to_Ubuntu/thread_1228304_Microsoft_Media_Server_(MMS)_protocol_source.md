---
title: "Microsoft Media Server (MMS) protocol source"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-31
Hello,
I want to watch an online stream which uses mms protocol; is there anyway to watch it under Linux?
Thanks.

---

### Post by jacklinux on 2009-07-31
only thing i can suggest is maybe if you can install would be via WINE but as its a microsoft realease i wouldn't get my hopes up.

---

### Post by niteshifter on 2009-07-31
Hi,

Nah, you don't need wine for mms streams. VLC can handle them.

[VLC's wiki on receiving streams]("http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream"). Gives command line instructions. In the GUI, just use File -> Open.

[Wikepedia MMS article]("http://en.wikipedia.org/wiki/Microsoft_Media_Server").

---

### Post by Hoom@n on 2009-08-02
> **niteshifter said:**
> Hi,

Nah, you don't need wine for mms streams. VLC can handle them.

[VLC's wiki on receiving streams]("http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream"). Gives command line instructions. In the GUI, just use File -> Open.

[Wikepedia MMS article]("http://en.wikipedia.org/wiki/Microsoft_Media_Server").
Thanks. I installed VLC Media Player but, it streams only the first 10 seconds and then stops!(I just used GUI and didn't try commands)

---

### Post by hibliss on 2009-08-02
Mplayer can handle them. You can even make Mplayer default to open them in your browser.

Mplayer can handle NSV (Winamp) as well.

Just open a terminal, and type:

```
mplayer <stream address>
```

Post the stream address so we can test it if you can.

---

### Post by Hoom@n on 2009-08-02
> **hibliss said:**
> Mplayer can handle them. You can even make Mplayer default to open them in your browser.

Mplayer can handle NSV (Winamp) as well.

Just open a terminal, and type:

```
mplayer <stream address>
```

Post the stream address so we can test it if you can.
Thanks. "mplayer" was better! It streams for some seconds and stops, again plays and stops.
(My Internet connection is not fast enough to play that stream; VLC buffers once at first start so just works for some seconds, MPlayer buffers at start/each stop so it won't stop.)
You can try this: mms://213.80.127.1/C_7

---

### Post by hibliss on 2009-08-02
> **Hoom@n said:**
> Thanks. "mplayer" was better! It streams for some seconds and stops, again plays and stops.
(My Internet connection is not fast enough to play that stream; VLC buffers once at first start so just works for some seconds, MPlayer buffers at start/each stop so it won't stop.)
You can try this: mms://213.80.127.1/C_7

Right after it loads, press the spacebar, that will pause it and give it time to buffer. For a very slow connection, I recommend letting it buffer for at least a few minutes before you start watching, depending on how long you plan to watch.

You can also set the resolution and other parameters that the mplayer window opens with using custom commands.

For example, you can go fullscreen by pressing f.

Here is a full listing of Mplayer commands, it is a very powerful palyer -- [http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html]("http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html")

Oh, and that stream works great for me.

For streaming in Ubuntu, mplayer > VLC by a mile.

---

### Post by llamabr on 2009-08-02
Yes, wine is very rarely the correct solution.

Furthermore, rather than waiting for mplayer or vlc to buffer, with flash videos, mplayer will store the contents of the video in /tmp.  When it's completely received, you can just navigate to /tmp and play it there.  With flash, it saves it as /tmp/Flash75uthe or whatever.

i can't find an mms stream to verify this.  If you post yours, or another, we can take a look and make sure it's the same.

---

### Post by llamabr on 2009-08-02
Or, just look here:

[http://gmms.sourceforge.net/](http://gmms.sourceforge.net/)

---

### Post by hibliss on 2009-08-02
Post #6 has the stream address he is trying to get. If it is a constantly active stream, then downloading it could take some time ;)

Why use a third party app that is no longer being developed, and where the author says there are errors they are not fixing?

mplayer works fine.

---

### Post by llamabr on 2009-08-02
> **hibliss said:**
> Post #6 has the stream address he is trying to get. If it is a constantly active stream, then downloading it could take some time ;)

Why use a third party app that is no longer being developed, and where the author says there are errors they are not fixing?

mplayer works fine.

Beats me.  If mplayer works fine, I'd ignore that gmms.  Particularly if mplayer dloads the entire file to /tmp.

Frankly, it's none of my business what app the op uses, but he/she asked for solutions, and that's a possible one.

---

### Post by Hoom@n on 2009-08-03
> **hibliss said:**
> Right after it loads, press the spacebar, that will pause it and give it time to buffer. For a very slow connection, I recommend letting it buffer for at least a few minutes before you start watching, depending on how long you plan to watch.

You can also set the resolution and other parameters that the mplayer window opens with using custom commands.

For example, you can go fullscreen by pressing f.

Here is a full listing of Mplayer commands, it is a very powerful palyer -- [http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

Oh, and that stream works great for me.

For streaming in Ubuntu, mplayer > VLC by a mile.
Thanks! I'll try these tips next time I use MPlayer.
(Ahmadinejad banned Internet access with the speed of more than 128Kbps for home users! I'm using a 512Kbps ADSL and the only available faster speeds(768Kbps & 1Mbps) are more than 400$/month!)

---

### Post by Hoom@n on 2009-08-03
> **llamabr said:**
> Yes, wine is very rarely the correct solution.

Furthermore, rather than waiting for mplayer or vlc to buffer, with flash videos, mplayer will store the contents of the video in /tmp.  When it's completely received, you can just navigate to /tmp and play it there.  With flash, it saves it as /tmp/Flash75uthe or whatever.

i can't find an mms stream to verify this.  If you post yours, or another, we can take a look and make sure it's the same.
Really thanks for /tmp! I always looked for a way to save YouTube videos in Ubuntu; it's the way!

---

### Post by andrew.46 on 2009-08-03
Hi Hoom,

> **Hoom@n said:**
> Thanks. "mplayer" was better! It streams for some seconds and stops, again plays and stops

You can add a few options to make that a little better:

```
mplayer -cache 2048 -cache-min 80 mms://213.80.127.1/C_7
```

This played nicely on my system and I must say that music was quite catchy :-).

Andrew

---

