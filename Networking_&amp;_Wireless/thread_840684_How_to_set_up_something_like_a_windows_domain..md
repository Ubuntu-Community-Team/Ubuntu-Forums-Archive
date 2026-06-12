---
title: "How to set up something like a windows domain."
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by musther on 2008-06-25
I do network admin for a local small school, currently 99% Windows based (they have one ubuntu computer).  

Anyway, the principle and I have been talking and we're just chewing over the possibility of going to a fully linux network.

I'm experienced with linux, and I'm experienced with windows domains and such, but I've not set up something like this under linux, so I have a few questions.

The system they currently have is a 2003 server, about 50 XP desktops, and about 10 XP laptops (oh, and one Ubuntu desktop!).  
Pretty standard windows domain stuff, including file synchronisation for the laptops so that they can be used off-network.

Now for the possible Ubuntu based replacement:
An Ubuntu server - I've set a couple of these up for various things in the past, but not for networked users.
Desktops set up to connect to the network, users home folders on the server I assume, together with user account info, so all user stuff is controlled centrally.
Same for the laptops with the addition that when a user logs in to the laptop, their profile and home folder should be synced so that when they go off-network, they can still log in and work on their files, which will have to be uploaded to the server again next time they connect.
Then hopefully centralised updates and installing of software etc?

So, can anybody give me a rough rundown on how to achieve this, how to set up the desktops to use the server, and how to set up the laptops.  Also, pointing me to any good documentation of this kind of stuff would be very, very helpful.

Thanks a lot.

---

### Post by Mr_Whippy on 2008-06-26
Hi Musther,

there is a guide out there to setting up samba and openldap to allow both ubuntu and windows clients to join a domain, 

if you google smaba openldap domain you should find it, however i have tried it myself a few times and always seem to get something wrong, that is openldap wont start when i have followed some of the instructions, however that is probably just me,

[http://ubuntuforums.org/showthread.php?t=640760&highlight=openldap+samba](http://ubuntuforums.org/showthread.php?t=640760&highlight=openldap+samba)

edited to add link to the

---

### Post by musther on 2008-06-26
Thanks for the information, but I think you misunderstood me.  I'm not looking to add linux clients to a windows domain, I'm looking to provide domain type functionality with a linux network.

Basically:
* Authentication from the server
* /home/user mapped from server

Cheers

---

### Post by Mr_Whippy on 2008-06-27
Hi mate,

that guide allows you to add windows and linux clients to a linux domain, and should give you most of the domain type things you are looking for, have a read through it and see what you think

---

