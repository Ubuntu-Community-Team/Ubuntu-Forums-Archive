---
title: "Banshee errors"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-06-10
I am trying to add my music collection to Banshee, but it gets messed up for some reason. I used to use Banshee before I switched to Kubuntu so I could try KDE4, but it pissed me off. So I'm back with gnome, but Banshee rejects over 5000 of my songs. Heres some of the errors that are in the log file. Some say the file name others don't.
```
 [Warn  19:34:25.788] Caught an exception - Sqlite error
unrecognized token: "'Alternative Rock" (in `Mono.Data.Sqlite')
  at Mono.Data.Sqlite.Sqlite3.Prepare (System.String strSql, Mono.Data.Sqlite.SqliteStatement previous, System.String& strRemain) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.BuildNextCommand () [0x00000] 

[Error 20:55:21.798] /home/lewis/Music/Eminem/Encore/05 Like Toy Soldiers.mp3 - Sqlite error
unrecognized token: "'Hip-Hop"
[Warn  20:55:21.803] Caught an exception - Sqlite error
unrecognized token: "'Hip-Hop" (in `Mono.Data.Sqlite')
  at Mono.Data.Sqlite.Sqlite3.Prepare (System.String strSql, Mono.Data.Sqlite.SqliteStatement previous, System.String& strRemain) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.BuildNextCommand () [0x00000] 
```

---

### Post by directhex on 2009-06-11
> **Dapilot1 said:**
> I am trying to add my music collection to Banshee, but it gets messed up for some reason. I used to use Banshee before I switched to Kubuntu so I could try KDE4, but it pissed me off. So I'm back with gnome, but Banshee rejects over 5000 of my songs. Heres some of the errors that are in the log file. Some say the file name others don't.
```
 [Warn  19:34:25.788] Caught an exception - Sqlite error
unrecognized token: "'Alternative Rock" (in `Mono.Data.Sqlite')
  at Mono.Data.Sqlite.Sqlite3.Prepare (System.String strSql, Mono.Data.Sqlite.SqliteStatement previous, System.String& strRemain) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.BuildNextCommand () [0x00000] 

[Error 20:55:21.798] /home/lewis/Music/Eminem/Encore/05 Like Toy Soldiers.mp3 - Sqlite error
unrecognized token: "'Hip-Hop"
[Warn  20:55:21.803] Caught an exception - Sqlite error
unrecognized token: "'Hip-Hop" (in `Mono.Data.Sqlite')
  at Mono.Data.Sqlite.Sqlite3.Prepare (System.String strSql, Mono.Data.Sqlite.SqliteStatement previous, System.String& strRemain) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.BuildNextCommand () [0x00000] 
```

Can you file a bug upstream (or try talking it through with the developers on #banshee)? Bugs like this can only be fixed when they're observed in the wild, allowing developers to see what the actual issue is

---

### Post by BinaryMn on 2009-10-15
I had the same exact problem with multiple tracks. Looking for this problem with Google turns back some hits, but to my great displeasure, there is no solution.

Until now.

I used an extremely powerful freeware ID3 tag editor called Mp3tag ([http://www.mp3tag.de/en](http://www.mp3tag.de/en)) to fix certain tag fields. Unfortunately, there is no Linux build. However, it does install and work seamlessly with WINE. I'm not aware of a suitable replacement that works natively with Linux.

Irritatingly enough, when Banshee throws an unrecognized token error, it isn't telling you the ID3 tag field that is causing the error. It only gives you the text in the field. What I did is the following.

I went through and blanked the Album Artist and Composer (%band% and %composer% fields respectively) fields on all my tracks. I could have done this only on the tracks giving me problems, though.

Next, I still had certain songs throwing back unrecognized token errors. I went to each individual track (in Mp3tag) giving me problems, one at a time, right-clicked on the song, and left-clicked on "Extended Tags". In the window that popped up, it was only a matter of finding the tag field that matched the "unrecognized token" text, deleting it, and clicking OK.

Deleting the tag fields causing the problem is the quick and dirty way of fixing this. I'm not a programmer. I don't know why Banshee is having problems processing random ID3 tag fields. 

This problem doesn't seem to be in the upstream, least not correctly. There is something on Launchpad with the same problem, but it's focused around unicode problems. None of the ID3 tag fields that I had problems with had any unicode characters in it. Regardless, I'll try filing something this weekend.

---

### Post by Dapilot1 on 2009-11-16
Awww, but I like the extended tags that the MusicBrainz Picad Last.fm Plus plugin gives me.

---

### Post by dca on 2009-11-16
Sounds like the genre tags, I keep a WindowsXP in VMware @ the office and run songs through 'TagScanner':
 
[http://download.cnet.com/TagScanner/3000-2141_4-10056506.html](http://download.cnet.com/TagScanner/3000-2141_4-10056506.html)
 
...don't quote me but so far it handles all the music I have which spans MP3, WMA, & M4A

---

