---
title: "Best remote desktop server?"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by 1clue on 2014-03-11
Hi.

I've been using ssh -X <hostname> to get UI access to a remote system.  It's slow.

So with that in mind, I'm looking to change my approach.  Here are the requirements:
[LIST=1]
[*]Fast.
[*]Multi-user, multi-connection. (not just sharing a console)
[*]Standard cross-platform client.
[*]Stable.
[*]Starts as a service.
[*]Encrypted.
[/LIST]

I've never done this before, looking for the best product.

---

### Post by TheFu on 2014-03-11
"product" implies a budget - if you have $5K, there are lots of choices.

However, I like FreeNX with any NX client.  Google "ubuntu freenx" for a guide AND follow it CLOSELY. There are manual steps. This is a remote desktop that works around the world. It uses key-based ssh connections. I've used it from 4 other continents when ssh just wasn't enough.

I don't know what you mean by "cross platform client" - there are NX clients for Linux and Windows. I hear the OSX one is buggy, but don't have any first-hand knowledge. NoMachine is working on the Android version ... I couldn't get it to connect to any of my FreeNX servers. There are separate x32 and x64 clients, so be certain to get the correct one.

Oh and FreeNX meets your 6 things - for certain values of "fast" and depending on what you need by "cross-platform" and "standard." ;)  Clearly, the connectivity involved will have _some small impact_, right?

In the future, Spice might be viable.  It is part of the KVM virtualization packages - don't know if it works directly on real hardware.

---

### Post by QIII on 2014-03-11
NoMachine 4.0 now has a Windows server (as well as a client), but it does not use SSH.

I use it to remote to my Win 7 Pro machine ... but mind your firewall even behind your router, I think.

I remote to my other Linux machines with NoMachine.  Be sure you DON'T use passwords with SSH, but keys.

The personal use version of NoMachine is free (but not open source -- they went closed source for 4.0).  They make their money on corporate contracts.  

FreeNX is code from about 2008 and is not under current development.

NeatX from Google was never "released" as it was an internal project, but the source code is available if you want to try to compile it.

X2Go doesn't work with other NX implementations as far as I know.

I was never very impressed with remmina or KRDC and the like.

---

### Post by 1clue on 2014-03-13
"product" means something that was produced.  It's the result of directed effort.  With or without a budget, but definitely without a large budget.

A Mac workstation will definitely be necessary.

Thanks, lots of names to go look at.

---

