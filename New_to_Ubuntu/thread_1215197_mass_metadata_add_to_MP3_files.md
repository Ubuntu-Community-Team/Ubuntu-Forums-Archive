---
title: "mass metadata add to MP3 files"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by earthpigg on 2009-07-16
hi,

i started my mp3 collection about a decade ago. for some reason, several years back, i decided to strip ALL metadata from my collection. 

as a result, i have about 2,000 mp3 files with zero metadata - the file names are accurate, but not uniform. ie, some are "artist - title.mp3" and some are "artist - album - title - track number.mp3" and yet others are "artist - track number - album - title.mp3" and other random variations.

the only thing i have ensured, over the years, is that the first part of the file name is the artist.

is there any method that anyone is aware of that could possibly compile accurate metadata by, for example, assuming the first part of the file name is the artist and comparing the music contained in the mp3 to music by that artist and looking for a match?

....or am i SOL and forever doomed to using mp3 players that can simply sort/display by file name, and never get to see pretty album art?

---

### Post by starcraft.man on 2009-07-16
EasyTag editor. Just install from repos, package name is of course easytag.

Point the editor to the directory, I assume you at least have the music sorted by CD yes (or in such a way as you can tell).

Then, you'll see all your tracks in main middle pane. Select all the tracks belonging to an album (shift or ctrl + click), then click the CD in the gui on the middle right (or ctrl + B) to bring the CDDB search. Then push find, it matches albums by length of each track and total. If it isn't found, you can manually edit a whole album by highlihghting all of them then filling artist, album, year and right clicking on each entry and selecting "tag files with this field" then the tag will be aplied to all the selected files.

Once your done editing, save out (ctrl +s). Takes a while to process that many files, come back in 5.

---

### Post by earthpigg on 2009-07-16
well, this seems simple enough.

thanks!

---

### Post by spillin_dylan on 2009-07-17
I also strongly suggest MusicBrainz Picard, also in the repos, but I think there is a more current version on their website [http://www.musicbrainz.org/](http://www.musicbrainz.org/) I think.  I'm sure it has at least equal functionality to Easytag, but I found the interface easier to use.  And, it can actually download art and link it to the file at the same time!  

Of course, everyone has their own preference!

---

### Post by Chronon on 2009-07-17
+1 for Picard.  It does a good job, in my experience, with scanning your files and properly guessing the correct identity of most files.  It's also largely automatic, though you'll want to double check the results as I have gotten some false IDs a couple of times.

---

### Post by earthpigg on 2009-07-17
easytag is already about 4/5 done, but ill check out picard in a few.

thanks again!

---

### Post by Chronon on 2009-07-17
Cool.  I also use EasyTag and think it's a great program.  It seems the different file naming patterns didn't cause too much problem, then.  ;)

---

### Post by earthpigg on 2009-07-17
> **Chronon said:**
> Cool.  I also use EasyTag and think it's a great program.  It seems the different file naming patterns didn't cause too much problem, then.  ;)

i went down the list and did them in batches - probably about 5% of them have inaccurate or odd tags because of that.... the track number being listed as the album and the like. 

let's see if picard can refine it any.

---

