---
title: "Frostwire won't connect"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Scheater5 on 2006-08-26
My frostwire is continually "starting connection.  I've googled it, and from what I read about limewire, it seems I need the "newest Java" - but from my previous attempts to install Java, that's over my head without "easy ubuntu" or Automatix.  I've run both of these, and still frostwire won't connect.  Any ideas?

---

### Post by v1ct0r on 2006-08-26
Well...
[http://www.linuxquestions.org/questions/showthread.php?t=447405](http://www.linuxquestions.org/questions/showthread.php?t=447405)
[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)
Hope these help you. Goodluck.

---

### Post by Scheater5 on 2006-08-26
Alas, no.  Running it in a terminal yeilds

Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]

So I suppose Java is not the problem.  But I also get this message, which I don't understand.

log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).

---

### Post by lemix on 2006-10-29
Hey, your post is a little old, if your monitoring it or have email forwarding on this post i was wondering if you managed to solve this problem. I understand your problem unlike whoever replied to it. It launches but it wont connect to a network. What did you do to solve this problem?

---

### Post by Scheater5 on 2006-10-30
Hey lemix.  
As it turns out, the problem is "unsolvable" - I was on a network at a university that has a firewall with most P2P software blocked.  But, it seems they've never heard of Apollon, and I managed to configure it with some minimal success to get through the network.  I'm afraid I'm a bit noobish, and I don't *completely* understand the "ins and outs" of why I couldn't connect, or why I can now, but I'm pretty sure it has to do with which port the P2P software is using (I cranked Apollon up pretty high - in the 200s, I believe).  I brought my laptop home for a weekend, and Frostwire works fine.

---

### Post by bucky100771 on 2007-05-05
I wish I understood a word of the previous post because it sounds like you solved the problem and like you and the previous post to yours, I'm having the same problem.  Both frostwire and Limewire simply give me "starting application" and never run...

---

### Post by Scheater5 on 2007-06-02
What's your situation?  Are you behind a firewall, or on a large network?  In my case, I was behind a firewall on a university network that had blocked the ports p2p networks generally go through, so I changed to a program they weren't aware of and manually changed what port it goes through.  It's been a while since I did that, and I'm on a different network now.

---

