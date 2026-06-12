---
title: "Accidentally started install on external hard drive archive"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by ZoneSeek on 2011-01-24
I was trying to install Ubuntu on my girlfriend's netbook, I think the install didn't detect the netbook's hard drive (and I should've noticed if it auto-selected my portable drive, mea culpa) so Ubuntu started to install on my Seagate external drive. I shut down after the installer asked me to choose my timezone, restarted, now I can't get to the files in the Seagate from my own Ubuntu netbook or on Windows machines.

My house burned down last week, what's left of my life is on that Seagate, 15 years of notes and journals. I know, should've backed up first thing. Disk Utility sees the Seagate:
[http://i275.photobucket.com/albums/jj300/zone815/Screenshot1.png](http://i275.photobucket.com/albums/jj300/zone815/Screenshot1.png)
[http://i275.photobucket.com/albums/jj300/zone815/Screenshot2.png](http://i275.photobucket.com/albums/jj300/zone815/Screenshot2.png)
[http://i275.photobucket.com/albums/jj300/zone815/Screenshot3.png](http://i275.photobucket.com/albums/jj300/zone815/Screenshot3.png)


I'm hoping (desperately) that I can just delete the Linux Swap partition and then I get my digital life back. I'm looking up the Ubuntu Philippines team too, because I'd pay money for a safe and sure way to recover my drive files.

Got another 320gig hard drive, a Toshiba. Any way I can copy the whole Seagate over? So that there's a backup of the mess I'm trying to fix.

---

### Post by psusi on 2011-01-24
You can try testdisk and photorec.  They may be able to at least recover some of it, but at this point you are on hope and prayer mode.

---

### Post by ZoneSeek on 2011-01-24
I don't think the install reformatted the Seagate drive yet, it was just starting to setup the install when I shut it down. But so I'm screwed cos of the partition?

Downloaded testdisk, still learning how to install on Ubuntu.

---

### Post by oldfred on 2011-01-24
Testdisk is in the repository. You just have to download it from synaptic.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

photorec will recover any files it can find on a drive. I had lost a couple of folders and it recovered 1000's of files, but for example I had saved a text file many times. It found all the versions, and I do not think I ever found the last saved one.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by psusi on 2011-01-24
It started formatting, just hope that it did not get too far.  If not, then testdisk or photorec have a better chance of getting more files out.

---

