---
title: "Joining MS Windows network"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by danwizard208 on 2008-05-20
I recently installed Ubuntu 8.04 Hardy on my Acer Travelmate 4021, and am in the midst of configuring it.

My current configuration problem is this:
As soon as I got connected to my router and the internet (which was almost instantly, because of lots experience dealing with network configs on windows), I managed to mount, and view a preexisting windows network (still 3 computers in my house that run windows), as well as manipulate files there in every way. However I just noticed today (as part of an Issue getting Warcraft 3 lan games on WINE) that my Ubuntu machine is not listed in the windows network and cannot be accessed from the windows XP computers. I apparently have samba preinstalled, and I've been googling around trying to see if anyone else has been having my problem, and found some instructions to do the following:

edit the /etc/samba/smb.conf file, and set the following lines:
workgroup = RESNICK (my windows network workgroup name)
security = domain

then run the command: net join -w RESNICK

however I still am not part of the windows workgroup...
:confused:
Any suggestions are welcome!

---

### Post by Garmuar on 2008-05-20
This isn't going to help much, but I do know that the windows machines use NETBIOS  to "see" each other in workgroups and on LANs, and Linux doesn't use NETBIOS. So even if all machines were talking, you would see the ubuntu machine in My network places. 

This probably isn't your main goal, but when it comes to creating spur of the moment "LAN party" networks, I use Hamatchi to create a vertual lan and then all network problems instantly solved.

---

### Post by jimv on 2008-05-20
I just did some testing on my home network, and my linux server didn't show up to the windows boxes until I actually shared something.

---

### Post by danwizard208 on 2008-05-20
I managed to get my computer seen (turns out samba was only partly installed or something, because by sharing a folder, suggested by jimv thanks, it told me that i didn't have sharing software installed, and let me install samba), though now it won't let me access it (won't even give me a logon...)
Trying to fix that now, thanks for your help...

More suggestions appreciated!

---

### Post by danwizard208 on 2008-05-21
are bumps tolerated in these forums?

---

### Post by tact on 2008-05-21
> **danwizard208 said:**
> are bumps tolerated in these forums?

Hey there...  you have security=domain set in smb.conf.  Do you need that?  Do you have a domain set up on your home network?

To just peer share with other windows peers, just like windows machines all peer share (in workgroups rather than a domain) then you should have security=share

Of course "security=share" brings with it the lower security as well as ease of sharing that windows<>windows machines experience.  So perhaps (if you can tolerate having to enter passwords and setting up accounts for remote users of shares) it is better to have security=user instead.

---

### Post by kismeras on 2008-06-20
Hey Guys, 

I'm trying to follow along, but it's not working. I think you are asking the same thing i want to know, but i am not sure. I don't know what Samba is and i'm very new to Linux/Ubuntu. 

My goal is to connect to my windows network so that i can get files from my windows PCs as well as share files from my Ubuntu laptop and use the printer that is shared on one of my windows PCs. Can you guys help with this? Also i am very new so i might need a little (read as tons of) help with terminal and stuff like that. Thanks.

---

### Post by kismeras on 2008-06-23
Anyone?

---

### Post by Iowan on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by kismeras on 2008-06-23
@ Iowan, 

Thanks. I saw that post before and followed the instructions. My problem is that Windows can see the Ubuntu shares. However, Ubuntu can see the windows computers on the network, but it can not see the files that are being shared. If i enable simple file sharing in windows, then it works. However, i don't want to use simple file sharing. Anyone seen this before? Thanks.

---

### Post by jetsam on 2008-06-24
I think it's a known bug that you have, discussed in this thread (and some others):
[can't see windows shares in nautilus]("http://ubuntuforums.org/showthread.php?t=762525")
and this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072")

The title of the bug report makes it sound like it's only restricted to active directory domains, but I think it applies to all Windows based password protected shares.

The easiest workaround is to type:
```
smb://[COLOR="RoyalBlue"]server[/COLOR]/[COLOR="RoyalBlue"]share_name[/COLOR]
```
into the location bar in Nautilus.  This seems to let people enter a password and browse their shares one by one.

There hasn't really been a full solution for people.  It looks in the bug report like they're working on a fix, but might or might not make the 8.0.4.1 release.

---

### Post by kismeras on 2008-06-24
@jetsam

:guitar: Thanks a million. That absolutely worked. I've been rackin my brain for the last 3 days trying to figure this out. \\:D/

---

### Post by theDaveTheRave on 2009-01-29
Hi all,

I have a curiosity.

I have no problems in accessing any share on any pc. however 2 things are odd about the network.

On all the windows pc's only the other windows pc's are viewable (I guess this is the "netbois" mentioned by Garmuar. If I set up an LDAP will this solve my problem, as all the terminals will be demanding an IP from the same server, that I will have control over.

Also, the terminals all run with a static IP address. but the windows pc's have a netmask of 225.225.225.0 and the linux terminals have 225.225.225.128 which I haven't been able to explain.

Again will setting up an LDAP solve these problems, and if so can I use LDAP to give specified IP address to specified MAC addresses?? Especially as I have recently discovered that you can get the mac address of the pc you are pinging with the use of nmap.

why not try it on the nmap server (this is lifted from the nmap man page)....
```

 sudo nmap -A -T4 scanme.nmap.org 205.217.153.62

```

interesting tool I think.

David

---

