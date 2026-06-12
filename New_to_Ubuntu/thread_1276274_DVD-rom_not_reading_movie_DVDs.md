---
title: "DVD-rom not reading movie DVDs"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by daimyo505 on 2009-09-26
Hello I am having problems with my DVD-rom reading movie DVDs. I am able to read CDs, and blank DVDs, but not movie DVDs. 

I have all my sources checked (main, restricted, multiverse, universe). I double checked that I have libdvdcss2 installed. Ubuntu replies that I have the most recent version.

I then saw this bug and don't know if it is still around:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/27316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/27316)

I do have a Plextor DVD-RW drive, and following the above link put music CD into the drive first. Then placed a movie DVD into the drive. The drive was then able to read the name of the DVD but not able to play it in either Mplayer or VLC player.

I also checked my fstab and saw this:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I'm not a linux expert but it looks like my DVD is listed as a CD-ROM.

Can anyone help me? :confused:

Thanks in advance.

---

### Post by nmccrina on 2009-09-26
I long ago gave up trying to play movies in Linux. I know there are people around who say they got it to work, but I've never had any luck. It sucks.

On the other hand, I've got a lot more reading done lately...:-k

---

### Post by halitech on 2009-09-26
are the movie cds you are trying to read commercial dvds? (ie. store bought) Have you tried a data dvd that you burned yourself?

---

### Post by Ms_Angel_D on 2009-09-26
I'm pretty sure (not positive) that it's always listed as cdrom I'm thinking that's just the name of the mount folder.

Did you install the required codecs, to play dvd's?

[http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg34t2.htm)

I just did what that guide said but On jaunty the commands are a bit different

You need to install libdvdread4

```
sudo apt-get install libdvdread4
```

then in the terminal run this command

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by oboedad55 on 2009-09-26
> **daimyo505 said:**
> Hello I am having problems with my DVD-rom reading movie DVDs. I am able to read CDs, and blank DVDs, but not movie DVDs. 

I have all my sources checked (main, restricted, multiverse, universe). I double checked that I have libdvdcss2 installed. Ubuntu replies that I have the most recent version.

I then saw this bug and don't know if it is still around:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/27316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/27316)

I do have a Plextor DVD-RW drive, and following the above link put music CD into the drive first. Then placed a movie DVD into the drive. The drive was then able to read the name of the DVD but not able to play it in either Mplayer or VLC player.

I also checked my fstab and saw this:
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I'm not a linux expert but it looks like my DVD is listed as a CD-ROM.

Can anyone help me? :confused:

Thanks in advance.

Install VLC, that's the best known player. I can never get movie player to play DVDs, but VLC works fine for me.

---

### Post by halitech on 2009-09-26
> **daimyo505 said:**
> I do have a Plextor DVD-RW drive, and following the above link put music CD into the drive first. Then placed a movie DVD into the drive. The drive was then able to read the name of the DVD but not able to play it in either Mplayer or VLC player.

> **oboedad55 said:**
> Install VLC, that's the best known player. I can never get movie player to play DVDs, but VLC works fine for me.

as the OP has stated, they have tried VLC and has the same issue there as in mplayer (which has never worked for me)

---

### Post by daimyo505 on 2009-09-26
> **halitech said:**
> are the movie cds you are trying to read commercial dvds? (ie. store bought) Have you tried a data dvd that you burned yourself?

I've tried both commercial and burned but no luck.

I have tried both VLC and Mplayer to no luck.

The DVD-player used to work when I was using with Kubuntu. I then switched to Ubuntu and haven't watched a movie since. :(

---

### Post by halitech on 2009-09-26
what about a cd? can you open a data cd?

---

### Post by anewguy on 2009-09-26
As Ms_Angel_D stated, you will probably need those 2 packages installed to be able to read and decode commercial DVDs.  In additional, be sure you have all of the gstreamer plugins (good, bad and ugly I believe they are called).  If after all of that you still have problems, post back and we'll go from there.

Dave :)

---

### Post by halitech on 2009-09-26
> **anewguy said:**
> As Ms_Angel_D stated, you will probably need those 2 packages installed to be able to read and decode commercial DVDs.  In additional, be sure you have all of the gstreamer plugins (good, bad and ugly I believe they are called).  If after all of that you still have problems, post back and we'll go from there.

Dave :)

if they can't read a burned data dvd then it has nothing to do with codecs of any sort.

---

### Post by anewguy on 2009-09-26
> **halitech said:**
> if they can't read a burned data dvd then it has nothing to do with codecs of any sort.

