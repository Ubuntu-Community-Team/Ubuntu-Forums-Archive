---
title: "How to install backup computer"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by chrisKr on 2009-05-30
I would like to backup my system but i cant seem to be able to find hubackup.  Its not in System --> Administration and when i wrote, in Terminal, [COLOR=Magenta]sudo aptitude install hubackup[/COLOR] it cant locate the file.

I think i need to add a repository to be able to download it.  Does anybody know which repository has this little backup package? Or is there another way of backing up the computer?

---

### Post by blueridgedog on 2009-05-30
Let's start with a broader question:  What specifically do you want to backup and where do you want to back it up to?

---

### Post by bacardiandwatermelon on 2009-05-30
[https://wiki.ubuntu.com/HomeUserBackup#Code](https://wiki.ubuntu.com/HomeUserBackup#Code)

Oh but I found this.. They are Intrepid files which may still work?
[http://linuxappfinder.com/package/hubackup](http://linuxappfinder.com/package/hubackup)

---

### Post by chrisKr on 2009-05-30
In particular i need to backup my files, i.e. documents etc..  Also, if possible, i would like to be able to have a package similar to system restore in windows.  Is that possible?

---

### Post by bacardiandwatermelon on 2009-05-30
Scratch that, the backup portion of the intrepid deb works, however when you try and restore, nothing seams to happen...

---

### Post by SuperSonic4 on 2009-05-30
> **chrisKr said:**
> In particular i need to backup my files, i.e. documents etc..  Also, if possible, i would like to be able to have a package similar to system restore in windows.  Is that possible?

Backing up documents is simple enough - copy them to external storage and paste them back in should anything happen. Most of my documents and media are stored on a different physical drive to my OS installs.

[Luckybackup]("http://www.kde-apps.org/content/show.php/luckyBackup?content=94391") looks interesting although its deps are qt, rsync, openssh. Although I recall VLC uses qt so it may be on there already.

---

### Post by bacardiandwatermelon on 2009-05-30
Looks like a bug was reported ages ago and it was removed from the repos cause of the issues with it..
[https://bugs.launchpad.net/hubackup/+bug/64594](https://bugs.launchpad.net/hubackup/+bug/64594)

---

### Post by NHArticleTen on 2009-05-30
> **blueridgedog said:**
> Let's start with a broader question:  What specifically do you want to backup and where do you want to back it up to?

I second the question above.

I use Clonezilla regularly as I don't trust background applications implicitly.

as always, your mileage may vary...

---

### Post by blueridgedog on 2009-05-30
> **chrisKr said:**
> In particular i need to backup my files, i.e. documents etc..  Also, if possible, i would like to be able to have a package similar to system restore in windows.  Is that possible?

OK, so everything in your home directory or do you have a dedicated drive that you store files on?  Also, where do you want to put the files you backup?

As far as "system restore" goes, the closest thing I can offer is a good backup and the remastersys program.

It is available in the repistories with:

```
sudo apt-get install remastersys
```

You can read about it here:

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

You can use it to make a bootable DVD of your system with your data.  I keep a remastersys image of my system that I update once a month (but I am paranoid and also keep two spare copies of all my files via hot swap drives).

So, for a bare metal, gotta get it back restore, you have remastersys (if you run it and then burn the resulting iso to a DVD).

For everyday, you have as a previous poster suggested which is a simple copy/paste, or an rsync command which I will help you develop if you tell me more about your system (questions above as to special drive and don't forget the "where to put it" question).

---

