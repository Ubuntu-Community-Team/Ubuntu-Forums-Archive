---
title: "Port forwarding on Belkin router doesn't work."
date: 2009-12-24
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-12-24
Hi,
I want to set up a simple ftp server to make it easier for me to exchange files on my network and to share files with someone I know. The person I know has difficulty seeing enough to navigate the web so I have been doing some downloading for him, then I give him the files on cd. I would use Ubuntu One or Dropbox for this, but I am concerned that some of the "freeware" I pass along would get my accounts canceled, because of the extra restrictive freeware licenses some of them carry. eg "transferring or storing is forbidden" I'll save Ubuntu One and Dropbox for things that are mine or actually carry "free" licenses.

So I want to start out by installing PureAdmin, because it has an easy enough looking gui for a beginner like myself. The only problem is I can't get my Belkin router to forward port 21. I followed the directions [http://portforward.com/](http://portforward.com/) , but the directions are for an older version of my router. The directions I followed were for Belkin F5D7234-4 but I have Belkin F5D7234-4-v3. For reference look at this page [http://portforward.com/english/routers/port_forwarding/Belkin/F5D7234-4/FTP.htm](http://portforward.com/english/routers/port_forwarding/Belkin/F5D7234-4/FTP.htm) .

I am attaching screenshots of the configurations I have tried, but both times the router told me the configurations were invalid. Does anybody have ideas on how to get this Belkin port forwarded?
Thanks

---

### Post by Temposs on 2009-12-24
Don't you need to type in the IP address field? It's probably just a simple case of you needing to complete that line before moving on.

---

### Post by Zzl1xndd on 2009-12-24
> **Temposs said:**
> Don't you need to type in the IP address field? It's probably just a simple case of you needing to complete that line before moving on.

Temposs is correct you have to tell it what computer you are forwarding the Port too.

---

### Post by ankspo71 on 2009-12-24
Hi, I just managed to forward a port 21 for a single computer to connect on my network. I used my local IP for now which is 192.168.2.2. I also have ufw open on port 21. I went to sheilds up and it said I failed because port 21 is open, which is what I was trying to accomplish lol. 

So if I forwarded port 21 to 192.168.2.2 (my computer on my network, which will have the ftp program running) does that mean that the port is now open to the public? I think shieldsup says it is if I failed. If-so facto, then the term 'private' port must mean the same as local port because I am not able to configure the router with a blank private port or address entry. see screenshot again...

Thanks for the help

---

### Post by elliotbeken on 2009-12-24
yes they are correct, i have a friend that had the same problem but it was fixed when the router new what device to open the port to...

---

### Post by Temposs on 2009-12-24
Yes, in this case 'private' and 'local' refer to the same thing. If your 'shields up' option tries to restrict port 21 as well, and you're trying to forward port 21, that is a conflict, so that security feature will fail.

---

### Post by Zzl1xndd on 2009-12-24
> **ankspo71 said:**
> Hi, I just managed to forward a port 21 for a single computer to connect on my network. I used my local IP for now which is 192.168.2.2. I also have ufw open on port 21. I went to sheilds up and it said I failed because port 21 is open, which is what I was trying to accomplish lol. 

So if I forwarded port 21 to 192.168.2.2 (my computer on my network, which will have the ftp program running) does that mean that the port is now open to the public? I think shieldsup says it is if I failed. If-so facto, then the term 'private' port must mean the same as local port because I am not able to configure the router with a blank private port or address entry. see screenshot again...

Thanks for the help

You do have to specifiy an IP. 

Basically the Router needs to know when trafic comes in on this port (unsolisoted) where to send it. With the IP set When Traiffic comes in on port 21 it is forwared to the local PC at 192.168.2.2 (hence Port Forwarding).


> **Temposs said:**
> Yes, in this case 'private' and 'local' refer to the same thing. If your 'shields up' option tries to restrict port 21 as well, and you're trying to forward port 21, that is a conflict, so that security feature will fail.

Shields up is a test program over at GRC used to test if ports are open. If it shows as Closed in the test and it Failed the True Stealth test then he should be fine.

Basically the Router needs to know when trafic comes in on this port (unsolisoted) where to send it. With the IP set When Traiffic comes in on port 21 it is forwared to the local PC at 192.168.2.2 (hence Port Forwarding).

---

### Post by ankspo71 on 2009-12-24
Thanks again everyone, I have a simple ftp server running and working.

Umm, I noticed something very strange. pure-ftpd & pureadmin will only authenticate logins if the ftp user has a matching ubuntu username and password on my system. So either it is configured wrong or it is supposed to be like that. Currently anonymous connections aren't possible either as a secure connection can't be established. I'll keep working on it and see what happens.:P

---

### Post by ankspo71 on 2009-12-24
Hi again,
Everything is perfect now. I uninstalled pureadmin and pureftpd, then I  installed proftpd and gadmin-proftpd and it is working perfectly. I got pureftpd running in about 2 minutes, after creating the first user, certificate, and set the ftp directory. This server is working out much better.
Thanks again.

---

