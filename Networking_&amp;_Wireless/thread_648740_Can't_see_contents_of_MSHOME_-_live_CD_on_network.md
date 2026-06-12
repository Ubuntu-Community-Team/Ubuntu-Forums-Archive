---
title: "Can't see contents of MSHOME - live CD on network"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by ryank76nz on 2007-12-24
I'm on my ubuntu PC, connected via a router, trying to see my Linux Mint PC's files. The OS went bad (might be a hard disk  issue) so i'm running the Mint Live CD on there.

I mounted /dev/hda1 to /mnt/disk1 and can see all the files in the home folder on the PC.  I want to get to the files: /mnt/disk1/home/brooklynne

The IP address of the Mint PC is 192.168.1.2 and this one is 192.168.1.3. 

So far I have installed SSH on here and tried to get to it that way with no luck. I have shared that folder on the Mint PC. Now when I restart this PC the mshome folder appears on my desktop (even though neither PC are Windows) and I can't get into it - I get the message:

Couldn't display "ssh://mshome", because no host "mshome" could be found.

I have tried:

ryan@ryan-desktop:~$ sudo mount 192.168.1.2:/mnt/disk1/ /files
Password:
mount: 192.168.1.2:/mnt/disk1/ failed, reason given by server: Permission denied

When I do this Live CD behind me whizzes away but Permission denied is as far as I get. 

Can someone help please? There are too many variables here for me to work it out from forums - I have been trying for days. Thanks

---

### Post by ryank76nz on 2007-12-24
*bump* do I need to provide more info?

---

