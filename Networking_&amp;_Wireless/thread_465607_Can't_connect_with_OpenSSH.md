---
title: "Can't connect with OpenSSH"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by Mets on 2007-06-05
I recently setup OpenSSH on Feisty and I can't seem to connect into my box when I have it connected on my home ISP.  Whenever I try to connect, it just times out.  To see if it was a problem with OpenSSH I tried it at my friends house and I was able to ssh in.  I'm thinking that my router is blocking the port that OpenSSH uses.  Does anybody know what ports I should forward so that this can work?  Or if it might be another reason?  Thanks.

---

### Post by clyrrad on 2007-06-05
Yes, SSH uses port 22, so you will need to forward port 22 on your router to the machine you would like to connect to.

Cheers!

---

### Post by Mets on 2007-06-06
Thanks, perfect fix!

---

### Post by kevdog on 2007-06-06
Port 22 is the standard port, however I would advise you actually change the port number.  You will get a lot of traffic snooping on port 22.  In order to change the port, edit the /etc/ssh/sshd_config file and look for the line Port 22.  Change this to whatever port you want -- some high number.  Remember the port assignment, and restart the ssh server -- sudo /etc/init.d/ssh restart.

Port forward the chosen port to your computer and good to go!

---

