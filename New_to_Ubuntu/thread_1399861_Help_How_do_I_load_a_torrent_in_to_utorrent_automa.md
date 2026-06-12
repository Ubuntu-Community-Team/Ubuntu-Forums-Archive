---
title: "Help: How do I load a torrent in to utorrent automatically"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by verachion on 2010-02-06
First off I am sorry that I am asking so many questions but this one has me stumped, 

I have followed these steps from this web page [http://www.larryni.me.uk/blog/2007/02/24/associate-torrent-files-with-utorrent-running-under-wine/](http://www.larryni.me.uk/blog/2007/02/24/associate-torrent-files-with-utorrent-running-under-wine/) However, if I download a torrent and click on it, it automatically comes up with Unable to load "/tmp/*name of torrent; Path not found. 

Any ideas?

---

### Post by airtonix on 2010-02-06
1) wine programs expect to use standard windows Universal Naming Convention. which means c:\path\to\a\folder\and\a\file.torrent.
2) best way to give wine a driver letter for a particular folder in your linux filesystem is using winecfg : 
 a) open winecfg from the applications menu : applications > wine > configure wine
 b) change to the drives tab
 c) click autodetect first (it will most likely create a drive for your home folder
  mine looks like : 
```

 c: ../drive_c
 d: /home
 h: /home/airtonix
 z: /

```
 d) possibly also create a dedicated place in your home folder for torrents : 
Mine looks like 
```

/home
 /airtonix
  /torrents
   /downloads
   /completed
   /hash

```

+ Torrents in-progress are stored in 'downloads'
+ Torrent hash files are auto loaded from 'hash', while in progress i keep them in the downloads folder.
+ Completed torrents get moved to 'completed'

3) Open uTorrent.
 a) find the preferences for changing the location you auto load torrents from and change it to something like :  
```
h:\torrents\hash
```
4) use similar path concept for torrent download location, etc, etc.
5) when downloading .torrent hash files, save them in the ~/torrents/hash folder and utorrent should auto load them.

i say should because i don't use utorrent.... I find that transmission or deluge do a better job.

---

### Post by verachion on 2010-02-06
airtonix: **I have done step one and mine now looks the same, I have set it up so that utorrent, stores all torrents in download folder and that it automatically opens torrents from download and then deletes them. However I am still getting the same error.** 

**In regards to the below, I am a new to ubuntu, I have had this O/S for no more than a day or so how do I do all this? **     

> 
possibly also create a dedicated place in your home folder for torrents : 
Mine looks like 
```

/home
 /airtonix
  /torrents
   /downloads
   /completed
   /hash

```+ Torrents in-progress are stored in 'downloads'
+ Torrent hash files are auto loaded from 'hash', while in progress i keep them in the downloads folder.
+ Completed torrents get moved to 'completed'
[b] 

[B]This is what I have done so far: , 

1. Gone to wine configuration and completed step one. my wine looks like yours. 
2. I have pointed firefox to load utorrent with torrent files 
3. I have pointed utorrent to open torrent files to  [/B]
h:\torrents\hash[B] 

*However, I still getting the same error   **  *Unable to load "/tmp/*name of torrent; Path not found.[/B]**
[B]

Is there anyway you tell me how to set all this up in easy terms that I can learn from?[/B]

---

### Post by verachion on 2010-02-06
***UPDATE*** 

The torrent now goes into utorrent when its open, but it doesn't open utorrent.exe when its not open any ideas?

---

### Post by verachion on 2010-02-06
****BUMP**** 

I really need to know how to open utorrent.exe automatically when I point firefox to it. Ji just need to know how I direct the path?

---

### Post by verachion on 2010-02-07
***all sorted, it turned out that the script was pointing to c,program file and not wine c program file, thanks goes to a very friendly member of the wine irc.  ***

---

### Post by beegary on 2010-02-07
I was a happy uTorrent user under Windows, I have now switched to using Ubuntu exclusively (9.10), Deluge is a great replacement for uTorrent.
I think your torrent setup would be allot simpler with a Linux/MulitPlatform client.

---

### Post by nhasian on 2010-02-07
is there some feature you used in utorrent that deluge doesnt have?

---

### Post by verachion on 2010-02-07
> **nhasian said:**
> is there some feature you used in utorrent that deluge doesnt have?

The problem I had with deluge is that after I closed it, it would not open. 

>  
I was a happy uTorrent user under Windows, I have now switched to using Ubuntu exclusively (9.10), Deluge is a great replacement for uTorrent.
I think your torrent setup would be allot simpler with a Linux/MulitPlatform client.


I undertand that it would have been simpler to carry on a linux based torrent engine. But the thing is I like to learn new things and by taking the long way round I have learnt alot about shell scripts. Being a new user to ubuntu I am curious to know how all these things work. I suppose I ahve always taken windows for granted.

---

### Post by beegary on 2010-02-08
> **nhasian said:**
> is there some feature you used in utorrent that deluge doesnt have?
Not that I can think of, I dont think I ever got close to using half of uTorrents features. I think, in general Deluge seems to be giving me slightly better speeds. 


> **verachion said:**
> The problem I had with deluge is that after I closed it, it would not open. 
Sorry I cant really help you there, my Deluge install worked right out of the Ubuntu Software Centre. I realise you have gone over to Wine/uTorrent but next time it may be worth trying to run the application from terminal which will help when troubleshooting.


> **verachion said:**
> 
I undertand that it would have been simpler to carry on a linux based torrent engine. But the thing is I like to learn new things and by taking the long way round I have learnt alot about shell scripts. Being a new user to ubuntu I am curious to know how all these things work. I suppose I ahve always taken windows for granted.
Totally with you on that one, I cant believe I lasted on Windows so long. Learning something new every day, usually by breaking something then fixing it!

---

### Post by switch10 on 2010-02-08
> **beegary said:**
> I was a happy uTorrent user under Windows, I have now switched to using Ubuntu exclusively (9.10), Deluge is a great replacement for uTorrent.
I think your torrent setup would be allot simpler with a Linux/MulitPlatform client.

+1 here.  Deluge is the best.  a perfect clone of Utorrent

---

