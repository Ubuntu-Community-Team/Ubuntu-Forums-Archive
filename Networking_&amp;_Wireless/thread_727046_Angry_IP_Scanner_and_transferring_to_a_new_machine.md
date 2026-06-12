---
title: "Angry IP Scanner and transferring to a new machine"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by Valyander on 2008-03-17
I am currently using Angry IP Scanner at work, and I find it very useful as a network scanning tool.
However I have recently tossed my old machine aside and replaced it with a somewhat more up-to-date one.
Then I met a problem.

One of the weaker aspects of this program is the favorites.
I have googled and altavista'ed all I can think of, and I have browsed the Angry IP Scanner website, but nowhere can I find how to transfer favorites from one machine to another under a Linux environent.
I found that in Windows one had to copy out a registry file and move that over to the new machine, but that won't help me much here.
I have also checked the Java runtime cache and such since the Linux client is Java based, but to no avail.

The thought of having to repopulate a favorites list of this size makes me want to cry a bit.
So, does anyone in here maybe know how I can do this?

---

### Post by Valyander on 2008-04-07
I have now repopulated my favorites list (manually), and crossed my fingers I will not have to switch machines for a very very long time.

Should however anyone come across a solution feel free to post it :)

---

### Post by pseudo-random on 2008-04-07
Angry IP scanner...thats a bit 1990's.
Try Nmap. Combine that with a shell script with smbfs and you've got something that pisses all over Angry IP scanner.

---

### Post by Valyander on 2008-04-08
I'm all game with a better solution than Angry.

I have installed Nmap with Nmap Front End, but what I can't seem to find is some sort of favorite solution. The reason I ended up with Angry now is because I can quickly access a named IP range to scan. The naming of IP ranges is quite handy when you quickly must access one range among 150.

Any tips?

[Edited to clarify]

The functionality I need is fairly basic.
I need to scan an IP range (usually 31 IP adresses) on our network.
Then I need to get the alive IP adresses possibly with the machine name (most are windows boxes).
Some way to easily and quickly access the scan ranges.

---

