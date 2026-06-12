---
title: "[SOLVED] NoMachine stopped after ssh update"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Nampla on 2008-05-14
NoMachine stopped after ssh update. it says:
NX> 500 Authentication failed
NX> 500 Remote host identification has changed
NX> 500 Offending key in /usr/NX/home/nx/.ssh/known_hosts
NX> 999 Bye.
NX> 280 Exiting on signal: 15

but when i go to /usr/NX/home/nx/.ssh/ there is no known_hosts file

what do i do?

---

### Post by chili555 on 2008-05-14
You can do:```
sudo updatedb
locate known_hosts
```I suspect it may actually be in /home/nx/.ssh/known_hosts but that's just my guess.

---

### Post by .rdg on 2008-05-14
The messages given by NX are self explanatory - file usr/NX/home/nx/.ssh/known_hosts includes old keys used by your ssh daemon. Edit the line, remove your old key and it should be fine. In case it's not you should put the current public key you're using (stored in /etc/ssh/ssh_host_rsa_key.pub). That should do it.

---

### Post by JasonAnthony on 2008-05-14
I have had the same problem this afternoon.

After upgrading to the latest versions of nx client, node and server, the problem remained.

At first I followed the instructions on the nomachine website to regenerate and distribute new keys but that did not work.  [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)

So I tried to delete the known_hosts entry on the client but found it just reappeared with each try to connect to the server in question.

Eventually, I went to my target server, and deleted the key from the known_hosts file on that machine!!  Presto!!  Everything is working again.  It was in this directory (I think, I was rushing a bit) - /usr/NX/home/nx/.ssh/

---

### Post by Mortuis on 2008-05-14
I'm still unable to connect to nomachine even after following this advice.

I tried following the instructions at the following link:
[http://www.nomachine.com/news-read.php?idnews=237](http://www.nomachine.com/news-read.php?idnews=237)
But that hasn't helped either.


When I try to connect, it says authentication failed for user, the detail button is grayed out so I'm not sure that I'm getting the exact same error as the original poster, but my problems did start right after I updated SSH.

---

### Post by Mortuis on 2008-05-14
I finally figured out my problem, somehow my username got deleted from nxserver:
> 
USERNAME@SERVERNAME:~$ **sudo nxserver --listuser**
NX> 100 NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 146 NX users list

Username
---------------


NX> 999 Bye


So I set up a new username:
> 
USERNAME@SERVERNAME:~$ **sudo nxserver --adduser USERNAME**

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 716 Public key added to: /home/USERNAME/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye
USERNAME@SERVERNAME:~$ **sudo nxserver --passwd USERNAME**
NX> 100 NXSERVER - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
New password: 
Password changed.
NX> 999 Bye


Everything works now.

---

### Post by Nampla on 2008-05-14
thanks for all the replies.  I figured it out.  I simply had to go to the target machine and delete the key in the /usr/NX/home/nx/.ssh/known_hosts file and then it worked again. I was looking on my local machine for the file and of course it wasnt there.

---

### Post by Nampla on 2008-05-14
once you get the error go to the details. you can click that instead of cancel. that will give you the exact error. THe other thing i reccomend is try to ssh to the target using the same username and password (this can verify that ssh is not the problem, and the user/password is correct).  use ssh -v so you have a verbose to help diagnose the connection issue.  I also reccomend checking your /usr/NX/etc/node.cfg and /usr/NX/etc/server.cfg  for the node and server and ensure that you have the proper ports listed in the correct areas (need to be all the same and uncommented).  THese need to match the /etc/ssh/ssh.config and /etc/ssh/sshd_config files port settings.

---

### Post by martinolsson84 on 2008-05-19
> **JasonAnthony said:**
> I have had the same problem this afternoon.

After upgrading to the latest versions of nx client, node and server, the problem remained.

At first I followed the instructions on the nomachine website to regenerate and distribute new keys but that did not work.  [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)

So I tried to delete the known_hosts entry on the client but found it just reappeared with each try to connect to the server in question.

Eventually, I went to my target server, and deleted the key from the known_hosts file on that machine!!  Presto!!  Everything is working again.  It was in this directory (I think, I was rushing a bit) - /usr/NX/home/nx/.ssh/

Worked fine 4 me.

---

### Post by rylleman on 2008-07-10
I just got this error after an update of my server and SSL.
I don't have a monitor connected to the server and it is a major hazzle to connect it to one so I would need to fix this over ssh.
I've never used ssh in the terminal before so could anyone please help me with this.
(following post #7;)
I have managed to login to the server and cd;d my way to /usr/NX/home/ then when trying to go further to nx/ I get the error "cd: 55: can't cd to nx". A ls shows me that there are a folder called nx but I can't cd into it.
So, how do I reach the known_hosts file?, and how do I edit it over ssh when I reach it?

please help,
-david

---

### Post by simmonsm on 2008-07-25
yes, removing the known_hosts file on the target server also fixed this issue for me. I presume that instead of deleting the file there might be a more subtle way that involves a change to that file's contents that could be done if you have a bunch of other entries to preserve. 

> **JasonAnthony said:**
> I have had the same problem this afternoon.

After upgrading to the latest versions of nx client, node and server, the problem remained.

At first I followed the instructions on the nomachine website to regenerate and distribute new keys but that did not work.  [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126)

So I tried to delete the known_hosts entry on the client but found it just reappeared with each try to connect to the server in question.

Eventually, I went to my target server, and deleted the key from the known_hosts file on that machine!!  Presto!!  Everything is working again.  It was in this directory (I think, I was rushing a bit) - /usr/NX/home/nx/.ssh/

---

