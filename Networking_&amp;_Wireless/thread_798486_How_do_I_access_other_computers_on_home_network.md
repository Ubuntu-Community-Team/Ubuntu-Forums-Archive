---
title: "How do I access other computers on home network?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by deleyd on 2008-05-18
I can connect to the internet. Now how do I connect to other computers on my home network? (How can I see and share files over my home network to my other home computers (which all run Windows))?

---

### Post by logx on 2008-05-18
Hello,

I actually was looking for this myself!

I think you first need to be in the same domain as the rest of the hosts.
Once this is done, you should check the host name of the computer you want to connect to and then use a tool such as Remote Desktop Viewer.

But I'm not quite sure you can do this with hosts running in different os's. Normally it should since the protocols etc are standars, but I'm really not sure.

Anyway, I tried to do this myself but is not as easy to just check in your 192.168.1.1 the IP of the other unit and connect!

Anybody has already try this or at least is sure of how it works?

---

### Post by SpaceTeddy on 2008-05-18
you can access any windows machine that has shares always through it's ip. For that, open nautilus (that is the filebrowser) and simply type in
```
smb://ip
``` where ip is the ip-address of the remote computer. 

However, this requires knowledge of the IP of the other computer. I *think* i know what to do to get the Places -> network button working, but i am far from sure about that :( So, if anyone knows how to acctually get this working properly, please post it. 
I only have linux machines and mainly use sshfs - i would not know how to do the smbbrowsing of machines :) sorry... 

hope it helps :)

---

### Post by Iowan on 2008-05-19
Check post #6 [here]("http://ubuntuforums.org/showthread.php?t=789444") for some file sharing info.  There's also this [Samba  HowTo]("http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer")

---

### Post by Zigzag Lampie on 2009-08-18
I am a complete linux newbie running ubuntu 9.04. I have several windows XP machines and a Freecom Netdrive pro 500 running via a router. I spend ages searching forums to find out why I was seeing Windows Network on my ubuntu computer, but was unable to 'mount the share' and see anything on the network. 

The problem was the firewall settings (which I had forgotten about completely). I went to system / administration / Firewall configuration. When the firewall box popped up, I selected'allow incoming traffic', then on the advanced tabwhere it says 'From Any & To Any', entered the lower and upper IP addresses of the range used by my home network.

Bingo - all the shared files on the XP computers are now accessible. The netdrive isn't but I expect I will need to change my ubuntu login password to match the netdrive password first.

Hope this helps someone, as in spite of all the posts on the forums I've read, I still had to stumble across it myself. RULE 1 - assume nobody knows anything to start with then you will only be pleasantly surprised later.

---

