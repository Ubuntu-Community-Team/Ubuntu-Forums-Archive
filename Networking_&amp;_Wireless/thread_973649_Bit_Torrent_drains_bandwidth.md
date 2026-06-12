---
title: "Bit Torrent drains bandwidth"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by sirebral on 2008-11-06
There is a huge problem in the 8.10 distro of Transmission.  I am running the software on another computer, and if I run the software it slows down the internet for my other computer.

I know it is now the amount of bandwidth that the PC running Trans is receiving because I have scaled that down to 15kb/s.

The problem that I see is that the bandwidth on the computer I am working on is drained somehow.  Browsing is so slow, and it seems to effect Firefox and the Update manager the worst.  FF is slowed so bad that clicking on tabs grays the software out for a time.

If I even pause Trans, the bandwidth returns and browsing speeds back up.  What is causing this?

---

### Post by MakotoTheKnight on 2008-11-06
My guess is that your problem is self-evident.  Bittorrent is causing your lags, so naturally, stopping it would restore your network speeds to normal.

I haven't noticed hiccups when using Transmission, so my advice is that you go with that instead of BT.  Just remember if something's using the network's bandwidth, it's going to run a little slowly.  ;)

---

### Post by crazyness003 on 2008-11-06
> **sirebral said:**
> I know it is now the amount of bandwidth that the PC running BT is receiving because I have scaled that down to 15kb/s.

Is that your DL limit or UL limit? Sometimes, when you neglect to set a UL speed-limit, it just sucks the BW like a vampire. You achieve excellent UL speeds in the torrent, but everything else suffers.

Also what the guy above me said, if its too slow, turn it off and only run it at nitetime (or when you passivly dont need to use any net functions)

---

### Post by sirebral on 2008-11-06
i actually meant Transmission.  I am used tot he BT client still.  i was just coming to edit my post before anyone answered.

So,the answer isn't so self evident, Makato.  Unfortunately.

No, crazyness.  My UL is 0-3kb/s.  So over all I am sending 18kb/s with Transmission.

---

### Post by crazyness003 on 2008-11-07
> **sirebral said:**
> i actually meant Transmission.  I am used tot he BT client still.  i was just coming to edit my post before anyone answered.

So,the answer isn't so self evident, Makato.  Unfortunately.

No, crazyness.  My UL is 0-3kb/s.  So over all I am sending 18kb/s with Transmission.

Maybe your internet connection is throttled by your ISP? I dont know. I had this problem when i was on a slower "high speed" connection. I could only use web browser or torrent at 1 time. But since this only started to happen when you upgraded, then there may be a necessity for you to file a bug.

---

### Post by sirebral on 2008-11-07
Not sure what happened.  I know I downloaded some updates this morning so that might have been what happened.  

I went to my laptop today to check on the server software I am running and I noticed that Transmission had been running and downloading.  I didn't even notice it.  So this is [SOLVED] and I will edit it to reflect that.

---

### Post by salingova on 2008-11-11
I have the exactly same problem. After upgrading to Ubuntu 8.10 when running transmission it totally slows down the network. Let me just clarify what you did to make it work, or did it just stopped causing problems on its own? I am still experiencing this problem.

---

