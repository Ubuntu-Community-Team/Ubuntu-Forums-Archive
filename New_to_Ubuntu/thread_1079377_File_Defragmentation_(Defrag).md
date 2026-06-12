---
title: "File Defragmentation (Defrag)"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by BruisedQuasar07 on 2009-02-24
It is my understanding that an advantage of using Linux (as opposed to Micro-softhead Windows) is that Linux does not fragment files on the 
hard drive. I wonder about that one. I have have Ubuntu on my main PC and Xubuntu on a laptop for 2 years now. I think both computers have slowed down since the first few months. 

I wonder if Linux fragments files much more slowly than Windows but does frag over time. Am I correct? I ran across a utility last week that claims to defrag Linux distros. What is the skinny on this subject? Does she or doesn't she?

--Bruised  ):P

---

### Post by sydbat on 2009-02-24
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

Also - [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by gjoellee on 2009-02-24
Ext4 gives online defrag

---

### Post by Kellemora on 2009-02-24
Hi BQ

NTFS is like a string of pearls, every addition and every change gets stuck to the end of the string.  And each time you edit a file, only the edited part gets stuck at the end of the string.  Edit 30 times and the read heads have to look in 30 places for the whole file.

EXT3 is more like pigeonholes in the wall.  You add a file it gets stuck in a pigeonhole far away from the last filled pigeonhole.  When you edit the file it gets stuck back into the same pigeonhole.

What appears as fragmentation is when a file is larger than a pigeonhole, then it gets placed in two adjoining pigeonholes, but still as a contiguous file.
The only time you have true fragmentation of the files is when the hard drive is so full that there are no sequential pigeonholes left.

TTUL
Gary

---

### Post by BruisedQuasar07 on 2009-02-25
Thank you for the replies. The perceived slow down I mentioned could be just that - perceived, & it was two years before I thought there was some slow down. It is nothing like a month of regular Windows use accumulates. I ignored it until I saw an online ad for a defrag utility for Linux. The ad claimed Linux users do need a defrag utility.

--Bruised

---

### Post by TomB19 on 2009-02-25
There's no need to defrag Linux but then there's no need to defrag Windows drives, either.

Even back in the old FAT days, fragmentation wasn't much of an issue.  I used to defrag my drive once a week until I did some benchmarking.  The difference in speed from a badly fragmented drive to a newly defragmented drive is negligible.

I'll bet your systems are slower than when you first installed them.  That's how it goes.  Over time, we add the odd thing here, the odd thing there, and our systems become slower over time at an imperceptible pace.

---

### Post by Jingle on 2009-02-25
Even though ext3 doesn't need defragmenting is it possible to defragment an NTFS partition from within ubuntu?   

ie. I currently have a shared hard drive that is accessed by some windows machines so it's NTFS but it's also had silly amounts of file activity and I'd like to defragment it as much as possible without having to boot into windows.

---

### Post by randalph on 2009-02-26
No. ext3 can definitely fragment under normal usage, even prior to the drive approaching full. Every filesystem demonstrates real fragmentation and you will likely eventually get very noticeable slowdown if you do not use a defragmentable filesystem. Yes, some filesystems are better than others but all are susceptible under normal real-world conditions. The claim that ext3 only fragments when it doesn't have a contiguous sequence of blocks is just plain wrong. See my posts in this thread for a simple test to demonstrate fragmentation on your own system: [http://ubuntuforums.org/showthread.php?t=1070946](http://ubuntuforums.org/showthread.php?t=1070946)

As far as defragging NTFS from Linux I wouldn't advise it. You could try the filesystem independent defrag code. I've never used it so I can't say how good it is other than the authors acknowledge it's never as good as a native fs-specific defrag utility. If you really want to defrag NTFS from Linux: my impression is the fs-independent defraggers just create a copy of a file and use the new copy if it has fewer extents so I suppose they should be as safe as doing a bunch of normal reads & writes to NTFS from Linux...

Progressive slowdown as a machine ages and undergoes package updates is not something inherent in Linux and is not something that needs to be accepted. If you suspect your slowdown might be due to fragmentation, run test #1 provided in the thread I linked to above - a large # of extents with that speaks toward fragmentation being the cause. It takes a few seconds to run.

I'm not trying to be mean but anyone who goes around telling people that ext3 fragmentation is a non-issue quite frankly doesn't know what they're talking about and they simply refuse to do some simple verification or research. If you want to not deal with fragmentation, reformat using a defragmentable filesystem and run a defragment cron job. e.g. XFS with xfs_fsr.

---

