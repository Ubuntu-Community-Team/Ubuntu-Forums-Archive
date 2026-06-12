---
title: "Networking - Samba, SSH- Security"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Ordes on 2009-07-18
When i started with Ubu i used samba to share my files between my Laptop and PC. But sometimes Samba doesnt really satisfy me, specially when u need stuff that is not shared yet... So i tried SSH. And i really like it. But of course i see the possibulity of exploit. And all those pages in the www are pointing it out to.

My question:
1. My network is behind a router. with firewall on and no ports forwarded

How secure is this? are people still able to scan through my router? and find my ssh?

I also changed the ssh default ports, and in firestarter only allowed ssh/port/IP. With ssh/port/IP the only open inbound port allowed for one certain IP

2. Is there a option to just allow ssh for inner network IPs. 

3. Or is there something else that only allows me something like the file managment of SSH, without the ability of become a remote user?

4. SSH keys: Tried to figure it out. But always when i read through the instructions getting confused. 
is it:
A) Server: a) create key b) copy publicKey to the machines u want to connect from (thats what i thought it should be.. but when i read through the instructions it sound like)
B) MyPC: a) create key b) copy publicKey to server u want to connect to

If b is right, how do i:
1) create multiple public keys, for my laptop and pc and how unite them in server?

-----
Or should i just use FTP, for the file sharing? But than again.. people say ftp is not secure... sftp is... but sftp is as far as i see connect to ssh.. so i will still need ssh... and as it seems... mounted ftp is also not browsable for some apps.. 

What i want is basiclly for my two PCs to connect, share the files, without opening the whole command prompt to others...


thanks

---

### Post by .nedberg on 2009-07-18
> **Ordes said:**
> When i started with Ubu i used samba to share my files between my Laptop and PC. But sometimes Samba doesnt really satisfy me, specially when u need stuff that is not shared yet... So i tried SSH. And i really like it. But of course i see the possibulity of exploit. And all those pages in the www are pointing it out to.

My question:
1. My network is behind a router. with firewall on and no ports forwarded

How secure is this? are people still able to scan through my router? and find my ssh?

I also changed the ssh default ports, and in firestarter only allowed ssh/port/IP. With ssh/port/IP the only open inbound port allowed for one certain IP
I would say you are pretty safe if you don't open up your router to allow ssh from outside
> 
2. Is there a option to just allow ssh for inner network IPs. 


Try DenyHost [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)
Or use /etc/hosts.allow and /etc/hosts.deny

But there is no need for this if you don't open your router! If you did I would recommend fail2ban and changing ssh port in the config file.

> 
3. Or is there something else that only allows me something like the file managment of SSH, without the ability of become a remote user?

4. SSH keys: Tried to figure it out. But always when i read through the instructions getting confused. 
is it:
A) Server: a) create key b) copy publicKey to the machines u want to connect from (thats what i thought it should be.. but when i read through the instructions it sound like)
B) MyPC: a) create key b) copy publicKey to server u want to connect to

If b is right, how do i:
1) create multiple public keys, for my laptop and pc and how unite them in server?

thanks
Create a key, then copy it to the server. You also copy it to any machine you want to use for ssh.

Hope this helps!

---

### Post by Ordes on 2009-07-18
thanks helped pretty much so far.. 
except for the keys...

right now with passwords my setting is like:

1) PC 
2) Laptop 
3) Server 

Pc and Laptop can access each other. and both can access server
Server cannot access any of them

1) to access server:
i need to make a key on 1+2 and copy on 3?
 
2) between lap and pc:
i can just use the key i made for server?

but than on 1 i am going to have a public key from 2+3. are they gonna override each other? or do i have to unite them?

---

### Post by .nedberg on 2009-07-18
I am no expert on this as I don't use keys on more than one server, and not across machines as you want

Read about password less ssh and keys here:
[http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/internet/node31.html)
and
[http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-4.html](http://www.puddingonline.com/~dave/publications/SSH-with-Keys-HOWTO/document/html/SSH-with-Keys-HOWTO-4.html)

You can make a key pair on 1, copy to 3 and bring the private key over to 2. That will allow 1 and 2 to log in without password on 3.

Then you will have to generate new keys on 1 and 2 to use for logging in to 2 and 1.

---

### Post by Ordes on 2009-10-20
..txs...

just using ssh now.. its awesome when you get into it.. 

just they keys are not working yet... but as i am only on a home network.. i dont mind using first login/pass.. till i figure that one out

---

