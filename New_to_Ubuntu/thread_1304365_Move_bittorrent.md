---
title: "Move bittorrent"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-29
Dear Forum,

I've just totalled my laptop so I don't have network access and am looking to move my halfcompleted bit torrents to my desktop.

I don't have the .torrent files anymore since I deleted them on import into transmission bit torrent.

Is there a way to copy all the data, including the half-completed downloads from one machine to another?

The old machine is running karmic desktop 32 and the one is running karmic desktop 64bit.


Richard

---

### Post by SuperSonic4 on 2009-10-29
Standard cut and paste job should work, just ensure you point transmission to the directory with the partial downloads. You may need to get the .torrent files to initiate it though

---

### Post by cipicip on 2009-10-29
And the torrents you find them in the transmission's config folder which should be something like: $HOME/.*config*/*transmission*

Alternatively you could do a search in your home folder:

```
find ~/.config -name "*.torrent"
```and see what it returns.

---

### Post by lovinglinux on 2009-10-29
Check the torrent hash info in Transmission. I don't remember where it is, but should be in the torrent details. 

Search the .torrent files at torrentz.com using the hash number (in red) like this:

```

http://www.torrentz.com/**[COLOR="Red"]60d5d82328b4547511fdeac9bf4d0112daa0ce00[/COLOR]**
```

Open each .torrent file you can find with the new client. It should re-check if the downloaded files are present and continue the download where it stoped.

---

### Post by RichardCL on 2009-10-30
> **cipicip said:**
> And the torrents you find them in the transmission's config folder which should be something like: $HOME/.*config*/*transmission*


Many thanks, I moved the torrents and the whole directory to the new computer. Everything then worked fine.

---

