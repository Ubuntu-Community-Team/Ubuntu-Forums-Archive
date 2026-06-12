---
title: "listening to music off of portable had(160 gig my passport) is laggy, and freezes"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by djmh on 2009-07-01
i have about 45 gigs of music on my 160 gig portable hd, i have a dell mini 9 with a 16 gig sdd and 1 gig of ram .... music plays fine off of my ssd but when i try to listen to music off of my usb portable hd it will freeze, almost like its buffering and then it will resume playing ...or sometimes it will say music cannot be read from source and wont play the song any further ... i dont know if this is an ubuntu problem, or what ... but if you have any suggestions for listening to my music off of my hd without lag that would be great !!

btw, i have songbird ... but i usually use gstreamer to listen to my music.
and i have tried many different players .. and all of them do that lag thing ...
thanks for the help !!

---

### Post by djmh on 2009-07-13
any ideas ?

i have read some ways to change the buffer rate of music...i am a bit Leary to try them out...unless you would suggest that ?

---

### Post by DaGrimReefah on 2009-07-13
Have you tried Rhythmbox? (Applications >> Sounds and Video >> RhythmBox)

---

### Post by djmh on 2009-07-13
yes.. i have tried many different media players ..they all produce the same effect...

---

### Post by RedRat on 2009-07-13
What kind of portable usb hd are you using, is usb 1 or usb 2?. Is it really a hard drive? or solid state like your mini? If it is a hard drive of course, there could be a number of problems there, i.e., fragmentation, lost bits, perhaps a failing hd. HDs do fail eventually, some sooner than others. Perhaps it was accidentally damaged. 

That you are experiencing the problem with a variety of software on teh Linux side, it might be that the usb hd just can't stream fast enough, some of the old usb1 memory drives were that way.

---

### Post by djmh on 2009-07-13
well, im assuming that it is 2.0 ... but im not entirely sure, how would i check ?
yes it really is a hard drive.
could a defrag possibly mess anything up ?
that does seem like a good idea, i never thought to do that.
i sure hope it is not failing, how would i go about checking if it is on its way out ?

---

### Post by djmh on 2009-07-13
uhhhm, so how exactly would i go about defragging my portable hd ?

---

### Post by Ravernomina on 2009-07-13
Gparted can run Disk checks. Along with USb 2.0 You can use device manager to see what ports u have on your computer. All Devices that came out 2006+ is usually USB 2.0. Usually If it came with a thicker cord that a good indicator that it USB 2.0.

---

### Post by djmh on 2009-07-13
yeah, i am almost one hundred percent positive it is 2.0
but it probably needs to be defragged, most files were put on from a windows machine.... so are you saying gparted can defrag it for me ?

---

### Post by RedRat on 2009-07-13
> **djmh said:**
> well, im assuming that it is 2.0 ... but im not entirely sure, how would i check ?
yes it really is a hard drive.
could a defrag possibly mess anything up ?
that does seem like a good idea, i never thought to do that.
i sure hope it is not failing, how would i go about checking if it is on its way out ?

Well if the drive is NTFS, and you have a handy Windows machine, hook it up to that machine. However, before defragmenting the disk, run chkdsk and ask for a repair. Then use either the Windows defragment program. The most important thing is that you clear any lost segments or fragments, that is what chkdsk does, if you don't do this you create more problems. If you are lucky, the defragmenting program just stops and informs you, if you are unlucky, the problems become worse!

In my Windows days, i used a program called Diskeeper which could place all the file fragments contiguously which meant that they would read faster and cut search time on the disk. They used to provide a trial version otherwise you have buy it.

---

