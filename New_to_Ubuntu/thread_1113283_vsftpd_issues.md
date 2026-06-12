---
title: "vsftpd issues"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by ronin2307 on 2009-04-01
In my quest to conquer Ubuntu (or at least pretend) I decided to install a FTP server. Quick google search seemed to suggest to take the vsftpd route, so i did
I installed it fine and the server is up and running. I also made a few basic changes to the conf file (turn off anon for example).
The bottom line is this:
I cannot connect to the ftp from any machine on my network. There is no firewall between the machines. I can sort of connect to the ftp server from the ubuntu machine itself but once i enter my usr and pwd I get this back:

500 OOPS: could not open chroot() list file:/etc/vsftpd.chroot_list

Can somebody tell me what I am doing wrong? I just want to be able to set up a simple and secure ftp server on Ubuntu. I also created an UNPRIVILEGED user called ftpsecure and that is what I wanted to use to log in to the ftp site

thanks

---

### Post by ronin2307 on 2009-04-01
OK, I have figured out the error part of my problem. Apparently I misunderstood the whole chroot concept, so once i commented the relevant lines out I could login in from the local ubuntu machine

however i still cannot connect from any other machine on the network (all windows). It is still timing out. Please help
thanks

---

### Post by ronin2307 on 2009-04-01
never mind. I am an idiot. I forgot that I installed firehol. Once I stopped the service I could connect just fine. 
I just need to figure out now how to enable ftp in the conf file 

on a separate note: which folder do the ftp users end up in by default when using vsftpd as ftp server?\
thanks

---

### Post by Malalo on 2009-04-01
> **ronin2307 said:**
> on a separate note: which folder do the ftp users end up in by default when using vsftpd as ftp server?\
thanks

Usually this would be /var/ftp/pub by default. I'm not sure for vsftpd though...

---

### Post by ronin2307 on 2009-04-01
could you explain me the following:
I now can use my ftpsecure account to log in to the vsftpd server.
The default home directory is /home/ftpsecure

Now, ftpsecure is a local user account (unpriviledged). How do I create an exclusive FTP account, without making it an ubuntu account? is that even possible? RIght now, my ftpsecure account, even though it is unpriviledged, can list every directory on the machine. I can go up to /bin etc and dig into them. Obviously I don't want anybody too be able to do this, so the other question is how do I prevent this?

thanks again

---

