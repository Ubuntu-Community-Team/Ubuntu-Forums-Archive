---
title: "proftpd security issues"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Tomi Hakulinen on 2006-11-14
Hello,

I have a huge problem with ProFTPd. I have been searching for an answer for 3 days now and the problem just keeps getting weirder the more I dig in it. This is what's going on:

**1. Configuration**
1.1) I have made a user to use for ftp connections.
1.2) I wrote this (and a fiew hundered different version of it) in the /etc/proftpd/proftpd.conf file to chroot users:
```
<VirtualHost 192.168.1.151>
User **the user I created**
Group **the group with the same name as my user**
DefaultRoot /var/www/ **the user I created**
</VirtualHost>
```
1.3) I have tried DefaultRoot and DirectoryRoot inside <VirtualHost> tags. I have tried both outside any tags <>. I have tried both inside <Global> tags.
1.4) Putting User and Group inside <VirtualHost> was just a desperate attempt.

**2. The Problem**
2.1) When I access the ftp server using either dos prompt or IE6, logging in as my ftp user, I am sent to the correct directory (/var/www/). Not sure if I'm chrooted here though, I need to try that in dos prompt.
2.2) When I access the ftp server with the ftp tool in Putty, it throws me into the ftp users home directory and allows me to move around, browsing files on my whole server! I haven't tried removing stuff yet since I bet if I knew it was possible I wouldn't sleep at nights unless I turned off my server! :-k 

**3. What I'm trying to accieve**
3.1) Having an admin ftp user (doesn't need to be admin for real, just a normal user), that is chrooted to /var/www/
3.2) Having another user, one that I will allow my friends to use, that is chrooted to /var/www/ftp/

**4. Possible ways out**
4.1) Repairing this issue (my favorite)
4.2) Reinstall of ProFTPd
4.3) Installing some other ftp daemon, suggestions?

 - Tomi H.

---

### Post by dmizer on 2006-11-14
use the second link in my sig to configure proftpd.  follow the non-gui instructions and you'll have a relatively secure ftp server with chrooted accounts.

---

### Post by Tomi Hakulinen on 2006-11-14
Hello,

that thread looks good. I wonder how I have managed to not see that one ](*,). I will try that once I get home from work, even if I have remote terminal and could do it from here.

Thanks dmizer, I really hope I get it sorted with that :D.

---

### Post by lkagan on 2006-11-14
Putty is an SSH client.  When you connect to the server using putty, you are connecting to the ssh server via the sftp subsystem of your ssh server, NOT proftp. You are connecting to port 22 (ssh), not 21 (ftp) thus it's a different server all together. Your proftpd conf has no affect on your putty login.  Users and passwords and everything else are different on the two servers.

Larry Kagan

---

### Post by Tomi Hakulinen on 2006-11-14
Oh! I were just about to post here about the changes not really... changing anything. That explains it then. So it was not up to my skills then, even if I'm a newbie in the linux world :D. Thanks for the info Larry, now I can sleep my night in peace again.

---

### Post by Tomi Hakulinen on 2006-11-15
Hello,

sorry for bumping this thread, but this is kind of related. I am currently connected to my server from work, trying to turn off sftp because it's really confusing me. Besides, what do I need 2 ftp servers for? I have a question that I would like an answer for:

How do I turn off the sftp server currently running? It was not installed by me so it must have been delivered with ubuntu 6.10. It would be nice if someone could provide a command for doing this.

- Tomi H.

---

