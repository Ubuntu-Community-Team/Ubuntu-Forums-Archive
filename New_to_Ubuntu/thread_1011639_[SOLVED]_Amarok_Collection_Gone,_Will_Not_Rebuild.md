---
title: "[SOLVED] Amarok Collection Gone, Will Not Rebuild"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by jpoRS on 2008-12-15
Hey All,

Yesterday I added some music into the folder that Amarok watches, and nothing happened.  I waited for the little "scanning collection" progress bar, it showed up, but the music did not show up in my collection.  Bummer.  So I tinker for a while, try a bunch of tips I found around the web, in a moment of clarity I downloaded Exaile in hopes that would allow me to at least listen to music while I finished Amarok, but that wouldn't show my collection either.  Ah-ha!  So it would be a SQLite error, right?  Having always intended to upgrade at some point, so I decided to try my hand at MySQL.  Well that didn't work (for details see [HERE]("http://ubuntuforums.org/showthread.php?t=1010530").)

So after all of this, I go back to Amarok figuring I will at least be able to listen to what is already in my collection, right?  WRONG!  Something I did trying to set up MySQL must have wiped SQLite out.  Awesome!  So I go to rescan collection in Amarok, and the little progress bar goes from 0-100% in about thirty seconds (far to fast for my 60Gig music collection) and then Amarok just sits there, no collection.

The files are still there, they play fine in totem, so it appears to just be some sort of SQL problem?

I am running 8.10 (64bit) on a System76 Pangolin.  Any help would be greatly appreciated, it is finals week and I can't study without music!

Thanks,
jim

---

### Post by dwasifar on 2008-12-15
This has worked for me in the past:

1) Change Amarok's collection directory to a different path that does not contain any music files.
2) Do a rescan.
3) Change it back to point at the correct directory.
4) Rescan again.

That MAY work.  And it may not.  But it doesn't take long to try.

---

### Post by jpoRS on 2008-12-15
Thanks dwasifar, but that didn't do it.  In fact I just noticed that the "Apply" button never lit up when I was changing the collection path.  Is that significant?

jim

---

### Post by dwasifar on 2008-12-15
It seems the Apply button only activates on that page when you change the collection database type.  So no, I don't think that is significant.

This is rather more drastic, but you could try deleting (or renaming) the ~/.kde/share/apps/amarok directory.  That should cause Amarok to behave as a new installation the next time you start it up.  It should also take your previous database down with it.  Worth a shot.

---

### Post by jpoRS on 2008-12-15
Tried that already too.  Even went as far to fully remove (both through Synaptic and terminal) Amarok, then delete that .kde/share/apps/amarok, then reinstalling Amarok.  Still no luck.

---

### Post by sydbat on 2008-12-15
Which version are you running? Maybe installing an older (or newer, depending) version might help.

---

### Post by jpoRS on 2008-12-15
Of Amarok?  1.4.10 I think.  And (other than 2) that is the most up to date, right?  So where would I find an older one?  Or is there some way of getting Amarok2 to work without KDE already (I would prefer that)?

jim

---

### Post by sydbat on 2008-12-15
I *think* you should be able to install and run 2.0 on your Ubuntu box. If you are running 1.4.10 without any problems...

[http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

---

### Post by shredder12 on 2008-12-15
ya there is a way to make amarok work without kde you will find a gnome-do-plugin amarok package in synaptic..
i think this is how i am able to run amarok on gnome..
may be you should give it a try...
newaz.. have you checked whether rhythmbox is working fine or not..

---

### Post by jpoRS on 2008-12-15
Ok, so Amarok2 does work, but it is having the same problem persists- Amarok scans through the collection, and nothing came of it.

However I noticed that it already "knew" where my collection was, even though I deleted /kde/share/apps/amarok  Does Amarok keep config data somewhere else?

I installed gnome-do-plugins, but it doesn't seem to have done anything.  Also RhythmBox does "work" but it has always been buggy for me.  I can't change some tags, some music never shows up, and I just don't like it as much.  But that is a recurring problem rather than something (I think) related to my Amarok issue.

thanks 

jim

---

### Post by Elfy on 2008-12-15
I've been playing with amarok2 and like oyu had a few issues - but what I've just found out is that I have now got amarok2 files/data in /var/tmp, be differnet name for you, but I wonder if it's conflicting with the old collection 

/var/tmp/kdecache-kevin/kpc/amarok.data

Maybe try renaming the folder. I assume that when you say > Even went as far to fully remove you eman there are no residual configs.

In the past I've done as you and it has reinstalled and been a 'new' installation.

I haven't actually gone so far as removing my collection to see if the newer folder in /var gets seen, but I would try a rename of it.

---

### Post by jpoRS on 2008-12-15
Thanks Forest, that did it.  Both Amarok 2 and Amarok 1.4 work fine now, though I did have to reinstall mp3 support.

As an aside: I really don't like Amarok2.  When I first started using Amarok I was implressed by how intuitive it was and how much it could do.  This one doesn't give me the same feeling.  Anyway.

Thanks everyone!

im

---

### Post by bonfire89 on 2008-12-27
I was having the same problems. They started after upgrading to amarok2 and then downgrading after I found out that amarok2 isn't even completely finished and because I wasn't a fan of it in general.


I use a remote mysql server for my collection and I think my breakthrough was when I realized that the database was empty. I temporary switched to mysqlite, then switched to a local mysql database, and then switched it to my remote one. I built a sample collection and it worked. Right now I'm re building my full collection, if it doesn't work I'll post back.

I also re installed amarok and deleted directories and all that jazz, it doesn't seem to have had an effect, but, maybe it did.

---

### Post by afrodeity on 2010-12-23
how to clear the database on Amarok Version 2.3.2? Just a one liner please.

---

