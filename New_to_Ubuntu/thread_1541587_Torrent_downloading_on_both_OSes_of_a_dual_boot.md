---
title: "Torrent downloading on both OSes of a dual boot"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by Tejus on 2010-07-29
Hi!

I have a dual boot with Win7 and Lucid. I use uTorrent on Win7 and Transmission on Lucid. I want to synchronise the clients so that I can download from whichever OS i'm using. 

Similar to [this]("http://ubuntuforums.org/showthread.php?t=501438") (Old post), except I cannot bear using anything other than uTorrent on Windows! All the other options are too bloated for me.

In theory I should just load the .torrent file on both clients, set both to download at the same location, and just rechek/verify the files each time I switch OSes.

But sometimes I get an error in uTorrent saying "Elements missing from job..." which doesn't go away even if i force a re check. Only option will be to download that particular torrent in Transmission only, or to delete the file and re download in uTorrent only. So clearly there is something more to it.

If anyone has dealt with this issue of torrenting on a dual boot please hand me some tips.

Thanks!

---

### Post by ankspo71 on 2010-07-29
Hi,
If I remember correctly, uTorrent runs well in wine, so you can have identical torrent clients in both Ubuntu and Windows. I don't know for sure if this will help or not, but it would be the thing I would try first.

ratings for uTorrent in wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

Here are instructions on how to install and use wine
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine) (better instructions)
With wine you can install your uTorrent.exe setup file in Ubuntu

Another option is to try to find a cross platform torrent client that runs in both Windows and Linux. Azureus/Vuze is one, but it requires Java.

Hope this helps.

---

### Post by Tejus on 2010-07-29
Hey that sounds like a good option!

I'm figuring out how to install and use Wine right now...I'll get back after trying uTorrent on it.

Thanks a lot ! :)

---

### Post by lovinglinux on 2010-07-29
Keep in mind there is an uTorrent version for Linux being developed and it should be available later this year.

I would recommend [qBitorrent]("http://qbittorrent.sourceforge.net/"). It is cross-platform, looks similar to uTorrent and is the fastest torrent client I ever used. I also like Deluge and Ktorrrent, but qBitTorrent is what I use know.

---

### Post by synapsys on 2010-07-29
I have used uTorrent on Vista and Wine (Ubuntu  9.04) simultaneously. It was a real pain re-checking files every time (especially with large files that were almost complete), other than that it worked fine. I kept the directories on the Vista partition and pointed both uTorrents there. 

It eventually became too painful to re-check every time, so I ended up just using deluge on Ubuntu and letting it run all night long. It made sense for me to do it this way because the only reason I use Windows is for games and when torrents are hogging all the bandwidth, its real hard to play games.

---

### Post by Tejus on 2010-07-29
> **synapsys said:**
> It was a real pain re-checking files every time (especially with large files that were almost complete), other than that it worked fine. 

I found a few blogs that suggested making a symbolic link to the %appdata%\uTorrent\ (Windows version of uTorrent) at the appropriate location for the Wine version of uTorrent. Can I safely use this setup without rechecking everytime?

---

### Post by Tejus on 2010-07-31
All right....this is what worked for me:[INDENT] 1. Installing wine like [ankspo71]("http://ubuntuforums.org/member.php?u=734190") said, and configuring all the necessary drives that uTorrent uses so that they have the same drive letters as in windows.

[/INDENT][INDENT] 2.a)Creating a symbolic link in the wine's version of "C:\Program Files\uTorrent" pointing to the actual Windows' "C:\Program Files\uTorrent\uTorrent.exe"
[/INDENT][INDENT] b)and also a link in wine's "C:\Users\username\Application Data\uTorrent" pointing to Windows' %appdata%\uTorrent.

[/INDENT][INDENT]3. Making a Launcher on the Ubuntu desktop that launches uTorrent.exe with wine along with the /noinstall parameter:
[/INDENT][INDENT]wine "insert utorrent.exe location here" /noinstall
[/INDENT][INDENT] For me it is:
[/INDENT][INDENT] wine /home/tejus/.wine/drive_c/Program\ Files/uTorrent/uTorrent.exe /noinstall
[/INDENT]I do not know if i can use it without the /noinstall parameter. I'm too lazy to test it out right now...anyway everything is working fine :p. I am able to resume downloads without rechecking as all my user data including resume.dat are the same. But I hope that linux version comes out...then I could eliminate wine from the setup I guess.

Note that I have fstab configured to mount my windows installation  partition on startup, so that the Program Files and Application Data  folders are accessible from start.

Thanks everyone! :)

---

