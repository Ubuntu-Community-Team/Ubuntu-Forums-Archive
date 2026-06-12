---
title: "Networking to allow VNC access to Windows XP running in KVM"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by jdpipe on 2007-07-26
I have got KVM running on my Ubuntu 7.04 box and have installed a virtual Windows XP system on there. It runs fine and can access the network.

The VNC client built into KVM does not seem to be very bandwidth-efficient so I have installed TightVNC in my virtual Windows system, and I would like to be able to connect to that somehow from outside the office.

Is it really necessary to set up a 'bridged' connection, as suggested in the KVM documentation on the Ubuntu Wiki? It's a bit scary. Are there other options, such as perhaps some simple kind of port forwarding or the kind I am familiar with using SSH?

I was vaguely hoping for something like...

[john@home] $ ssh office.example.com
[john@office] $ kvm -vnc :2 -net socket,L5901:localhost:5901 windows.img &

another window:
[john@home] $ ssh -L5999:localhost:5999 [email]john@office.example.com[/email]

another window:
[john@home] $ vncviewer -encodings "tight copyrect" :99

Is there any technique that lets me do things a bit like that?

Cheers
JP

---

### Post by jdpipe on 2008-05-30
To answer my own question:
[http://ascendwiki.cheme.cmu.edu/Remote_Virtual_Windows](http://ascendwiki.cheme.cmu.edu/Remote_Virtual_Windows)

---

