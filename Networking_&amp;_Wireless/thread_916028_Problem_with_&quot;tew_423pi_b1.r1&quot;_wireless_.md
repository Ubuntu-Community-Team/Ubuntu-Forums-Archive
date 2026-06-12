---
title: "Problem with &quot;tew 423pi b1.r1&quot; wireless card"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by ntoulas on 2008-09-10
I want to use only ubuntu but i can't.
I have problem with my wireless card.
Because I'm beginner, please tell me step by step.
Ubuntu 8.04

---

### Post by ntoulas on 2008-09-12
anyone?

---

### Post by ozanamn on 2008-09-12
Have you tried ndiswrapper yet?

---

### Post by timjohn7 on 2008-09-12
I am not an expert, but I have helped a few people with wireless problems.

Firstly, I recommend using wicd to setup your card.

If you know how to do this, ignore 1 - 6 in the next section.

1.  Select System>Administration>Synaptic Package Manager
2.  Enter your password
3.  Select Search and enter wicd in the Text Entry Box
4.  Once it is found, mark for installation
5.  Once it is installed, reboot (make sure your card is in the computer)
6.  Run wicd and see whether it has discovered your card.
7.  If not, open Terminal and type sudo lshw
8.  Post the output here and we'll take it further then

Cheers

---

