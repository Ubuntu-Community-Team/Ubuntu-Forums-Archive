---
title: "Converting netbook into wifi access point"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by treesloth on 2014-04-19
Hi.  I have an Eee PC 900A running, until recently, Ubuntu 12.04.  I converted it, seemingly successfully, to a wireless access point using the instructions I found [here]("http://superuser.com/questions/437137/how-to-turn-my-linux-netbook-into-wifi-ap").  It worked until the first reboot.  Then, no networking at all.  Restarting networking did not help.  Since I was planning to wipe it and install 14.04, I didn't spend much time on it.  So, I installed 14.04 and went through the same instructions.  I again seemed to have created an AP, but upon reboot I had the same problem.  I've returned it to the original, working 14.04.  Is there a recommended way to do this?  Here's what I'm going for:

1)  I would like to use the netbook to share a wired connection to multiple clients wirelessly with secured connections.  
2)  When not serving as an AP, I would like the netbook to be able to connect to other wifi connections as a client.
3)  I'd like it to continue to function as a netbook in other ways, with the same Ubuntu utility as otherwise.

I'm not completely committed to 14.04.  If a different version is better for my purpose, that's fine.  Many thanks in advance.

---

### Post by varunendra on 2014-04-20
Might help if you also post exactly which card and driver you are using, which means the outputs of the following -
```
lspci -nnk | grep -iA2 net
lsmod
```

Run the above commands in a terminal (Ctrl-Alt-T) and post back their outputs here. While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

I may not be able to reply back to your post in a timely fashion, but hopefully the above outputs may get you some good help from others.

---

