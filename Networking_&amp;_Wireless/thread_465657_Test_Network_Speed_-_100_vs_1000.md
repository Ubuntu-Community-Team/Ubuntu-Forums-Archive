---
title: "Test Network Speed - 100 vs 1000"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by verevi on 2007-06-05
Forgive the noob question, but I've searched around and I can't seem to find something this simple. 

Basically, I would like to confirm that files copied from one machine to another on my network are generally moving at the speed that I should expect for my network.  I'm currently connected using 100baseT but I am planning on switching to a gigabit switch soon.  

According to netspeed panel app, when I'm ssh'ing from one box to another I am sending at about 2 MB/s.  Is that about right for a 100M connection?  What is the simplest way to test this?  An FTP connection?    What should the transfer speed be for the gigabit network?

Sorry if any terminology used in this question is incorrect, please clue me in where necessary.  

Thanks for any help.

---

### Post by verevi on 2007-06-06
I just FTP'd a file between computers on my network and got 
**[SIZE=+1]9208.27 (KB / s)[/SIZE]**

That's pretty much what you'd expect for 100baseT I would guess.  So, I guess I can assume my network is transfering as expected?

---

### Post by netztier on 2007-06-06
> **verevi said:**
> I just FTP'd a file between computers on my network and got 
**[SIZE=+1]9208.27 (KB / s)[/SIZE]**

That's pretty much what you'd expect for 100baseT I would guess.  So, I guess I can assume my network is transfering as expected?

9,2Mbytes/s is good, but 100baseT can do better; 11MBytes/s is possible and can be achieved. The fact that you only see ~2MBytes/s with SSH (using scp or sftp) most probably is due to the fact that all traffic has to be en/decrypted by the systems involved. Changing encryption algorithms might help here.

Try the **iPerf** package from the universe repositories to test raw TCP throughput from device to device; you'll have to install it on both endpoints of the TCP connection and run one as "server" and the other as "client". It uses server/client terminoligy inversed - actually the "client" is *sending* to the server. Also take a look at the different command line options, there's a lot of fun to be had with these (multiple TCP streams, TCP window sizes, bidirectional etc...).

Filling a gigabit pipe is not a trivial task, even with modern hardware, so don't get confused if you see "only" 600-700Mbit/s with iPerf after the gigabit upgrade. If you transfer to/from disk, it's very probably going to be even less. 


best regards

Marc

---

