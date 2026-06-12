---
title: "Juke Box"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Greydog on 2009-08-25
Hi all,

I'm looking for a Juke Box program that will allow guests at a party to select a song from my data base and put in a queue to be played in it's turn.

I have looked around but, I'm not real sure how to phrase a search to find a program to do this.

Any help is great. Thanks.

Greydog

---

### Post by MrWES on 2009-08-25
> **Greydog said:**
> Hi all,

I'm looking for a Juke Box program that will allow guests at a party to select a song from my data base and put in a queue to be played in it's turn.

I have looked around but, I'm not real sure how to phrase a search to find a program to do this.

Any help is great. Thanks.

Greydog

Why not use the default music player, Rhythmbox? I made a playlist called 'Jukebox', and from there your guests can scroll through your library and when they find a track they like; just right click on it and add it to the 'Jukebox' playlist. Or just click add to play queue.

Bill

---

### Post by Greydog on 2009-08-25
Thanks Bill,

I didn't realise that you could do that. I guess I should look deeper into Rythmbox. 

This is a new project for me. I want to set up a music server and have a wireless laptop for a "guest" interface so that anyone can listen to what they want.

Eventually, I'd like to have a graphic interface with a real "Juke Box" look and feel to it...........someday.

Thanks again,

Greydog

---

### Post by MrWES on 2009-08-26
> **Greydog said:**
> Thanks Bill,

I didn't realise that you could do that. I guess I should look deeper into Rythmbox. 

This is a new project for me. I want to set up a music server and have a wireless laptop for a "guest" interface so that anyone can listen to what they want.

Eventually, I'd like to have a graphic interface with a real "Juke Box" look and feel to it...........someday.

Thanks again,

Greydog

Rythymbox also supports mt-daap shares - basically a music server. I run one from my server, but will also run on the deskptop version. Rythmbox has a built in plugin for DAAP shares, and iTunes will also pick it up too. It's in the repositories:
```
sudo apt-get install mt-daapd
```
from a terminal window. If you need configuring it let me know, it's fairly easy.

DAAP share is now called firefly media server and here is their web site:
[http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")

Bill

---

### Post by Greydog on 2009-08-26
Thanks again, Bill,

I am going to work on my project again tonight. I'll let you know how it goes.

Greydog

---

