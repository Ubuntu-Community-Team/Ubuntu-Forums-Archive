---
title: "ftp server &amp; security n00b questions"
date: 2004-12-21
forum: Networking &amp; Wireless
---

### Post by negativ on 2004-12-21
Currently, my Ubuntu box sits behind a Netgear router.  I am THINKING of opening up the router to [partially] expose the box directly to the internet.  My reasons for doing this are because I would like to be able to ssh into my box from work, and I would also like to have an FTP server strictly for my own use, so that I could xfer files to and from work.

Problem is, I don't know JACK about network security under linux.  I have only the vaguest notions of how to procede.  I obviously don't want to open up my samba and nfs shares (and other exploitable things that I probably don't know about) for all to see.

Any advice or a pointer to an Ubuntu/Debian-specific HOWTO would be exceptionally welcome.

Also, I'm SURE there must be a way to do this via some sort of scripting kung-fu:

I would like an automated process that determines what my router's IP address is, and then emails that to a specified email address (namely, my gmail account) at regular intervals.  How would I go about such a thing?

---

### Post by uliketu on 2004-12-21
I would stay away from ftp all together.  Why not use sftp.
It's secure and you don't have to open a whole wack of ports.
There's a win32 port if you require it.

$man sftp

$sftp user@host

---

### Post by negativ on 2004-12-22
ok, so I opened up port 22 on my router and forwarded it to my ubuntu box.  Still, I get "connection refused" when trying to login remotely....

---

### Post by fishd on 2004-12-22
If you're trying to connect from work/school/college/library you'll need to check that their internet connection doesn't block port 22 outbound. You should also check that your ISP doesn't block any incoming ports. Following this theme have you got Firestarter running on your Ubuntu box? If so you need to create a rule to open port 22.

After this check you've got SSHD installed and running and as long as you've not tinkered with the config file it should be listening on port 22.

What software are you using on your client? If running Windows I'd recommend getting 'Putty', google for it, it's brilliant. Download the full package and you'll get psftp (Putty SFTP) which will run with the same config as SSH (only one can connect at a time though I think)...

Try those and let us know how you get on...

---

### Post by uliketu on 2004-12-22
Have you ever tried sshing from work before?
If your ISP is blocking port 22, it's quite easy to get around that.
Have your router forward a random port (say 63999, just an example) to port 22.
Direct your ssh (from work) to use port -p 63999 and your router will do the rest.

From what you state, you either don't have  sshd running or it's bound 
to your localhost address.  At this point I'm guessing.  Go through your config file and make sure it's listening on the correct address and that you have DISABLED ROOT LOGIN.  Try running netstat to see what services are running.  Good luck.

---

### Post by negativ on 2004-12-22
putty is exactly what I was trying to use.  

I can sftp and ssh between the laptop and the desktop, but I was wondering if that had something to do with private vs. public IPs.

According to a web-based port scanning tool, it seems that my port 22 is open.

---

### Post by Averatec5400 on 2004-12-22
[QUOTE=negativ]putty is exactly what I was trying to use.  

I can sftp and ssh between the laptop and the desktop, but I was wondering if that had something to do with private vs. public IPs.

According to a web-based port scanning tool, it seems that my port 22 is open.[/QUOTE]
 I would say to move to a random and much higher (over 1024) port as 22 could be blocked as others have said.

---

### Post by negativ on 2004-12-22
OK, I just verfied with my ISP and the IT guy at work that port 22 in particular is not blocked.

Just for grins, I changed the port in ssh_conf to > 1024 and after that I couldn't even connect between my laptop & desktop.

---

### Post by uliketu on 2004-12-23
By changing your ssh_conf file, you're telling your client to connect to your sshd daemon using port > 1024.  However, your sshd is listening on 22.  This is the reason why you can't connect.   When you're connecting from work you'll need the IP  that your ISP has given you, not your internal IP which is running the daemon.  Keep hacking, you'll get it.

work -> Home (IP) - router (forwards to internal server) -> your sshd daemon

---

### Post by negativ on 2004-12-23
I know this.

Scenario:

desktop private IP = 192.168.0.2
laptop private IP = 192.168.0.3

from laptop at home:
ssh 192.168.0.2 = works

IP supplied by ISP to router = (this is made up) 68.123.456.78

port 22 forwarded to 192.168.0.2 by router.

from work: ssh 68.123.456.78 = connection refused
from laptop at home: ssh 68.123.456.78 = connection refused

me = 

 :confused:

---

### Post by negativ on 2004-12-24
[http://www.sygatetech.com/probe.html](http://www.sygatetech.com/probe.html) reports this:

>  Trying to find out what services you are running...
Secure Shell Open = SSH-2.0-OpenSSH_3.8.1p1 Debian-14ubuntu1

so it looks like the port is open and listening.... why can't I connect?   ](*,)  ](*,)

---

### Post by mistic on 2004-12-25
i don't really know about the unability to connect to it, maybe you should check your router config, or just try having it forward port 7000 to your desktop PC and then connect to your IP (from the ISP) with port 7000, you should also check out what ports the IT-guys at your firm keep closed...


As for the FTP-service, pure-ftpd is GREAT, it has been used on several hacking-parties as the ftp-server for the target machine and it hasn't been compromised yet...

But there is actually no need for it if you get ssh working, you can just use SCP then (its secure copy through the ssh-protocol so everything is encrypted)

in linux:
[INDENT]to get something FROM your machinge to your current PC[/INDENT] 
       ```
scp user@machine:/home/user/file /wherever/you/want/it
```
 
 [INDENT]to get something TO your machine [/INDENT]
        ```
scp /file/you/want/to/upload user@machine:/where/you/want/to/store/the/file
```
      

in windows there's a great gui-tool for doing this (kinda acts linke total-commander named winscp, with that tool it even seems as if you are running an FTP-server on your system eventhough it's just SSH :-)

grtz
Mistic

PS: change "user" to your username on the "machine" and change "machine" to the IP of the machine you are trying to get on

---

### Post by negativ on 2004-12-28
Just a follow-up in case anyone else ever has a similar problem:

It turned out to be the router.

I was given the Netgear MR814, and it replaced my previous Linksys wired router.  On a whim, I decided to reconnect the Linksys and disable all the routing functions on the Netgear router, reducing it to a switch + wireless access point.

I enabled port forwarding on the Linksys router, and now it works like a charm.

I have no idea why the Netgear router wouldn't cooperate, but at least I found the fix.   :D

---

