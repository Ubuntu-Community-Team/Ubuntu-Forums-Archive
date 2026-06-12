---
title: "Huge file received at window printer"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by geofff on 2007-12-09
I have recently upgraded to Gutsy, replaced the printer and added a nvidia card. Because of some problems with previous version (6.10) I did a clean install then added back the home directory. I had quiet a few problems.

This one has me beat (not that difficult - I'm hardly flying with these things!) 

Printing is via a printer connected to a networked windows machine - using XP. Today I sent a file of 36.3kb to be printed (26 pages) it took about an hour. When looking on the windows machine the size of the file being printed was 653Mb - nearly 20,000 times bigger than the one sent! - although only the stuff sent was printed. 

Is there something I've missed?!

As a check I typed a test page of 6.7kb which, when received for printing, was 368kb - only 60 times larger, but still a lot bigger than I would have expected.

---

### Post by geofff on 2007-12-09
This doesn't explain the huge file size - but it seems there is a problem on the windows machine. 

Something called hprblog.exe which is a bit of hewlett packard software is utilising 99% of CPU and slowing everything down particularly remote printing. When this application is terminated printing does speed up quite a bit. However the file size transferred after termination is still 653Mb. Surely this cannot be right?

I've checked the package hprblog and it's not a virus, but it's not a positive influence on family dynamics (the windows machine is my wife's)! I've contacted hp support.

However I'd still appreciate any thoughts on the huge increase in file size from sent to received. 

Thanks Geofff

---

### Post by geofff on 2007-12-11
Since the last post I have wondered whether the problem was something to do with the odt format that the windows box didn't like. I therefore converted it to doc and resent it. The size of the doc file on the linux box was 197KB and when received for printing on the window machine was 649MB - although the size of the file sent increased, the size received reduced by 4MB - something but still not an explanation for the huge file size.

I then created another file of 26 pages with just one character per page  to see whether there was something complex within the original file that was causing the problem. In odt format the new file was 7KB, and when received for printing it was 4.86MB. This is an increase by a factor of about 700 - huge but not comparable with the first one. When converted to doc format this was 94KB and when received for printing was again 4.86MB

I'm beginning to think that the increase might just be normal overhead for printing with a printer attached to a windows box. However it seems just too huge to comprehend. 

The other worry is that it might be a method that a virus/rootkit has found for downloading my disc contents, bypassing controls that I've installed with Firestarter. I don't accept that linux cannot be compromised - especially when I attach to websites that take a very long time to load but which won't allow me to disconnect whilst they are loading. Paranoid maybe but that doesn't mean they're not out to get me!

Any reassurance regarding the normality or otherwise of a 653MB file received at a windows box when the file sent was only 36KB would therefore be much welcomed.

---

