---
title: "How can I access my own home on another PC"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by irw on 2006-08-25
I have two PCs on a wired network via a router. I can access folders on each with samba, but would like to control this a bit better.

Each PC is set up with the same user accounts for all 5 members of the family, with a shared folder on each that everyone can access.

Is it possible to set it up so that whoever is using one PC can access their own home plus the shared folder on the other PC?


(I am also looking at using SSH so I can administer the other PC even if someone is using it - that that will be another thread if I get too stuck!)

Any suggestions or help gratefully recieved!

---

### Post by Crooksey on 2006-08-25
Enable ssh, open the ports, then you can directly connect to your PC and be greeted with the ubuntu command line, that enough control?

---

### Post by az on 2006-08-25
I guess you can mount all of their home directories on one box with the corresponding directories on the other box using NFS.  But both computers would have to be on at the same time and a lot of things will be pretty slow.

As well for SSH, 
sudo apt-get install ssh.

Then just access the other box

ssh -X me@192.168.0.10

and run your graphical apps as well as have a command line.

I don't think you want to be running a LTSP client, though.  I think that would mean that you have to boot over the network onto your other box and then it would be doing all the work for both.

---

### Post by irw on 2006-08-26
Thank you for the head-start on SSH - that was the next project I had not yet really got into!

Is it possible to have different samba.conf files for each user?  I know my current one is in /etc/, but Would anyone know if that would be a possibility?

---

