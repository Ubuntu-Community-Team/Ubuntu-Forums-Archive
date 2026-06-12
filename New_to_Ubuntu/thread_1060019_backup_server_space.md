---
title: "backup server space"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Erom on 2009-02-04
Hey all-

Just got started and honestly I love it so far - I prefer OSX to windows but hate that nothing's customisable in OSX (and the lack of a taskbar! The dock is not sufficient!) so Ubuntu is looking flipping sweet so far.

Anyway, I've got most of my must-have work programs handled (Eagle, Eclipse, Open Office, AutoCAD through Wine) but I'm hung up on one last killer app - Mozy.

I've got to have a backup solution, folks. I know there are plenty of GUI options for backup programs (and honestly I'm willing to work from the command line if I must) but none of them that I've seen come with server space like Mozy does. I know there is a lot of reservation about using backup servers you don't control around here, but tinfoil hats aside I've used Mozy for a while and trust the company.

Is there any way to swing this through Wine or something, or a recommendation for another provider?

Thanks,
Erom

---

### Post by binbash on 2009-02-04
[http://www.getdropbox.com/](http://www.getdropbox.com/)

works very well at ubuntu

PS : I don't know if you are looking for this since i never heard Mozy.

---

### Post by 7mkgw7q on 2009-02-04
I'm not sure if this is exactly what you are looking for, but I did find the page below.

[http://jeremy.zawodny.com/blog/archives/007641.html](http://jeremy.zawodny.com/blog/archives/007641.html)

Let me know if that is in the ballpark of what you wanted.

---

### Post by Erom on 2009-02-04
Sort of, but those all use Amazon S3, which is pretty pricy compared to Mozy (which cost a whopping 0 for the 2 gig version).

It's not really the backup program that I need - it's the free, secure server space.

If I have too, I can pipe everything from my ubuntu machine to one of my windows/mac boxes but... that seems like failure, doesn't it? Plus it would be a hassle when I'm away from my home network.

---

### Post by cwill747 on 2009-02-04
you can use a program like TimeVault to backup your files, and RSync to upload these to a mobile server. More information at:
[http://www.linux.com/feature/150600](http://www.linux.com/feature/150600)

---

### Post by Erom on 2009-02-04
Those are both good answers to the *how* question, but what I'm really asking is *where*.

E: Dropbox seems like a not-half-bad solution, if a little weaker security wise. Thanks binbash.

Anyone else got any other thoughts.

---

### Post by jwooton on 2009-06-30
Here is a simple service i've started experimenting with. Pretty plain and simple...nothing fancy. I only have about 9 people using it so far. If you want to give it a try, just email me at the address on the site. It's cheap and offers the protocols you're looking for.

[http://www.datastorageunit.com]("http://www.datastorageunit.com")

---

### Post by MrWES on 2009-06-30
> **Erom said:**
> Hey all-

Just got started and honestly I love it so far - I prefer OSX to windows but hate that nothing's customisable in OSX (and the lack of a taskbar! The dock is not sufficient!) so Ubuntu is looking flipping sweet so far.

Anyway, I've got most of my must-have work programs handled (Eagle, Eclipse, Open Office, AutoCAD through Wine) but I'm hung up on one last killer app - Mozy.

I've got to have a backup solution, folks. I know there are plenty of GUI options for backup programs (and honestly I'm willing to work from the command line if I must) but none of them that I've seen come with server space like Mozy does. I know there is a lot of reservation about using backup servers you don't control around here, but tinfoil hats aside I've used Mozy for a while and trust the company.

Is there any way to swing this through Wine or something, or a recommendation for another provider?

Thanks,
Erom

If you're willing to use command line, rsync via a crontab entry is the way to go.
```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av --delete --progress  /media/external/Documents /data/backup

```

That's my crontab for my server backup using rsync. It runs every Sunday at 3:30am. You can read up on it here:
[https://help.ubuntu.com/community/rsync]("https://help.ubuntu.com/community/rsync")

Can't get much easier.

Bill

---

