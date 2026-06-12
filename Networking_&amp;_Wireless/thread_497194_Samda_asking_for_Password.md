---
title: "Samda asking for Password"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Bob Fletcher on 2007-07-09
I have just install Ubuntu 7.04 along with Samba. The installation
went very smoothly.

The problem I now have is when I try to access folders on my
Linux box from my Windows XT machine a password is requested.

Right Clicking under properties says I do not have the unnecessary network privileges

I have tried to use my Linux login but this is not accepted.

I want the network to be as open as possible as it is just a two
machines home network.

The entry in samba.conf is:

[Documents]
path = /home/bob/Documents
available - yes
browsable = yes
public = yes
writable = yes

---

### Post by fredj on 2007-07-10
You have to add users and their passwords to samba. It has its own separate security system.
I can't remember the name of the program that you use to do this.
Otherwise you can set the security mode in the smb.conf file to, I think its 'share'  or 'shared' but I'm
not sure so check in the documentation. This will get rid of the need for passwords etc but its not so secure.

---

### Post by AhrenBa on 2007-07-10
Go to the terminal and type this:

sudo /etc/samba/smb.conf

Then use the find tool. Search for the term "security", uncomment it by removing the ";". The change the word user to share .

You will have to restart the Samba server after this.

---

