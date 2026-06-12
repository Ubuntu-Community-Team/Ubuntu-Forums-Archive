---
title: "A big stupid mistake! with ebox, and networking help wouldbe appreciated."
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by gkffjcs on 2008-03-25
I have a system in a remote location (home, I am a student at university) , I use as a personal file server.  I have therefore only ssh access.
  Background: 
        It has a 1.5ghs processor, 2.5 gigs of ram, one nic card, two harddisks, one is 20 gigs and has my root, partition, the other is 500gig, and is split into two partitions, one for files and one for vmware machines. On this system I have installed kubuntu gutsy, ssh, samba, and vmware server (free). In vmware I have xp pro running with remote desktop enabled.
What I did:
        I was anoyed with sshfs and wanted to use smb over secure vpn, so I wanted to try and install openvpn on my server/desktop. I had attempted to set it up using the terminal and several tutorials, and guides which didn't work. So I searched on apt for a ui for the admin side of the openvpn server setup and configuration and found ebox-openvpn. I expected that it would install a few packages related to openvpn, Instead as i found out later ebox is a massive remote admin suite, desighed to be installed on a dedicated box. ebox installed, but I noticed that my ssh session had completely died. I could no longer login. For some strange reason the remote desktop session in the windows vm was still functional. I was able to open up putty, and luckily for some reason I don't fully understand; when I tried to ssh in from putty in windows vmware/remote desktop session  I was seen as localhost and was allowed past the firewall. I have since read that ebox over writes many critical files in /etc/* At the time I initially tried to simply remove ebox using apt but that didn't work, I tried to reinstall it, but appearantly the computer no longer has any internet access at all. infact, aside from the strange fluke with being able to login to the winxp session nothing can get in or out, also the vm has no internet either. I cannot reinstall ebox, is there a way of restoring the net functionality of my system? Also I have iso's of the kubuntu live cd on the system, so I can loop mount them if needed, if they might help. Also if I had not made this specifically clear one of the ebox packages was a firewall. And clearly un installing it has not given be the ability to log back in. I believe it may have messed with my iprouting tables, but I am not sure, and that would only be a guess. There is absolutely no way I can get physical access to the box for several months.

---

### Post by SpaceTeddy on 2008-03-26
i have never heard of ebox before, but i think i won't touch it :)

anyways - have you checked your network devices, routing tables and iptables rules if there is anything in there that might block you. Also, at one point i was playing around with some software that hooked directly (!) into the network drivers, rendering them pretty much useless. 

but lets check your "normal" internet functions first... can you provide the output of
```
sudo iptables -L
route -n
ifconfig
```

which will show if there is something just blocked or misconfigured.

---

### Post by thavid on 2008-05-30
Hi there. I guess that happened because the ebox firewall package must blocked the 22 port. About the OpenVPN, I think that eBox works better with two NIC's, at least as a OpenVPN client (to do thing like, point to point tunneling). As a server I don't know, because for that I use another platform.

Anyway, about the eBox project, my advice is for you to test it, because it is very very worth it! Just follow the installation guide @ [http://ebox-platform.com/installation-guide](http://ebox-platform.com/installation-guide) and you'll have a full packed server working in no time! It works good for me, been following this project for years and have it running in a lot of locations with no stress at all.

---

