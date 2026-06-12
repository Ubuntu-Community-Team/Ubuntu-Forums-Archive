---
title: "Intruder/ hacked machine"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by pius shililifa on 2011-09-01
Hi guys, 

I am new to the forum but not so new to ubuntu, I have been using ubuntu for about three years(GUI) not command line user. 

Recently i installed firestarter to give me a bit of piece of mind and i saw the same ip being blocked several times throughout the day, would therefore like to know how i can check if my machine is compromised and how to lock it down effectively.

Thanks

---

### Post by haqking on 2011-09-01
> **pius shililifa said:**
> Hi guys, 

I am new to the forum but not so new to ubuntu, I have been using ubuntu for about three years(GUI) not command line user. 

Recently i installed firestarter to give me a bit of piece of mind and i saw the same ip being blocked several times throughout the day, would therefore like to know how i can check if my machine is compromised and how to lock it down effectively.

Thanks

no ports are open by default.

Unless you open a service that is, so is already locked down.

firestarter (out of date) and UFW/GUFW are merely interfaces to the built in firewall which is IPTables/netfilter.

IPs try to connect all the time, they could be from your ISP, alot of comms outside require a connection back.

like you said it is blocked so why worry.

depends on the IP really and port they may be trying to connect to.

Also if you are behind a router it is protecting you also

---

### Post by pius shililifa on 2011-09-01
Noted haqking, any way of checking if there are any open ports that i might have opened when installing/activating services.am paranoid about security and need assurance that the machine is secure

---

### Post by haqking on 2011-09-01
> **pius shililifa said:**
> Noted haqking, any way of checking if there are any open ports that i might have opened when installing/activating services.am paranoid about security and need assurance that the machine is secure


scan it using NMAP or more simpler use

netstat -lp

---

### Post by spiky001 on 2011-09-01
[http://nmap-online.com/](http://nmap-online.com/)

---

### Post by haqking on 2011-09-01
> **spiky001 said:**
> [http://nmap-online.com/](http://nmap-online.com/)

that will scan the WAN IP which of course is the issue i think he has, but i think he is paranoid as he said and also wants to scan his actual machine.

---

### Post by Rex Bouwense on 2011-09-01
I think Gison Research has a web site where you can check how secure your machine is.

```
https://www.grc.com/x/ne.dll?bh0bkyd2
```

---

### Post by pius shililifa on 2011-09-01
thanks for the quick responses guys, tried the online tool and it returned a error saying that the host appears to be down.this is a bit of reassurance because it tells me that firestarter is doing the job. 

but would still like to know how to better protect the machine from intrusion, that is the reason i switched to linux from windows three years ago, got tired of patching and updating antivirus programmes(had about two running yet my machine was still taken down by a bad virus) want to have as secure a machine as possible.

---

### Post by Rex Bouwense on 2011-09-01
To ease your apprehension a little, a Linux OS such as Ubuntu has been described as a house with locked windows and locked doors.  The only way something can get in is for you to open one of those windows or doors and that requires your approval and authentication password.  Since there are less than 100 virus programs (none active that I know of) somebody must be doing a good job.

---

### Post by pgp_protector on 2011-09-01
> **pius shililifa said:**
> thanks for the quick responses guys, tried the online tool and it returned a error saying that the host appears to be down.this is a bit of reassurance because it tells me that firestarter is doing the job. 

but would still like to know how to better protect the machine from intrusion, that is the reason i switched to linux from windows three years ago, got tired of patching and updating antivirus programmes(had about two running yet my machine was still taken down by a bad virus)** want to have as secure a machine as possible.**

About the only way to be %100.00 secure is to unplug it & put it in a locked vault.

If you can connect to it, someone else can connect to it by doing what you do.

Example. I've got ports opened so I can run a web server or SSH into it.
Given that I can connect, anyone doing what I do can also connect by doing the same thing.

---

### Post by haqking on 2011-09-01
> **pius shililifa said:**
> thanks for the quick responses guys, tried the online tool and it returned a error saying that the host appears to be down.this is a bit of reassurance because it tells me that firestarter is doing the job. 

but would still like to know how to better protect the machine from intrusion, that is the reason i switched to linux from windows three years ago, got tired of patching and updating antivirus programmes(had about two running yet my machine was still taken down by a bad virus) want to have as secure a machine as possible.


like i said you are already secure as no ports are open by default.

to check to see if they are like i said

netstat -lp

this scans your actual linux machine, WAN ip or router can be scanned like you just did.

For more security then i suggest reading the following:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

from Bodhi, an admin on this forum.

for virus questions read the following:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by BlinkinCat on 2011-09-01
> **haqking said:**
> like i said you are already secure as no ports are open by default.

to check to see if they are like i said

netstat -lp

this scans your actual linux machine, WAN ip or router can be scanned like you just did.

For more security then i suggest reading the following:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

from Bodhi, an admin on this forum.

for virus questions read the following:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

As usual, you are a tireless worker haqking! - :P

---

### Post by pius shililifa on 2011-09-01
:-) thanks guys. have been completely reassured. Am asking myself why i never joined the forum ages ago. the security question is sorted. Am just interested to know how i can create a bootable image of my ubuntu machine now, a kind of ghost ubuntu style.

---

### Post by cariboo on 2011-09-01
> **pius shililifa said:**
> :-) thanks guys. have been completely reassured. Am asking myself why i never joined the forum ages ago. the security question is sorted. Am just interested to know how i can create a bootable image of my ubuntu machine now, a kind of ghost ubuntu style.

