---
title: "build a streaming server"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by cazz on 2008-09-03
I wonder if that is any easy and quick to create a media streamserver in Ubuntu?

Like to create so I have some movie clip in a directory that I can easy get from any computer on the network.
I also want so people can scroll forward and backwards.

I going to add a apache server so I can create a list of file so when someone click on a link it open a mediaplayer (like windows media player, VLC or quicktime) and start to show the movie.

---

### Post by puppywhacker on 2008-09-03
Hi,

(edit: by reading your post again, I think you only want to add the movies to your apache directory and and you will be fine)

VLC is very nice to play around with streaming video. There are quiet a few methods, but they have excellent documentation. (not just the wiki)

[vlc easy streaming howto]("http://wiki.videolan.org/Documentation:Streaming_HowTo/Easy_Streaming")

For a simple demonstration I used these commandline settings.

on the sending side:
vlc /media/movie.mpeg --sout '#rtp{mux=ts,dst=192.168.1.2}' --ttl 2

on the receiving side:
vlc udp:@

---

