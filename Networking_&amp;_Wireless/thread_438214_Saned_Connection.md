---
title: "Saned Connection"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by yahooadam on 2007-05-09
I finally managed to get saned working on my computer with the scanner attached today

Using windows and SaneTwain i can get images over the network so saned it definitely working and not blocking connections

However, with my ubuntu computer, I'm at a loss on how to connect to the saned computer

How can i acquire an image on the ubuntu computer, if i do scanimage -d net:IP.addr.goes.here (which seemed suggested on the Internet) it doesn't work

Any help here would be appreciated
Yahooadam

---

### Post by needhelpplease on 2007-07-17
I'm running Feisty Fawn and I'm running into the same problem.  My Ubuntu client can't access the Ubuntu server.  Not sure why.  When I had the server running on Suse it was fine.  Any ideas would be appreciated.

---

### Post by needhelpplease on 2007-07-17
I figured out the problem: saned can't run as user saned.  It can run as any other user apparently.  I have it running as root within xinetd and it's fine, although this is less than ideal from a security point of view.  I put up a blog entry about this:

[Linux network scanning with saned](http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html)

This works for now, but of course I'm interested in a solution that lets me run this thing the right way.

---

