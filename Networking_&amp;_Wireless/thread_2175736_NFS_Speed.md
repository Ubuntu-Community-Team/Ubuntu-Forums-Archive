---
title: "NFS Speed"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by Groover20 on 2013-09-20
I have a question regarding NFS speed.  

I have a server in the basement, and I made the drives available on my laptop through NFS.  Now, I'm in the process of ripping our DVD collection with the laptop.  I decided to make ISO files instead of getting strictly the movie.

Once the ripping is completed, I transfer the ISO files to the appropriate drive of the server, via NFS.  I noticed that when I start, the speed seems to be betwenn 45 and 50 Mbps.  It then continuously slows down until it gets to 7 or 8.

My question is why is it so quick in the first few seconds? And why does it get to only 7 or 8? Is there anything I can do to achieve the original speed? Or is there another protocol I should use?

Thanks in advance,

G.

---

### Post by paulisdead on 2013-09-20
That's pretty typical for things to slow down a bit over longer transfers.  Smaller transfers tend to be able to fit into memory, and will show as complete sooner, despite not having completely written out to disk.  However, once that buffer gets filled up, how fast it can actually read from and write to the disks can become the bottleneck.

Is that 7-8 megabytes per second or megabits?  Either way that seems pretty slow, but you haven't described what sort of hardware you're using.  If you're using wifi, 7-8 megabytes wouldn't be too bad, but over gigabit NICs that would be pretty slow.  It could also be the performance of the drive in your laptop or your nfs server.

---

### Post by Groover20 on 2013-09-20
I'm on wireless.  But I might very well get a wired connection, since the router is located downstairs directly under my office.

I've never thought of the speed of the drive on the server.  It might be the cause, since the server is older.

Your comment about the buffer answers my question.  I was transfering between 25 and 50 Go.  The first 500 Mo were quick and then it slowed down when it got to 6-7 Go.

---

