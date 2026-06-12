---
title: "Samba problems (can't see computers in gnome)"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by justinleewilson on 2007-11-27
Hi all :-)

I've got a problem networking my 2 gutsy PCs together using samba. 

Background:
I have a laptop which dual boots windows and gutsy and a desktop pc, also running gutsy, which I intend on using as a file server. I've installed samba on both gutsy instances and set a share named media on my desktop pc.

My Problem:
When browsing through gnome Places->Network I can't see any of my computers, not even the local computer (in both gutsy instances). However if I restart my laptop and boot into windows and browse to the Network on my desktop pc I can now see both my laptop and the local computer.
I tried connecting through the terminal on my laptop (gutsy) using the command smbclient //orion/media where orion is my file server and media is a shared folder, and it connected perfectly i.e I could browse the media folder. This suggests to me that smb is working fine!

Please help

Justin

---

### Post by michaelzap on 2007-11-27
I've had a similar problem since Feisty. If you have Firestarter installed, try stopping it and then trying to connect to your shares. I've always been able to get samba working after tweaking (or stopping) Firestarter.

---

### Post by justinleewilson on 2007-11-27
Hey,

I don't have firestarter installed :-) I have noticed since my original post that once I've connected to my samba share though the terminal the computer names appear in the Network place in gnome.

Anybody have any other ideas?

---

