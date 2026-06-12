---
title: "Network file browser slow now for some reason"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by belboz on 2008-02-24
For a couple weeks now when going to Places/Network on my Ubuntu 7.10 (32bit) system the network file browser comes up but shows no found network devices for a minute or so.

It use to immediately pop up and show three things.  

It would show two macs running Tiger with secure login services enabled (so my Ubuntu system sees them as secure ftp servers).

It also shows a third item for my Windows network group name.

For some reason now when I click on places/network it brings up the file browser but takes a minute to show the above three items.

I suspect it is something Windows share because if I double click on "Windows Network" it shows my workgroup name, and when I double click on that it pauses for about the same time as noted above and then errors out with "the folder contents could not be displayed".  

I have a few windows machines, and one Ubuntu server running some samba shares.  This server is not the same Ubuntu box I am doing the file browser above on.

I can do a connect to server, select windows share and put in the IP of my Ubuntu server running samba and it connects immediately.

Likewise the Mac's running the secure server connect immediately when their icons are double clicked on.

I am "guessing" this initial delay I am seeing is due to the Windows shares Ubuntu is trying to discover (along with the mac ones) when I click on Places/Network.  

It use to work great, so I am stumped on what to do, and would love any advice or help.

Thanks in advance.

---

### Post by belboz on 2008-02-24
I noticed on my Mac boxes if I run smbtree -N I get information for two PC's on my network with shares.

One being an XP machine, the other being the Ubuntu with the samba server.

smbtree lists both machines and shares available on them.

When I run the same command on my Ubuntu desktop machine it lists seeing the two machines but when it tries to connect to show the various shares it is generating timeouts connecting to an external IP that seems to resolve to my ISP.

Each share timeouts twice trying to connect to my ISP (one time on port 445, the other on 139).

My mac and Ubuntu desktop are both on the same subnet, and both have the same DNS server (which is a linux firewall running smoothwall)

This has to be why I am seeing the delays mentioned in my first message, just not sure what is going on.

---

