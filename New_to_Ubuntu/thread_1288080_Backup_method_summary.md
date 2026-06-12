---
title: "Backup method summary"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by BobJam on 2009-10-10
Have been struggling with methods to make backups, as you can see in these threads:

[http://ubuntuforums.org/showthread.php?t=1278805](http://ubuntuforums.org/showthread.php?t=1278805)

[http://ubuntuforums.org/showthread.php?t=1273593](http://ubuntuforums.org/showthread.php?t=1273593)

[http://ubuntuforums.org/showthread.php?t=1244282](http://ubuntuforums.org/showthread.php?t=1244282)

[http://ubuntuforums.org/showthread.php?t=1242128](http://ubuntuforums.org/showthread.php?t=1242128)

[http://ubuntuforums.org/showthread.php?t=1231898](http://ubuntuforums.org/showthread.php?t=1231898)

Have finally come to a conclusion:  The CLI tar method in Heliode's 2005 post ( [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) ) turned out to be the easiest and most workable for me.  Granted, that thread is old . . . and as one poster pointed out in that thread, there have since been refinements in GUI backup programs that, in that poster's opinion, pretty much relegated Heliode's tar method to the dust bin.

But I have tried and/or looked at a lot of the GUI backup programs, from Partimage to Clonezilla to Mondorescue to Grsync to SBackup to . . . etc. (the number of these things makes the head spin), and they were either totally confusing and/or just flat out didn't work.  Some of that may be my own shortcoming, so I can't really say that they don't work.  But they didn't for me.

I also tried some CLI stuff like FSArchiver.   Same result . . . not for me.

As an example of a GUI (well . . . "semi-GUI") program I tried, I had trouble with Partimage . . . one of the most popular ones out there.  I read the psychocats tutorial and the Partimage page tutorial, but I just couldn't get it to work.  In that regard, mapes12 did a nice "How To" on it ( [http://ubuntuforums.org/showpost.php?p=7800125&postcount=11](http://ubuntuforums.org/showpost.php?p=7800125&postcount=11) ), and had I read that instead of the ones I did read, I might have gotten it to work.  Mapes' tutorial, to me anyway, was much better than the psychocats tutorial.

Also earthpigg, BTW, did a good explanation of dot files in the home directory, so I have learned a lot along the way.

But for a noob like me to finally settle on a command line method is saying something.  Most of us noobs, myself included, are pretty intimidated by command line stuff, and naturally gravitate to GUI's at first.

The beauty of Heliode's method is that there is basically a single line, the tar command, and that's it.  Plus, Heliode gives the precise command in the post.

I tried it, and within 5 minutes, the command had executed completely, and I had a "backup.tgz" file in my root directory.  Closest thing to a single point and click backup.

I'm not sure it will do incrementals (haven't read through all 96 pages of Heliode's thread, but I think there may be a script for this, or another command line).

Bottom line, though, for me this CLI method turned out to be the most workable.  Had I not gotten so frustrated with Partimage though, I may never have tried it.

Thoughts?

P.S. Have some questions on some stuff related to these other programs, but I'll start another thread on that to keep this post from getting longer than it already is.

---

