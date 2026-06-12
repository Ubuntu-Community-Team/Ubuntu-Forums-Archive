---
title: "Can't acces my Windows laptop  from my Ubuntu 8.04 PC"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by _Ichigo_ on 2008-05-21
Hi. Maybe this has been posted somewhere else already but I have to see if anyone can help me.

I have my Ubuntu 8.04 (Hardy) installed in my XPS410 machine and runs very smoothly and nice. I also have a laptop with Windows XP Service Pack 2.

Well the other night I was trying to connect both of 'em over my network (I have a netgear router which I use to connect all the computers in my house to the internet). Well I installed samba and everthing when nice, and I also installed smbfs and smbclient. There after I configured Windows XP to share some folders over the network.

Well to make the story some short. I can see my Ubuntu PC from Windows XP and access the folders that I want and everything (of course  it asks me for password and username). But on the ubuntu side it only shows the XP computer. And when I try to access the folders and files it doesn't display anything like if there nothing to share. 

I've double check the security of my Windows machine and share properties and even turned off the firewall without any kind of success. Plz can anyone help in this matter  :( . Thx...


(Thx to all of you guys that make programming a lot more interesting with LINUX);)

---

### Post by bluefrog on 2008-05-22
this is a windows forum question but well...

I assume that as most windows user you are misbehaving with your OS and use it as administrator and without a password.

So, to begin with, set a password up to your administrator and then, from your ubuntu pc, open nautilus (file explorer), make the address bar appear (little icon on the left of the location bar) and write

smb://xp-IP/c$

<enter>

If you are not prompted for your windows administrator name and password, then it is definitely a windows problem.
If this works carry on with your normal shares (you may have to redo them)

(on the side, add a restricted user to your xp machine and log in with that one, then to install a program use "run as" (sudo equivalent))

---

### Post by mapes12 on 2008-05-22
I couldn't get sharing to work at all across my home LAN therefore I gave up on network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier. There are utilities to connect XP and Ubuntu boxes via this protocol.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

