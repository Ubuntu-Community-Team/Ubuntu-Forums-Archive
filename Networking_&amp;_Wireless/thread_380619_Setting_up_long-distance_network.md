---
title: "Setting up long-distance network"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by skyline5k on 2007-03-09
How would I set up my laptop to be able to access my desktop from anywhere? I'm on the road quite a bit, and would like to have access to my files (mostly music & entertainment as I live in China & hate Chinese TV).  I've networked my desktop to my WinXP desktop easily enough, and I can go back/forth through the "Workgroup" but how would I be able to tap into my desktop without being on the same wired/wireless network?

Also, probably a general linux question, & not an Ubuntu-specific question... My wife's company uses a company intranet, with Microsoft Exchange & such (obviously a Windows Network), and her company offices worldwide all have access to this intranet.  I'm setting up a new linux server and would like to be able to do the same with linux.  This sort of goes with the above, but on a grander scale. Any suggestions as to where to start? I haven't purchased the server yet, but plan to in the next week (new hosting company).

---

### Post by spin2cool on 2007-03-10
One option would be to set up ssh on your desktop, then use sshfs to mount the remote filesystem on your laptop.  These forums have tutorials on how to do both.

---

