---
title: "NIC problem."
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by MillDoGG on 2007-07-29
I am running ubuntu 7.04. I have a wireless PCI card and a wired PCI as well. Right now I am only allowed to use one at a time. i.e I can only use the wireless connection, or the wired connection.

I am connecting to the internet via my wireless NIC. I would like to also connect to a home LAN that can share this internet connection via CAT-5.  When it is connect to the wireless network and I click to select the wired connection as well, it will disconnect from the wireless connection and connect to the wired network. Vice Versa. I am quite new to Linux OS and need a beginner guide to remedy this situation.

---

### Post by saxophobe on 2007-07-29
Hey MillDogg,

It sounds like you are doing some sort of Internet Connection Sharing......Not sure if a default config of Linux will do this.  I'm also not sure why you would want to, but to each their own. 

So you can connect use your wireless connection, or your wired connection, and you want to share the connection?!?!?!  It sounds like you might need a router to give you >1 wired connection to the Internet.  Ubuntu works very well with DHCP on wired connections.  And if you already have a wireless setup, you've done most of the hard stuff.

I apologize if I'm not understanding what you are trying to do.  Please post back and let me know.

Hope this helps!

sax

---

### Post by MillDoGG on 2007-07-29
Sax,

My desktop is connected to the internet through my wireless NIC. I would like to also connect to other computers on my home LAN via a wired router. In turn the other PCs can access the internet through my main Desktop. Any clearer?

And to reiterate I can only select one or the other, not both.

---

### Post by saxophobe on 2007-07-29
Dude, I'm trying to help.....

Again, I'm sorry if I'm misunderstanding.  Please be polite when responding.

As far as getting both NICs to work at the same time, I'm not sure why they wouldn't.  If they both work at the same time under Windows, it sounds like a driver problem.  I would start by looking at the compatibility list for your NICs.

So you want to be able for your other systems to connect to shares on your Linux system, but it sounds like you have a weird network architecture.  Something like this:


Internet - Modem/DSL/Cable - wireless connection > Linux system
                                                                                                          |
                                                                                                          |
                                                                                                   Wired Router
                                                                                                          |
                                                                                                          |
                                                                                                Other Systems

Ideally, it should be something like this:


Internet - Modem/DSL/Cable - Wireless Router - All systems with NFS/NTFS shares setup


In order to get your Ubuntu system to read/write on Windows systems, you will need to setup Samba shares, or use a tool that will do it for you, like Automatix2, which has tool that will mount and read/write NTFS/FAT32 partitions.  It has all sorts of other cool tools as well.

Again, I hope this helps!

sax

---

### Post by MillDoGG on 2007-07-30
Sax,

I was not trying to be rude. I apologize if I came off that way. I just did some research and discovered the Network Manager is designed to use only one. Not sure why they would want to do that. I would like to try and install a different network manager, just lost on how to do such a thing. Can you assist me on removing the standard issue one and pick a different one.

My setup is:

(-)))))) PC-----Router======PC---PC
^^^
Hot-Spot

I live on a boat and the only way for internet is WI-FI. I just don't want to spend the extra money to by individual Wi-Fi adapters, besides I also want my boxs networked for file sharing.

---

### Post by saxophobe on 2007-07-30
MillDoGG,

After doing some research, I found a network manager called Wicd, which says it supports wired networks, as well as wireless, but I don't know if that means that it does both at the same time.  Here is the link to the sourceforge project:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I hope this helps!  Please reply with results so that you may help someone else.

sax

---

