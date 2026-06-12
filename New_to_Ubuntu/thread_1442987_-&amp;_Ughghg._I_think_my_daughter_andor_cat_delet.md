---
title: ":-&amp; Ughghg. I think my daughter and/or cat deleted all my videos from my external HDD"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by surelock22 on 2010-03-30
I know what you guys are gonna say:

How could they delete all the videos without emptying the recycling bin? 

The only scenario I can think of is that the entire "Videos" folder was highlighted because my 4 year old watches movies on this Ubuntu PC. Either she sent it to the recycling bin by accident by random button presses or dragging it all in there, or (this is what I'm more convinced of), the Videos file was selected and my cat just walked on the keyboard and hit "delete".

Me being the stupid moron that I am didn't look before I leaped after I erased some un-needed documents (along with the entire catalog of movies and cartoons I have accrued over the past 2 years. I noticed that emptying the trash can definitely took longer than I had expected at the time, and when I went to look for the last episode of "The Venture Brothers"in my .avi collection, My Western Digital My Book's files only read this: 

Media: Audio, Documents
System Volume Information: Restore , (Mount Point Manager Remote Database)
.Trash-1000: Expunged, Files, Info

I just bought this external HDD because my internal 320 Gigs was just too damn full. I can't believe this is happening to me.

Any geeky or not so geeky people know how to recover crap? Nothing is ever "truly" erased, or so I was told, and you should be able to at least try to get the stuff back.

No worries, but if you can help me, it'd be appreciated.

:rolleyes: :-& :-& :-&

---

### Post by Paqman on 2010-03-30
Install the package testdisk, you can use it's photorec function to scour the drive for files to recover. Despite the name it'll recover a lot more than just photos.

More info:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by ajgreeny on 2010-03-30
If the files were on an external disk, the trash will also be on that external disk and just emptying trash from your desktop, as normal, will not also empty that external disk's trash.

Open up nautilus and navigate to the external disk, then Ctrl+H to see hidden folders and files, and see if you can find a trash on that disk.  If you're lucky, you may find your folders are hidden away in there.  I hope so, anyway, for your sake.

EDIT:
It seems you may already have looked for that and see that the files etc are already expunged from trash on the external disk.  Sorry if I mislead you.

---

### Post by quadproc on 2010-03-30
> **surelock22 said:**
> 
Any geeky or not so geeky people know how to recover crap? Nothing is ever "truly" erased, or so I was told, and you should be able to at least try to get the stuff back.

Sorry that I can't directly help with recovering your missing files but I am sure that some other posters can suggest some forensic software that can find deleted files.

I did want to mention that what you were told is generally true; removing a file normally just returns the storage space back to the available pool without altering what is still stored in those sectors.  But there are exceptions!

The first thing is that the removed file's space can be overwritten.  Depending on the particular file system in use, that overwrite may not occur until very much later but you cannot count on this - some systems will quickly re-use the freed up space.  Once the space has been overwritten, it takes a very determined entity (such as NSA) with a lot of funding, a lot of time, and a lot of effort to try to extract the overwritten data, and often those efforts are unsuccessful.

The second thing is that _some_ systems have provision for automatically scrubbing the returned sectors before they are returned to the available space pool.  The older PGP systems had a wipe option which would do this.  Some government (and high security commercial) applications also have automatic scrubbing.  In these systems, removing a file does destroy the data that used to be in it.  The overwrite operation usually involves many passes with data designed to really obliterate the original flux transitions.

Also, some operating systems and some applications will rewrite an edited file into exactly the same sectors that it had previously occupied.  If the new file is longer than it used to be then additional sectors are appended but the original data is destroyed by the write of the new data; you can't go back to it.

So, removed files are sometimes lost forever.

quadproc

---

