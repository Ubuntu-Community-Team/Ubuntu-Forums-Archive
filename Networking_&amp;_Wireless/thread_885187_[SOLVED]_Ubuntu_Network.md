---
title: "[SOLVED] Ubuntu Network"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by Jerky on 2008-08-09
Okay I am a little new to Ubuntu but not a complete noob. I have a Ubuntu server and Ubuntu desktop. My ubuntu server has openssh installed. I can connect to the server via ssh and do command line actions on the server. I am also trying to use ssh to map a network share and see the files and folders.

It works and i can see the files and folders but it seems that i cannot create new files or folders. It is greyed out in my file explorer. Everything is a fresh install.

Any Suggestions?? Am i just missing something simple?

Thanks in advance.

---

### Post by Jerky on 2008-08-09
bump!

---

### Post by AlecJ on 2008-08-09
Yes your missing the permissions aspect of the shared folders etc...
You need user permissions set correctly to do stuff like that.
[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

---

### Post by zipperback on 2008-08-09
> **Jerky said:**
> bump!


Please don't bump your message after only 30 minutes of posting it. That's really pointless and impatient.

- zipperback
:popcorn:

---

### Post by Jerky on 2008-08-09
Its very strange. I followed those directions line for line. The only other thing i did was install vmware server. But i dont think that should make a difference.

I did all of those things. Should i remove openssh and install again?


P.S. sorry for bump post earlier.

---

### Post by Jerky on 2008-08-09
Wait. The username they use according to them is supposed to be my computer name. Is this correct? I am using my username and password that is on the server and on the client. (they are the same) If not i guess i need to make a user on the server with my computer name.

---

### Post by Jerky on 2008-08-09
Fixed.

A link on that site told me to run this

sudo chown your-username /media/dir-name

Did that and i am good.

Thank you for your help!

---

