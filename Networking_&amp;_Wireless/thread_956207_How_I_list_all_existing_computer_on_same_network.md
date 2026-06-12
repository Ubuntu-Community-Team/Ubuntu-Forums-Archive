---
title: "How I list all existing computer on same network ?"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by MrWhisper on 2008-10-23
Today. I just connect my PC to a network  and all pc is running Ubuntu.

I want to list all computer that connected to this network (like My Network Place on Microsoft Windows)

How I do it ?

thank you.

---

### Post by kilroy423 on 2008-10-23
You can run a ping scan of your network.  This will tell you if there is a machine on an ip.  

> sudo apt-get install nmap
sudo nmap -sP your network ex:192.168.1.0/24

If you want to have like network places then you can go places>network

---

