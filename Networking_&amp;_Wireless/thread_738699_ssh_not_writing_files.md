---
title: "ssh not writing files"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by keithclark on 2008-03-28
I am sharing directories on two different computers via ssh.  I can view directories and even play a video file from one machine to another, but when I try to copy and paste a directory over, a window opens up saying it is copying the file, but nothing else happens.  No progress and no errors.  It just sits there seemingly doing nothing and when I check my network activity, it also appears as though it is not transferring anything.  What could be wrong?

Keith

---

### Post by beren.olvar on 2008-03-28
sounds wierd...

I used to use ssh before and I am pretty sure it worked for me...
it may sound naive, but had you tried dragging and dropping?

cheers

---

### Post by keithclark on 2008-03-28
Yes, I've tried dragging and dropping.  Not only does it not transfer, and just sit there, but it will not allow me any more access to that computer via ssh.  I have to logout and log back in again in order to regain access.

---

### Post by keithclark on 2008-03-29
Further information that may be relevant, one computer is running 7.10 and the other 8.04.

---

### Post by fmartinez on 2008-03-29
> **keithclark said:**
> I am sharing directories on two different computers via ssh.  I can view directories and even play a video file from one machine to another, but when I try to copy and paste a directory over, a window opens up saying it is copying the file, but nothing else happens.  No progress and no errors.  It just sits there seemingly doing nothing and when I check my network activity, it also appears as though it is not transferring anything.  What could be wrong?

Keith

Ok... So it sounds like your setting up your SSH connection from the option in Places => Connect to a Server..... Then you enter your IP address of the server you want to connect and log in and passwd. 

One of the things or problems that I've overlooked is if I'm using a specific directory to hold my music and videos... the permissions I had as the user logged on wasn't able to write to that specific directory. Might be worth looking into. 

Aslo... I found that mounting that specific drive on the Host machine using NFS worked alot better than than connecting through the above described way. That maybe also another option. 
$man nfs
in a terminal to get more info

---

### Post by keithclark on 2008-03-29
Ok, after much searching and some kind advice on the ubuntu-server irc channel, I found out that nothing is wrong with ssh.  I can use scp and it works like a charm.  Not pretty and graphical but it works.

It appears as though it is a Nautilus/sftp problem.  I need to keep researching this issue and I hope someone out there can help.

Keith

---