Ah, but the op only stated they tried a burned DVD - didn't say it was data.  If it's just a data DVD and if they burned it on the drive but now can't read it, that can be another problem.  Burning a DVD either as a movie or as data, depending on the drive, can be much like the old days of cd-rw's, etc. - it can be an internal problem with the drive, it could be a media problem, etc..  I've also had this problem with DVD-RW's.

If they installed ALL of the codecs, etc., and still can't play a commercial DVD, then we really do need to look elsewhere.  I wanted to be sure all of those bases were covered first, since the op didn't state if all of that was done (only the css lib).

Hopefully the op will let us know just what all has been installed, then we can go from there.

(Not arguing with you at all, just trying to be sure all the bases are covered :)  ).

Dave :)

EDIT:  Such things as the desktop eye candy special effects can have a real impact on trying to play a DVD as well.  Sometimes it is best to turn those off while debugging an issue such as this.

---

### Post by halitech on 2009-09-26
> **anewguy said:**
> Ah, but the op only stated they tried a burned DVD - didn't say it was data.  If it's just a data DVD and if they burned it on the drive but now can't read it, that can be another problem.  Burning a DVD either as a movie or as data, depending on the drive, can be much like the old days of cd-rw's, etc. - it can be an internal problem with the drive, it could be a media problem, etc..  I've also had this problem with DVD-RW's.

If they installed ALL of the codecs, etc., and still can't play a commercial DVD, then we really do need to look elsewhere.  I wanted to be sure all of those bases were covered first, since the op didn't state if all of that was done (only the css lib).

Hopefully the op will let us know just what all has been installed, then we can go from there.

(Not arguing with you at all, just trying to be sure all the bases are covered :)  ).

Dave :)

that was the reason why I specifically asked about opening a data dvd, to eliminate it being a codec issue. I may have been mistaken by their answer that they couldn't open a data dvd (guess we will have to wait to hear from them on that :) ) as they just said no to a burned dvd. That's also why I asked about a data cd to see if that works. I think the way they stated it, is that this is simply a dvd-rom, not a dvd burner but that they have a plextor (I think) burner in another machine.

---

### Post by anewguy on 2009-09-27
That would make a difference - we'll just have to wait in see I guess.  Hopefully we can all find at least an answer (maybe not a "solution" as the op might think, but at least an answer).

Take care - I'll check back later.

Dave :)

---

### Post by theozzlives on 2009-09-27
I'm suspecting the drive, I had an HP drive that went bad it would read CDs but not DVDs. Eventually it just quit reading, burning, etc. They don't last forever.

---

### Post by halitech on 2009-09-27
> **anewguy said:**
> That would make a difference - we'll just have to wait in see I guess.  Hopefully we can all find at least an answer (maybe not a "solution" as the op might think, but at least an answer).

Take care - I'll check back later.

Dave :)

what's the difference between an answer and a solution? An answer is what they want to hear, a solution is what they don't want to hear ;)

> **theozzlives said:**
> I'm suspecting the drive, I had an HP drive that went bad it would read CDs but not DVDs. Eventually it just quit reading, burning, etc. They don't last forever.

I'm leaning towards it being the drive as well (how long since they sold just dvd-roms anyway?)

---

### Post by anewguy on 2009-09-27
> **theozzlives said:**
> I'm suspecting the drive, I had an HP drive that went bad it would read CDs but not DVDs. Eventually it just quit reading, burning, etc. They don't last forever.

I've seen drives do that as well - usually a good hint is to just listen to the drive when the DVD is inserted - does it spin up normally or is it constantly restarting and varying the speed, etc..  

Dave :)

---

### Post by anewguy on 2009-09-27
> **halitech said:**
> what's the difference between an answer and a solution? An answer is what they want to hear, a solution is what they don't want to hear ;)

I love that!  Back in the days when I was a systems programmer and systems admin on large iron I wish I had known of that term then!

Dave :)

---

### Post by halitech on 2009-09-27
> **anewguy said:**
> I love that!  Back in the days when I was a systems programmer and systems admin on large iron I wish I had known of that term then!

Dave :)

learned that from a supervisor back years ago when I was doing tech support for an ISP. People don't usually like to hear what they aren't expecting or wanting to hear.

---

### Post by mc4man on 2009-09-27
> 
I then saw this bug and don't know if it is still around
I somewhat doubt it is still an issue, was till around gutsy with certain plextor drives.
 
(actually had that same issue with a plextor 708a or 712a, was the cause of my very first thread/post here. Stumbled upon the solution shortly afterwards by putting an audio cd in ect., ect.

Considering this is a new drive then **after  getting it to recognize the dvd**
> The drive was then able to read the name of the DVD

run this and see what it reports
```
sudo lshw -C disk
```

Also then start vlc with this and ck. the output when trying to play the disk ( media - > open disc
```
vlc -vv
```

---

