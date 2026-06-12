---
title: "Wireless Card not detecting Networks..."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by Mirthoneist on 2007-03-17
Hey guys, I just installed Ubuntu and am having some trouble... I'm new to the OS, so go easy on me. :D

My problem is that my Wireless Connection (eth1) doesn't detect any networks because there is nothing in the drop down box.  I know that the network name on my router is named "hello", so I put that in the ESSID and it connects fine.  If I put in anything else, it doesn't connect, obviously.

I really don't know what to do to make it detect networks...

The wireless card on this laptop is an Intel Pro/Wireless 2200BG.  If anyone knows what the problem might be, I'd appreciate any help. Thanks!

---

### Post by gradedcheese on 2007-03-17
Hmm... people keep having this problem, and I had it happen to me once or twice.  One thing you can do is just upgrade to NetworkManager (find a HOWTO about this on these forums and follow the instructions).  It's a much nicer interface (and replaces the one you're using in the next Ubuntu release anyway), plus it will show the networks correctly.  You can verify that your interface really can scan by using the terminal with this command:

```

iwlist eth1 scan

```

---

