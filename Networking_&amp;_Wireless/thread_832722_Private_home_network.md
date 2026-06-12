---
title: "Private home network"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by rplantz on 2008-06-18
I have had only moderate success with networking my computers and printers at home. I would like to try to understand how to make them all talk nicely to each other.

I'm running OSX on a Mac G4, Ubuntu 8.04 on a desktop (AMD64), Windows XP on a desktop, Windows Vista on a laptop, and a laptop that dual boots into Ubuntu 8.04 or Window Vista.

I've read quite a few HOWTOs. Most are about setting up a file server. I don't want that. I just want any computer to be able to talk to any other within my home.

Some are connected to my router with wires, others wireless. They all work access the internet nicely.

Thing seemed to be working well, but Vista would access my Ubuntu files *without a password*. OSX correctly and Ubuntu correctly required a password.

I've been using Samba to do this. Is this the best choice? I'm an experienced programmer, but still learning a lot about networking. I'm not afraid to spend the time understanding the Samba documentation, but I would like some assurance that I'm on a reasonable path.

My router is configured to provide dynamic ip addresses. Would static be better?

---

### Post by dmizer on 2008-06-18
in order to share files to other computers, the machine hosting the files must be set up as a file server.

for example, when you use your ubuntu machine to access files on your mac g4, your mac is acting as a file server.  when that same mac g4 accesses files on your vista machine, your vista machine is acting as a file server.

vista may actually be automatically sending the password.  so even though you're not actually seeing the prompt, you're probably getting it anyway.  if you'd like confirmation of this, you can look at your samba logs in /var/log

i have very little experience with setting up a file share between ubuntu and mac, and when i did (way back in breezy), it was buggy at best, but you indicated that it's working as expected so it seems like you have that  solved.

since you have a variety of operating systems accessing each other, your best solution is to make use of a file sharing protocol which is common to all systems.  there are only two that i can think of which fit this bill: samba, and ftp.

since you seem to be asking for advice rather than specific help, i will say this:
in most cases, it's both easier and safer to have a centralized and shielded dedicated file server where all machines can access files at any time.  there's a lot of great reasons for this, not the least of which is that you don't have to go turn on another machine to access a file located on it.

---

### Post by lisati on 2008-06-18
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) explains one way of setting up file sharing across a home network from the Ubuntu perspective. I've managed to use the instructions there with just two machines, neither of which is a server. The effective result is something along the lines of Windows file sharing, using shared folders that are accessible from other machines on the network.

The best approach will depend on your needs.

---

