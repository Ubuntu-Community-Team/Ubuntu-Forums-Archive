---
title: "How to troubleshoot MTP segfault?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by salmonsm on 2010-01-22
Hello,

I'm trying to trace down an issue and just don't know how to proceed from here. I own a Creative Zen X-fi and installed Gnomad2 to manage it. All was peachy for quite some time. I saw mtp-tools listed in Synaptic and wondered if I could add console support to my setup so I could sneak in via the command line to perform small tasks. I installed it and, ever since, Gnomad2 craps out when I connect my X-fi.

Here's the breakdown:

When I connect it, I dutifully unmount it and start Gnomad2 and let it discover the X-fi on its own, which it did beautifully until recently

it hesitates, then dies when trying to list files on the X-fi

When I run it in the console (as my regular user and with sudo), i get

~$ gnomad2
Queried Creative ZEN X-Fi
Segmentation fault


I tried running it through strace and get, while it's loading the last visited directory on the hard drive, lots of these:

read(3, 0x99ae1c8, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x99ae1c8, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=7, events=POLLIN}], 4, 0) = 0 (Timeout)
read(3, 0x99ae1c8, 4096)                = -1 EAGAIN (Resource temporarily unavailable)


and then, when it starts looking on the X-fi, it ends abruptly with

read(3, 0x99ae1c8, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x99ae1c8, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=7, events=POLLIN}], 4, -1 <unfinished ...>
+++ killed by SIGSEGV +++

My question is, can I research this any further? I have tried uninstalling mtp-tools, and gnomad2, then reinstalling it, even wiping out libnjb and reinstalling it along with gnomad2.

I'd willing to post the output of anything.. if only I knew what.

Any insight would be wonderful. Thanks.

---

### Post by NoBugs! on 2010-06-30
It's a known [bug]("https://bugs.launchpad.net/ubuntu/+source/gnomad2/+bug/548967"), solution is to use the old package, as described [here]("http://ubuntuforums.org/showthread.php?p=9180401").

---

### Post by salmonsm on 2010-06-30
huh, couldn't find it when it looked. didn't look in the right place obviously. thanks for the reply.

---

