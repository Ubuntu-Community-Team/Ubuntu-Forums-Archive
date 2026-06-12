---
title: "switched to ubuntu - now linux boxes can't see each other"
date: 2005-07-19
forum: Networking &amp; Wireless
---

### Post by arjay1 on 2005-07-19
Hi all - switched from mepis to ubuntu and pleased I did  .... except for one big problem.

I have a three computer network - two linux boxes wired by ethernet and a Win XP laptop connected by wireless.  All three connect to the internet through a router.

Mepis automatically set up the new network including finding and organising the shares etc.  About the only thing it did well.

When I switched to ubuntu, both linux boxes refused to see each other.  Indeed i can't even ping either way.  Strangely enough, they can both see the Win XP shares through samba.  I am sure it can't be hardware related as everything worked fine under mepis.

I presume that it is something to do with the iptables which I just don't understand at all.  I have read a load of stuff on it and am still none the wiser.  I installed firestarter and set up polices to allow connection from hosts for the ip addresses for the three computers but that has achieved SFA.

I remember a while back in Fedora I had to open a couple of ports but don't remember which ones.

Could someone give me a steer?  I'll provide further info if asked.

TIA

BTW - 

1.  connection to the internet is fine from all three boxes
2.  I haven't set up samba shares between the two linux boxes - I thought that I only did this for Windows?  I want both linux boxes to be able to see and share ALL folders - if possible?

---

### Post by cwaldbieser on 2005-07-19
Could you post the output of:

$ ifconfig
$ route

for your Ubuntu machines and

C:\> ipconfig
C:\> route print

for your Windows machine?  Also, can you describe the physical connections?  Are you using dynamic or static IP addresses?

Unless you installed a firewall, it is probably not iptables / netfilter.

---

### Post by arjay1 on 2005-07-20
Sorry for not replying earlier, and thanks for coming to my aid.  I had done the ipconfig thing on windows but had forgotten that it was ifconfig not ipconfig  in linux.  So I was working pretty blind.  With your help I have been able to make some progress and can now ping every machine from the other and win xp can see one linux machine, after I made some changes to the smb.conf file.  I'll copy it to the other linux machine and hopefully they will at least all see xp shares.

However, my question  to you never really got anwsered in that - if I have, say,  - just two linux machines on a network - do I need to set up shares in the smb.conf file?  I thought samba was just for linux/windows sharing? 

 I would have thought that if I opened a port or two somewhere, or gave permissions somewhere for the network ip address and/or the ip address for each machine, then linux boxes should be able to share files etc without any further changes.  Is this correct?

Thanks again

Richard

---

### Post by cwaldbieser on 2005-07-20
Linux systems can share files many different ways over a network.  They include (but are not limited to):

+ SMB (Windows) shares
+ NFS (Network File System) shares
+ FTP
+ SCP
+ HTTP

If you just want to do Linux to Linux file sharing, you probably want to use NFS.

---

### Post by arjay1 on 2005-07-21
Thanks for the info - I am tied up with some other stuff right now but have not yet goteverything working so, if I may, I'll come back to you for more help after I have had a chance to do battle with samba and the rest!  may be a day or so.

Cheers

Richard

---

