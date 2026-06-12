---
title: "ext3 vs. NTFS?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Karychy on 2009-02-22
Hello,

From what I have read about ubuntu, I get the impression that one of the important advantages comapred to MS Windows is the file system. I just had a look at a wikipedia article that compares file systems, and can't say I managed to understand how/whether ext3 is better than NTFS. In fact, NTFS seems to have more features. I have read that no maintenance acctivities such as regular defragmentation were required under ubuntu, which is attributed to the better file system. However, I am failing to understand which exact feature/quality of ext3 prevents the huge fragmentation I have observed on Windows systems.
Can anyone please clarify this, or give me appropriate links for further reading?

Thank you!

---

### Post by yeats on 2009-02-22
You might want to read this page about why Linux doesn't need defragmenting:

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")

---

### Post by marshall.robert on 2009-02-22
It's called Journalling. [http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

Enjoy :)

---

### Post by blueridgedog on 2009-02-22
Fragmentation is prevented (from a lay perspective) by the journaling system that buffers writes and by the design of the system.  It will fragment if you keep the drive near full (search Google for ext3 fragmentation and you will find many examples).

As far as NTFS, it is a great file system that is, in my opinion, on par with ext3 and as you suspect better in some ways.  ext3 however is open source and also has a simple access methodology (user group other) while NTFS is proprietary and managed with access control entries that are considerably more complex (and more detailed and refined).  NTFS will allow permissions based on many groups and many users.  

The two are not really comparable as they have vastly different missions and origins.

---

### Post by Kellemora on 2009-02-22
Hi Kary

It might help if it explained to you in a graphical sort of way.  Although not exactly dead on, it will give you a visual image of what's going on inside that little black box, hi hi........

Let's start with EXT3 since it's the simplest to explain.
Visualize a wall filled with little pigeonholes, like the sort case at your local post office.  And assume you are in the middle of the row of pigeonholes.  Mail that goes in and out of these pigeonholes are placed in those holes intact, unless the letter is TOO BIG for the pigeonhole.  Then the letter is cut in half and put into two pigeonholes side by side to each other.  When you EDIT a file stored in a pigeonhole, it is saved back into the same pigeonhole, until the file gets too BIG to fit into that pigeonhole, then it uses two pigeonholes that are side by side to each other.  Files that are used most often are stored in the center and files that are rarely used get moved to the outside edges.  Pigeonholes are used up scattered apart from each other to leave room if a file grows.
EG:  IF you only had 10 pigeonholes in the center column, it would put files in 4, 6, and 8, leaving 1 and 10 for rarely accessed items.  If you edit the file in pigeonhole #4 it gets put BACK in pigeonhole #4 intact.

Now, let's look at NTFS.
NTFS is like a LONG string of Beads.  Each new file is stuck onto the end of the string of beads.  And if you EDIT a file, the edited part gets added to the end of the string of beads.  So a file could appear something like this when first started AAAABBBBCCCCDDDD nice and neat, no fragmentation.  BUT, you edit file A and save those changes, now your file looks like this AAAABBBBCCCCDDDDAA, part of A is now at the end.
You edit file C or save the score from a game that is stored as C and you end up with a hard drive looking like this.  AAAABBBBCCCCDDDDAACC.
OK, now you edit file B and save those changes.  Your hard drive is starting to look like this now.  AAAABBBBCCCCDDDDAACCBB, you add a new file to your hard drive and now you have AAAABBBBCCCCDDDDAACCBBEEEE.
You decide to add another address in your address book which is file A.
Now your drive looks like this AAAABBBBCCCCDDDDAACCBBEEEEAA.
When you go to read file A, it looks first to AAAA, then to the second instance of AA for that edit session, then finally to AA at the end to get the new address you just added.  The file just keeps getting more and more fragmented.  Running Defrag will put the files back in order so you would have AAAAAAAABBBBBBCCCCCCDDDDEEEE.  But the minute you do something, it begins to fragment again, slowing the drive back down.

In the EXT3 system, if you did a Fragmentation CHECK, it may show that files are FRAGMENTED when they really are not at all.  In EXT3 a file that was too big for one pigeonhole is stored SEQUENTIALLY in the pigeonholes.  Let's assume the file is 13k in size, and the pigeonholes are only 5k in size (this is just figurative).  It would use pigeonhole A for 5k of the file, pigeonhole B for 5k of the file and pigeonhole C for the remaining 3k of the file.  And it would probably leave pigeonholes D,E,F,G & H Empty to make room for expansion of that file, unless the drive is near full.
As you can see, the read heads of the hard drive would read the file from location point A and ending point C with no breaks.  Meaning it don't say Read point A start to A end, then B start to B end, and C start to end of file.  It just reads the contiguous file as all one piece.  The read head just flows along quickly.

On NTFS to read a fragmented file it would read AAAA, then jump to past DDDD to read AA, then jump again past EEEE to read the last part of file AA.  Time consuming!!!!!

IF EXT3 file system is SO FULL that it CANNOT use pigeonholes that are next to each other sequentially and it cannot find any area on the drive that does have enough pigeonholes sequential, THEN it will split the file into two pigeonholes that are not next to each other.  THEN you have a truly fragmented file.  LARGE Sequential files ARE reported as Fragmented because they reside in more than one pigeonhole.  But as you can see, they are NOT fragmented at all.

How a hard drive actually works is considerably more complex than the graphical image above, but it gives you a good idea of what is going on inside that box.

Interestingly enough, when you use LINUX to drive an NTFS drive, in a sense it almost defrags itself during use.  When Linux saves a file to an NTFS drive, it looks for a space large enough to fit the file without fragmenting it all to pieces to fill in missing beads.

When running windows defrag, it removes the file named AAAA to the END of the string of beads, then it reads BBBB BB BB to see if it will fit where AAAA was, it won't so it then moves file BBBB to the end and looks at file CCCC CC, aha, that will fit where AAAA BBBB used to be, so it moves CCCC CC together.  Reads how much space is left BB's space is, so it looks to file DDDD, that won't fit so it moves DDDD to the end and reads EEEE which will fit in BBCCCC space.  And so on and so forth!

When Linux writes to an NTFS drive, it looks for a space large enough to fit the file, and when it finally finds a space, it writes it there and removes the part originally loaded from to clear that area.
So, if you edited file AAAA and made it AAAAAAAA it won't fit back where it came from, so it places it behind EEEE and opens up AAAA for a smaller file.

Nonetheless, EXT3 places files as far apart from others as it can.
If you have 10000 pigeonholes, it will use number 5000 for the first file you save.  Then 2,500 for the next and 7,500 for the next.
Linux NTFS-3G still lines them up like a string of beads, but with some beads missing along the way.  Gaps that can be filled with files that fit that size gap and tries to save files contiguous whenever possible.

Again, the above is not 100% accurate, but close enough for understanding pictorially speaking!

TTUL
Gary

---

### Post by Karychy on 2009-02-27
Thanks everyone for your responses! It really helped a lot!

~Kary

---

