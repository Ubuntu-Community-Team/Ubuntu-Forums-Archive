---
title: "Newly updated Transmission (torrent client) launching multiple sessions"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-01-23
Just updated today to version 1.80 of transmission. New features are quite impressive but, whenever I click on a new torrent to download it launches a NEW transmission session. So, if I donwload 3 torrents I'll have 3 versions of transmission open. As you can imagine it's a little annoying! Any suggestions?

---

### Post by lovinglinux on 2010-01-23
Setup a folder to be watched and save the torrents to that folder instead of opening them with the application.

---

### Post by abhiroopb on 2010-01-23
Can i select a sepcific folder for torrents to be downloaded to? From Chrome I mean. See the thing is I use a script to download torrents, stuff like nightly builds, etc. These get downloaded to a specific folder which Transmission watches.

Now if I download a torrent from openbittorrent.com (as with ALL downloaded files on Chrome) the .torrent file goes into a Downloads folder. I have all this set up and I don't really want to change it. Clearly this is a bug and I'd like to see if there is a fix for it, rather than a workaround.

---

### Post by lovinglinux on 2010-01-23
> **abhiroopb said:**
> Now if I download a torrent from openbittorrent.com (as with ALL downloaded files on Chrome) the .torrent file goes into a Downloads folder. I have all this set up and I don't really want to change it. Clearly this is a bug and I'd like to see if there is a fix for it, rather than a workaround.

I don't know, I have Chrome, but it isn't working well here. But it should have an option to select the folder on per-file basis. 

BTW, you can't download any torrent from openbittorrent.com, since it doesn't host any torrents. It is a tracker, so it only tracks torrents uploaded somewhere else.

---

### Post by abhiroopb on 2010-01-23
I was just using it as an example.

How do i select folders on a per-file basis? Right now I have set to auto-open "files of this type" so all .torrent files automatically launch and that's when transmission opens up a new session.

---

### Post by lovinglinux on 2010-01-23
> **abhiroopb said:**
> I was just using it as an example.

How do i select folders on a per-file basis? Right now I have set to auto-open "files of this type" so all .torrent files automatically launch and that's when transmission opens up a new session.

Unset the auto-open "files of this type" and it should prompt for a location to save.

---

### Post by abhiroopb on 2010-01-23
Ah yes but I can't permanently set it to download to that location. And I hate having to select it each time!

---

### Post by lovinglinux on 2010-01-23
> **abhiroopb said:**
> Ah yes but I can't permanently set it to download to that location. And I hate having to select it each time!

I was going to suggest that, but apparently you didn't want to change the location of the Chrome download folder. At least that is what I understood from your previous posts.

---

### Post by abhiroopb on 2010-01-23
Yes that's kind of right. Basically, I don't like to fiddle with settings once I've clicked download. I'd like torrents to auto-magically go wherever and for transmission to also start up once the .torrent file is downloaded. Also, I don't really want a huge list of torrent files cluttering up my downloads folder. 

In addition everything else I download I want to go to my "Downloads" folder.

Anyway all I want to fix is the multiple opening of transmission. Like i said I really don't want to play around with anything else.

Thanks for the suggestions!

---

### Post by abhiroopb on 2010-01-23
Weird guess it was just a bug, error not happening any more :).

---

