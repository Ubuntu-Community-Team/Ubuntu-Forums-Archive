---
title: "Transmission/Deluge Bit Torrent"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Son of MaxVK on 2010-07-21
I just switched from Transmission bit torrent to Deluge to see if it was indeed faster, which it was but I have an issue with it. The torrent is already half way finished, I put the file that is being downloaded into the correct folder but it tell me the download is starting from scratch. 

Can I get it to recognise that the file is already half done?

---

### Post by colin.p on 2010-07-21
I have found that if I want to change to another program midway through, I have to download the torrent "starter" file first (not sure what you call it) and then have Deluge save to the folder that the partial torrent is saved to.
Then Deluge will see the partial torrent and after a "verifying" stage will continue to download from where Transmission left off.
If you use PB then you'll know what I mean.

---

### Post by Son of MaxVK on 2010-07-22
> **colin.p said:**
> I have found that if I want to change to another program midway through, I have to download the torrent "starter" file first (not sure what you call it) and then have Deluge save to the folder that the partial torrent is saved to.
Then Deluge will see the partial torrent and after a "verifying" stage will continue to download from where Transmission left off.
If you use PB then you'll know what I mean.

I'm afraid I don't know what you mean, could you explain in more detail please?

---

### Post by colin.p on 2010-07-22
I start a torrent (from Torrents R Us), called "Pioneer.One.720p.X264.torrent" in Transmission, for example, and have it saved to a folder called "torrents". I then decide I want to use Deluge, which I had set up to download to the same "torrents" folder. I would need to go back to Torrents R Us and click to download the torrent again. Firefox would ask what to do and where to put the file. I click to open with Deluge (in this case) and then Deluge would then start to download to the "torrents" folder. However, Deluge checks to see if that file is already there (Transmission does the same, so I think that it is a common trait with torrent programs).
It sees the file, then does a "verifying" stage and then it starts to download from where Transmission left off.
It is hard to explain without showing you, but it works. But then again, there is probably a much easier way to do it, but I like to figure things out for myself, which invariably is the hard way to do it.

---

