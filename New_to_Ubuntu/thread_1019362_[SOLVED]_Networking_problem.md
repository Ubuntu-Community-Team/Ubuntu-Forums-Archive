---
title: "[SOLVED] Networking problem"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-12-23
Hi

I have a network at home which has all the computers linked through ssh, which I set up with some fantastic help:

[http://ubuntuforums.org/showthread.php?t=900887&page=2]("http://ubuntuforums.org/showthread.php?t=900887&page=2")

All of a sudden, the network is not working.  The error I get when I try to access a folder on another computer is:

Could not open location 'sftp://192.168.1.2/media/New%20Volume/2233/Andrei&apos;s%20Stuff'

Host key verification failed

(see attached screenshot).  Any advice would be greatly appreciated.

---

### Post by iaculallad on 2008-12-23
Try to view this previous [thread]("http://ubuntuforums.org/showthread.php?t=955888"), looks like you both have the same kind of problem.

HTH

---

### Post by RoyHobbs on 2008-12-23
> **iaculallad said:**
> Try to view this previous [thread]("http://ubuntuforums.org/showthread.php?t=955888"), looks like you both have the same kind of problem.

HTH

Thanks for the reply, however not sure if this is the same issue?  I am using SSH not ssh?

---

### Post by hyper_ch on 2008-12-23
and how does "SSH" divert from "ssh"?

---

### Post by Captain_tux on 2008-12-23
> **RoyHobbs said:**
> Thanks for the reply, however not sure if this is the same issue?  I am using SSH not ssh?

Say again?!

---

### Post by albinootje on 2008-12-23
> **RoyHobbs said:**
> 
All of a sudden, the network is not working.  The error I get when I try to access a folder on another computer is:

Could not open location 'sftp://192.168.1.2/media/New%20Volume/2233/Andrei&apos;s%20Stuff'

Host key verification failed


If it all was working, and you didn't change anything related to ssh on that server, then I can think of the following theoretical options :

1) Assuming you're using dhcp, also for your server (not such a good idea), some other machine got the ip-address that the server had before.
2) Your server was compromised.
3) There's a problem with ssh via Nautilus.
4) You changed the hostname of the server, but because your firewall doesn't resolve the domain name "properly", your ssh connection gets redirected to the firewall itself.

Let's look at option 3)
Can you try the same thing on the command-line ?
For example :
```

ssh -v your_username_here@your_server_ip_address_here

```
Post the errors here.Thanks.

---

### Post by superprash2003 on 2008-12-23
are both pcs able to ping each other by ip/.

---

### Post by RoyHobbs on 2009-01-01
HI

Thanks for all your help, with a bit of playing around, I have managed to "fix" my problem.  With regards to the SSH v ssh one of the links I was pointed to ([http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)) had this explanation:

Before we start: in this tutorial, you will come across both SSH and ssh. The difference is this: SSH is the general protocol, and ssh is the linux SSH client command.

I am a NEWBIE (in caps because I really, really am!) so sorry if I asked a stupid question.

---

