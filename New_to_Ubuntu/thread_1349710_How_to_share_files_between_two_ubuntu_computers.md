---
title: "How to share files between two ubuntu computers"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by BT1 on 2009-12-08
Sorry about making a different thread than my last post.

How do you share files between two Ubuntu puters on a network. Like for instance, if I was doing a remote desktop connection, how can I transfer a file to the remote desktop computer?

If I need to set up a FTP between two ubuntu computers, can you give me a quick tutorial on how to do it or point me to one?

---

### Post by WitchCraft on 2009-12-08
> **BT1 said:**
> Sorry about making a different thread than my last post.

How do you share files between two Ubuntu puters on a network. Like for instance, if I was doing a remote desktop connection, how can I transfer a file to the remote desktop computer?

If I need to set up a FTP between two ubuntu computers, can you give me a quick tutorial on how to do it or point me to one?

You can setup ssh and transfer the file via scp, or just use sshfs.

---

### Post by wsims2 on 2009-12-08
If they are on the same LAN, i would use NFS.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by CaptainMark on 2009-12-08
When i was on windows it was as easy having two computers on the same LAN, and clicking on a folder you wanted to share and set its properties to 'share on network'. Is there an Ubuntu way that is as easy as this, bearing in mind i dont understand what FTP or SSHFS means.  I think windows way is less customisable but easier if you dont know exactly what your doing. 

Ps. I havent had two Ubuntu computers to attempt to network before, hence to noobishness on this topic.

---

### Post by bodhi.zazen on 2009-12-08
> **BT1 said:**
> Sorry about making a different thread than my last post.

How do you share files between two Ubuntu puters on a network. Like for instance, if I was doing a remote desktop connection, how can I transfer a file to the remote desktop computer?

If I need to set up a FTP between two ubuntu computers, can you give me a quick tutorial on how to do it or point me to one?

IMO, on your LAN you can use Samba, NFS, and FTP.

ssh (scp) also works, sshfs is nice, I use ssh (scp) and sshfs if I need to transfer over untrusted networks (internet).

---

### Post by Maheriano on 2009-12-08
If you don't have it figured out by the time I get home, I'll write up a tutorial for you. But there's 2 ways to do it:
1. Go to Places - Network and it should list all the computers on your local network.
2. If they're not on the same network, get the IP address for the computer you want to connect to and go to Places - Connect To Server and put in the IP. You'll need to connect with the username/password of that machine and you'll be connecting via SSH over port 22, and your home directory will be /.

---

### Post by BT1 on 2009-12-08
> **CaptainMark said:**
> When i was on windows it was as easy having two computers on the same LAN, and clicking on a folder you wanted to share and set its properties to 'share on network'. Is there an Ubuntu way that is as easy as this, bearing in mind i dont understand what FTP or SSHFS means.  I think windows way is less customisable but easier if you dont know exactly what your doing. 

Ps. I havent had two Ubuntu computers to attempt to network before, hence to noobishness on this topic.

Yeah...similar experience. It seems with Ubuntu you have to use a program? I'm still new to Linux and as far as I've read of stuff like "ssh" is "secure shell" definitions, and never anything about programs. Yes, I have a "introduction to ubuntu 9.04" book lol.

It seems complicated, but I'm sure we'll figure this out. :D

Just so you gurus know... stuff like:

> 
"IMO, on your LAN you can use Samba, NFS, and FTP.

ssh (scp) also works, sshfs is nice, I use ssh (scp) and sshfs if I need to transfer over untrusted networks (internet)."and

> You can setup ssh and transfer the file via scp, or just use sshfs.     Is alien language talk to me even though I've been a serious windows user since windows 3.1, meaning I have tech experience with the windows side of this issue. That's not to brag, and not to brag when I say I've set up networks with "ezMode"
 type network managers, but Linux is another world. In the future, you could say something like...
> 
"You could use SSH/SCP/SSHFS which is a [program/system] that does: _____, which you can find at the location I usually download it at: _____"That is NOT to insult those helping, just saying that for the "Absolute Beginner" part of the forums, it's helpful to give that extra 10% to educate people like me who are now Linux users for life and seeking to learn. :) You can believe that once I become even a modest Ubuntu linux user, I'm going to dedicate at least 2 hours a day to answering what questions in this part of the forum that I can as well as writing vast numbers of tutorials and tip articles (I LOVE doing those and did it a LOT when trying to help people with "Windows Woes"). So the faster I learn what you gurus know, the faster I can pass it on to those in the dark!

Thanks so far for the help!!!!!!!!!!! :)

---

### Post by bodhi.zazen on 2009-12-08
If you are new to Ubuntu , I suggest Samba, it should work out of the box.

You will need to set one of the ubuntu boxes as the server, the other is the client.

[https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Graphical%20Configuration)

---

### Post by 3rdalbum on 2009-12-08
Install the system-config-samba package. This adds a "Samba" menu item to System > Administration.

Create a new user account on your Ubuntu system that has the same username and password as your Windows system, and then go into System > Administration > Samba and create it as a new Samba user. Tell it what folders you want to share and what users can access it.

Reboot the Windows client and your new share will be available in the usual place.

---

### Post by BT1 on 2009-12-09
Problem solved. Once again the gurus save the day!

---

