---
title: "DLink WUA-1340 ... maybe"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by botulismo on 2007-05-30
Well, yes, that's the name of the wireless USB adapter I'm using on this laptop I've been trying to salvage from my closet... Feisty works fine on it, everything installs correctly, and it even detects the wireless adapter. It even goes so far as to list the available wireless networks around me (I live in an apartment complex.) However, whenever I try to connect to my (or a neighbor's, in an act of desperation) wireless network, it either freezes at "finding IP address" or it displays the wireless as connected but only at 0% (and hence does nothing for me.)

I plugged this adapter in on my regular desktop and it connects to the network (or a neighbor's) correctly... My roommate's Windows laptop connects perfectly to the network. But why wouldn't it be doing it correctly for my laptop? Any ideas? It seems bizarre that it is installed and can detect wireless networks but not actually do anything.

I'll provide any more info if someone could help.

---

### Post by dannyboy79 on 2007-06-07
this is because the native rt73usb driver that feisty provides doesn't work and you either need to use ndiswrapper OR recompile new rt73 driver from source. here ya go: [http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340](http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340)

---