Try [Remastersys]("http://www.geekconnection.org/remastersys/")

BTW if you are worried about security, I'd worry about firestarter, as it hasn't been updated since 2005. Also runnig it as root to monitor connections could lead to security problems.

If you are truly worried about security, I'd suggest reading the security stickies in [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338")

---

### Post by BlinkinCat on 2011-09-01
Hi,

Might I suggest you open a new thread with a more apt Title - :P

Edit - cariboo907 may have answered your question -

---

### Post by David Andersson on 2011-09-01
As others have said, if you have not installed any http server, ftp server, ssh server or similar, you are very safe. Even if you have installed a server, the default settings are usually pretty safe.

But open ports is not the whole picture. Today one must be paranoid about the *web browser*. Someone might exploit a bug in the browser or in a plugin such as flash or java. They won't destroy your system, but they might compromise your documents, or intrude your privacy by peeking into cookies or clipboards. I don't know of any actual exploits, but I feel it's worth being paranoid about.

(If you want to be paranoid about *something*.)

---

### Post by 3rdalbum on 2011-09-01
You installed Firestarter to "give you some peace of mind" and the logging function had the opposite effect :-)  Always happens!

---

### Post by oldos2er on 2011-09-01
> **pius shililifa said:**
> would still like to know how to better protect the machine from intrusion

Have you read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) ?

---

### Post by sffvba[e0rt on 2011-09-01
> **haqking said:**
> no ports are open by default.

Hi,

I am sorry to hijack this thread but I just have a question... I have seen the above statement before here on UF... and it has always bothered me that if the above is true why would the default for ufw be disabled (yet iptables is already setup in the way described above).  So I have checked up on the status of iptables in Ubuntu and all I found this ([https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)) in which it states...

> When you install Ubuntu, iptables is there, but it allows all traffic by default.Anyone have a more definitive answer, because from what I can gather if ufw isn't enabled then your Ubuntu box isn't being secured via iptables?!


404

---

### Post by 3rdalbum on 2011-09-01
> **not found said:**
> Hi,

I am sorry to hijack this thread but I just have a question... I have seen the above statement before here on UF... and it has always bothered me that if the above is true why would the default for ufw be disabled

You're definitely getting confused.

Your computer isn't just listening to all 65,553 possible incoming ports at all times. You actually need a program to be listening for an incoming connection on a specific port, in order for the incoming connection to get through on that port.

By default, Ubuntu isn't running any programs that are listening to any incoming ports. If a remote computer tries to connect, the connection doesn't open because nothing is listening for the connection.

Or, in other words, a deaf man doesn't need earmuffs.

---

### Post by haqking on 2011-09-02
> **3rdalbum said:**
> 

Or, in other words, a deaf man doesn't need earmuffs.


LOL

but dont deaf people get cold ears then ? ;-)

but +1

Ports being closed has nothing to do with IPtables.  IT means no services are running with ports open.  Which is why when you start UFW (which is an interface to manage IPTables) you start it with a deny all.

---

### Post by sffvba[e0rt on 2011-09-02
Makes sense... thanks for the answers...


404

---

