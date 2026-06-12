---
title: "Ubuntu server and ubuntu desktop cant talk to eachother"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by jperz09 on 2011-04-23
I've got ubuntu 10.10 loaded on my actual PC, and I'm still pretty new with it. On the same PC I'm running virtualbox that's running ubuntu server 10.04. I'm just messing around with it, finding out that its pretty cool, and easy to use. But anyhow, I set the virtual server up as a simple samba file server, and my Windows Vista PC sees the server just fine, and can save files to it, and I can ping the server using its name. But when I try to access the file server from my ubuntu machine, again which the virtual server is running on, ubuntu says its an unknown host. I can ping it using the IP address, but if I try and ping it using the server's name, I get another unknown host error message. Also when i try and ping my ubuntu desktop from my ubuntu server, it only pings successful if I use the IP address. And on my ubuntu desktop, when I go to Places>Network all I see is Windows Network, and the ubuntu server isn't in there either. I figured it would most definitely show up on the ubuntu desktop network. Not sure what I'm doing wrong, or missing.
     Now I've tried a few things. I made sure samba was installed on the ubuntu desktop PC. I've made sure that all PCs and the virtual server are using the same DNS name servers. I've made sure that everyone is on the same workgroup. I'm sure there was a couple other things I tried, but it was like 2 in the morning when i was messing with it last night.
     But anyways, any help would be awesome! Thanks! And by the way, if you guys need any extra info, let me know.

---

### Post by JKyleOKC on 2011-04-23
When you can ping by IP address but not by name, that's clear-cut evidence that the name in question is not in the DNS server you are using. None of your local computer names will be in your ISP's DNS server, so unless you are running your own DNS server it's pointless to expect to be able to connect by name. The workaround is to add the name and IP of each machine to the /etc/hosts file, on each machine; this was what everyone had to do before DNS was invented!

To see a Ubuntu box from a Windows machine, or in the Windows Network dialogs of another Ubuntu machine, the box in question must be running a Samba server in addition to the default Samba client. To see a guest system from its host when VMs are in use, the guests must be on the same subnet. The default setup for VirtualBox uses NAT for its virtual network adapter, putting it on a different subnet from its host. The cure here is to switch the network adapter setting of the VM to "bridged" and assign it a unique IP on the same subnet as the host; they will then be able to see each other.

Hope this helps!

---

### Post by jperz09 on 2011-04-23
Thanks for the quick reply! I added my ubuntu desktop to the server's host file, and vice versa on my desktop's file, and now they can talk via ping but I still can't see the server on my ubuntu desktop network. I guess i should have been more clear. In my mind, and maybe this is because I work with Windows all day long at work, but shouldn't the ubuntu desktop, and ubuntu server automatically see each other? Like when I go to Places>Network, I figured the server would be in there, before I even click on Windows Network. I lol But hey, like I said, I'm pretty new with Linux, so I could totally have my head up my a$$, lol. And that's exactly why I'm reaching out to you guys! Also changed the network settings in vbox a while ago, because i  noticed the IP address was 10.0.0.25, and that's def not my network IP  scheme!! lol Also, side note, when i edited the hosts file, when I was finished, it said 1 more file to edit, what did I miss?

---

### Post by JKyleOKC on 2011-04-23
Your conclusion is pretty logical, but there's one major point of which you may well not yet be aware: the automatic detection of network machines that Windows does depends on Microsoft's "netbios" protocols, which are not part of the standard networking traffic that Unix machines use.

That's what Samba does: it emulates the Microsoft netbios layer so that Linux and Windows machines can communicate with each other. However since Microsoft has never published the details of netbios, Samba is based on reverse-engineering and does not always act exactly the same as the Microsoft routines. For that matter, Windows itself does not act exactly the same from one version to the next. Win98SE does not communicate well with WinXP Pro, at least it would not for me when most of my machines were Win98SE.

The Samba suite is split into a number of parts. The most significant division for your current situation is that it has separate programs for the client and the server. Ubuntu installs the client package by default, so that a Ubuntu box can see and read from Windows boxes in the same workgroup, but does not install the server package -- and the server package is required for Windows boxes to communicate with the Ubuntu box.

Getting Samba configured properly can be quite confusing, although it's much easier now than it was a few years back when I was converting my home-office LAN from Win98 to Xubuntu. I found it necessary to buy a book, "Using Samba," and study it closely, in order to even get started. Even so, I could never get WinXP Pro boxes to communicate with my Linux-based LAN. Still can't get them to work directly, but they CAN communicate with XP Pro VMs running on Linux hosts so when needed, I do two-step transfers...

The central control point for Samba is the /etc/samba/smb.conf file; the default one is commented extensively to tell you what most of the content means. If you make any changes, though, be sure to run "testparm" from a terminal afterward. This will verify that the file is still acceptable to the samba programs, and can prevent total foul-ups.

I'm not sure what that "one more file to edit" message meant. Since I run Xubuntu rather than the main Ubuntu version (same kernel but different window manager and some different utilities) I edit with mousepad instead of gedit, and have never seen such a message appear.

EDIT: Samba isn't necessary for getting one Ubuntu box to talk to another; for this case the solution is NFS or Network File System. It's a bit involved to set up initially but once set becomes automatic. Search the "Tips and Tutorials" forum for "NFS" to locate tutorials on setting it up. You can then make each box see everything on the other, or restrict them to only a few directories, as you prefer...

---

### Post by jperz09 on 2011-04-23
well I solved the mystery haha...a couple days ago I was messing around with the linux firewall and I enabled it. So I disabled the firewall, and what do ya know? there's my ubuntusrvr in my network. Thank you so much for all you're help, this def won't be the last time you see me post...Thanks again! Linux reminds me why I got into the Information Tech field in the first place, I love it.

---

### Post by v1ad on 2011-04-23
quick question. can't we add the ip of the Ubuntu Server to the windows hosts file and not use samba? or does windows require netbios.

---

### Post by JKyleOKC on 2011-04-23
I believe that Windows requires netbios, but I might be wrong about that. None of the machines on my LAN boot to Windows any more; all of my Windows requirements are met through virtualization. The VMs can see each other in "My Network Places" but do not see the Linux hosts.

---

