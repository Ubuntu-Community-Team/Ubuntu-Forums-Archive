---
title: "bluetooth obexfs and gnome-vfs-obexftp with amarok - sony z610i phone"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by shaunbarlow on 2007-08-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/135812](https://bugs.launchpad.net/bugs/135812) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all,
Let me start this post by outlining my goal (in case someone else has a better way to do it)
I'd like to connect my sony ericsson Z610i via bluetooth as a "generic media player" in amarok.

I've got all but there with a number of methods and have learnt a heap in my tinkering.

Here are my problems:

1. I've followed a tutorial here: [http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html](http://davesource.com/Solutions/20070520.T-Mobile-Nokia-E65-Ubuntu-Linux.html)
and got everything functioning as described, except that when I try and copy files to the phone I get a dialogue that says "There is not enough space on the destination." The status bar in nautilus also reports "6 items, Free space: 0 bytes" 
There was an identical bug that was resolved in gnome-vfs-obexftp to be found here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-vfs-obexftp/+bug/120214](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs-obexftp/+bug/120214)
I've posted a bug for obexfs outlining this here: [https://bugs.launchpad.net/bugs/135812](https://bugs.launchpad.net/bugs/135812) but there's no subscribers. SO if anyone knows how to fix this, please help me out.

2. gnome-vfs-obexftp-0.4 also looked like a promising way to get amarok and my phone talking. The "no free space" issue had already been resolved in the bug mentioned above. However, I can't find anyway to point amarok to the obex://[xx:xx:xx:...] address.

If I type the obex:// address as the mount point for a generic media device then amarok says "malformed url" 
Please let me know if there is a way to get amarok to recognise the obex:/... address or a way to mount the obex://... address to a local mount point.

This is a very long winded post, and I guess it could be broken into a few separate posts, but these are all options towards achieving the one goal, so I figure it's ok as is.

Any suggestions, advice, help welcome.
Thanks in advance.
Cheers to all!!!
Shaun

---

### Post by shaunbarlow on 2007-09-02
Does anyone have any ideas? Anyway I can get obexfs to recognise that my phone has available free space?

Please help!?!?!?

---

