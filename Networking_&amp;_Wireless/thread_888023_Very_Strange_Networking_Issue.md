---
title: "Very Strange Networking Issue"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Maahes on 2008-08-12
I have a particularly strange networking issue. Currently I am typing and working just fine (for this site anyways), from my linux laptop.

IRC works, Pidgin works, And much of the web works.

But certain websites seem to get stuck in endless connection loops, never time out, never display: Reddit, Stikcam, half the places digg links to, etc.

This only happens on my ubuntu laptop, the windows machines here work fine over the entirety of the network.

To note: There is a VPN on the network, but it's unused, to my knowledge. 
There's also active directory for many of the machines here. But I was able to take a windows machine not in the AD, and without any VPN credentials and it does just fine with the net (Actually, 10 XP machines I have been setting up, work just fine).

This is made more odd by the fact that I can *ping* Reddit, just fine. I've tried using different DNS addresses, and that is not the issue.

I am at a very big loss as to what might be the problem, and I have no idea what steps to take to even diagnose why these sites aren't loading for me.


A brief description of the network: DSL Modem in bridge mode, plugged into router in bridge mode, plugged into server that handles routing off to a switchboard. Windows server, obviously -_-


Okay, so I did get some help from a friend, and have some more information:

According to my friend: it seems that there is packet loss, and then windows blocks sufficiently enough information about the packet loss that linux never recovers, the windows machines are differently agressive about retransmits, I tried lowering my MTU threshold but notta, anyone have any idea of how to make linux "stupid compatible" in this instance? She described the windows machines as being "Stupid in a compatible way".

---

### Post by Maahes on 2008-08-12
Just a bump, since I have more information regarding the issue.

---

### Post by Maahes on 2008-08-21
just another bump, as my issue is still unresolved.

---

### Post by wmdiem on 2008-08-21
If it's packet loss wouldn't ping show that?

---

