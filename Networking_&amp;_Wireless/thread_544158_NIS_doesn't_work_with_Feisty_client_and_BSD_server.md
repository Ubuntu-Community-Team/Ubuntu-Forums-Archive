---
title: "NIS doesn't work with Feisty client and BSD server"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by tvreeland on 2007-09-06
Based upon the other (unanswered) threads on similar topics, I don't imagine I'll get an answer but I figure it's worth a try.

I am trying to set up an Ubuntu workstation in an environment with BSD servers and Win2k/XP workstations presently.  We have an NIS server set up for user authentication and NFS/SAMBA fileshares.

After a great deal of troubleshooting and reading posts on this forum, I got the Ubuntu client to authenticate through NIS and automount user's directories.  The only issue was privs on groups like audio and cdrom.  I went home on a Friday and after 20 minutes, I found out how to use PAM to solve my (final) Ubuntu client problem.

Unfortunately, over the weekend, the NIS/file server was replaced with a new machine and all data was migrated over.  The IP address changed, but (according to the system's guy who did it) all other settings are exactly the same on this new server (including the NIS domain name.)

I came in on Monday AM and went to change the IP for the NIS server and then implement the changes to utilize PAM.  No go!  I couldn't get the machine to authenticate..."Invalid Username or Password" is what I get with any network account.  My local admin account on the machine still works.

I'm connecting to the NIS server, YPBIND is fine and I can YPCAT PASSWD to see all the users.  I can also auto-mount the network file system.  No matter what I try, I can't get the NIS authentication to work any longer.

I even went so far as to re-install Ubuntu, following the same exact steps that I had used the previous Friday to get the machine working....and no luck!  I know that the NIS system is working properly because I put BSD on a workstation and it connects fine.  Obviously I'm missing something to make Ubuntu look at the NIS user/pass information.

Can anyone give any help or advice?  I'm really tired of struggling with this for 2 weeks.  It's basically the thing that'll make or break Ubuntu as the new choice for OS to replace Windows in my work environment.

Thanks in advance!

---

### Post by Robstarusa on 2007-11-27
> **tvreeland said:**
> Based upon the other (unanswered) threads on similar topics, I don't imagine I'll get an answer but I figure it's worth a try.

I am trying to set up an Ubuntu workstation in an environment with BSD servers and Win2k/XP workstations presently.  We have an NIS server set up for user authentication and NFS/SAMBA fileshares.

After a great deal of troubleshooting and reading posts on this forum, I got the Ubuntu client to authenticate through NIS and automount user's directories.  The only issue was privs on groups like audio and cdrom.  I went home on a Friday and after 20 minutes, I found out how to use PAM to solve my (final) Ubuntu client problem.

Unfortunately, over the weekend, the NIS/file server was replaced with a new machine and all data was migrated over.  The IP address changed, but (according to the system's guy who did it) all other settings are exactly the same on this new server (including the NIS domain name.)

I came in on Monday AM and went to change the IP for the NIS server and then implement the changes to utilize PAM.  No go!  I couldn't get the machine to authenticate..."Invalid Username or Password" is what I get with any network account.  My local admin account on the machine still works.

I'm connecting to the NIS server, YPBIND is fine and I can YPCAT PASSWD to see all the users.  I can also auto-mount the network file system.  No matter what I try, I can't get the NIS authentication to work any longer.

I even went so far as to re-install Ubuntu, following the same exact steps that I had used the previous Friday to get the machine working....and no luck!  I know that the NIS system is working properly because I put BSD on a workstation and it connects fine.  Obviously I'm missing something to make Ubuntu look at the NIS user/pass information.

Can anyone give any help or advice?  I'm really tired of struggling with this for 2 weeks.  It's basically the thing that'll make or break Ubuntu as the new choice for OS to replace Windows in my work environment.

Thanks in advance!

I have the same problem.  Have you gotten this fixed?

---

### Post by tvreeland on 2007-11-27
No.  I still haven't gotten this fixed.

However, I did notice that the BSD servers are sending out passwd files that have '*' as the symbol for shadowed passwords while the Ubuntu seems to like having 'x' in that location.  I found some old post somewhere implying that this problem could be fixed by patching the server to generate master passwd files with an 'x' instead of '*'.  We tried that change to the server's shell script with no success.  In fact, it still appears to be generating the same file that it did before the patch -- no change.

It's really frustrating that the folks on both sides of this issue wouldn't put their heads together and come up with something consistent across the OSes!!

I've come to the conclusion that I'm not going to get this to work through NIS and am strongly considering finding a way to do the authentication using PAM and Samba, as ugly and stupid as that would be...

:(

---

