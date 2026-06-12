---
title: "just installed ubuntu 9.04"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by joeoreg on 2009-06-11
Yesterday I decided I had enough of Microsoft slavery, so I installed ubuntu 9.04.
When configuring my system and trying to fetch a few programs the following message appeared :
*W: Failed to fetch*[B][http://ie.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.21+nobinonly-0ubuntu1.9.04.1_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_2.0.0.21+nobinonly-0ubuntu1.9.04.1_i386.deb)
  Could not connect to ie.archive.ubuntu.com:80 (193.1.193.69). - connect (111 Connection refused)[/B]Can anybody please help me ?

---

### Post by Mornedhel on 2009-06-11
Hello,

Pinging ie.archive.ubuntu.com seems to work fine. Maybe it was offline yesterday for whatever technical reason. It happens.

If updating/upgrading still doesn't work today, you should switch to another server (System > Administration > Software Sources), for instance the main server (archive.ubuntu.com).

---

### Post by 123456789123456789123456 on 2009-06-11
check your internet connection first, make sure that your internet is working properly.
If so, like you can connect to internet, and download, view web pages, so on.  Then go to synaptic package program, and tell it to reload.
It would seem that your software sources are out of date for some reason.  Reloading fources Ubuntu to go out and see which ones are available, and download all information it can from them.  It should eliminate that error.
The only other concern I have is that the address 193.1.193.69 does not exist.  It is not a ip address that I am familuar with.  Thats why I asked to check internet connection to begin with.

---

### Post by Therion on 2009-06-11
The message you're seeing is really nothing to worry about.  Sometimes server "x" will go offline for a bit for whatever reason and you'll get that "error message".  You can try a different server or just ignore it; it'll go away by itself.

> **123456789123456789123456 said:**
> 
The only other concern I have is that the address 193.1.193.69 does not exist.  
Yes it does.  That's the HEAnet server in Ireland, they mirror Ubuntu releases.

---

### Post by Mornedhel on 2009-06-11
> **123456789123456789123456 said:**
> The only other concern I have is that the address 193.1.193.69 does not exist.  It is not a ip address that I am familuar with.  Thats why I asked to check internet connection to begin with.

As Therion says, it's the Irish server for Ubuntu repositories (ie.archive.ubuntu.com), and it pings fine from here in France. I am curious ; how did you come to the conclusion that 193.1.193.69 doesn't exist ?

---

### Post by Therion on 2009-06-11
> **Mornedhel said:**
> I am curious ; how did you come to the conclusion that 193.1.193.69 doesn't exist ?
I was all ready to be a smart *** and suggest he used [http://www.193.1.193.69.com](http://www.193.1.193.69.com) but you know what?  

It's a dating site in the UK...

Shut ME up!

---

### Post by joeoreg on 2009-06-11
> **Therion said:**
> I was all ready to be a smart *** and suggest he used [http://www.193.1.193.69.com](http://www.193.1.193.69.com) but you know what?  

It's a dating site in the UK...

Shut ME up!
how the hell did that get there ?
I used the check box on the add/remove applications and I'm getting the same answer when I try to install the lamp server !

---

### Post by Mornedhel on 2009-06-11
> **joeoreg said:**
> how the hell did that get there ?
I used the check box on the add/remove applications and I'm getting the same answer when I try to install the lamp server !

You misunderstood :) It would seem Therion's joke backfired. [www.193.1.193.69.com](www.193.1.193.69.com) is a website whose IP is *not* 193.1.193.69. It's just a coincidence.

193.1.193.69 is indeed the IP for the Irish server for the Ubuntu repositories. You probably set your localisation to Ireland when you installed Ubuntu. All this is very normal.

Have you tried my suggestion about Software Sources ? Aside from having a lower downtime, the main server has the advantage that it's the first where updates arrive, the other servers being mirrors of the main one.

---

### Post by Therion on 2009-06-11
> **Mornedhel said:**
> You misunderstood :) It would seem Therion's joke backfired. 
Precisely.

That'll teach *me*, huh.




/Or WILL it????

---

