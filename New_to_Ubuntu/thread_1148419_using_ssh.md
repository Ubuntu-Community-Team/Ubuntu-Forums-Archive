---
title: "using ssh"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Drenriza on 2009-05-04
I have 2 comps with a ubuntu desktop and ubuntu server edition on them. I wanna place my server out of sight, and was wondering how ssh works.

My server got a static ip adress assigned, is it then just from the command line window 

sudo ssh (ip) -4 ? or is their more to it

---

### Post by scheuri on 2009-05-04
There is no need to use sudo when using ssh. SSH is a tool which is (when installed) usually open to any user.

So basically you do this:
ssh [username]@[ip-adresse or hostname]

That is all...unless you need specific features.
Username = Username of the REMOTE box (if it is the same as your local user you are using, there is not need to add that, but you can).

Make sure you have openssh-server installed on the remote server!

---

### Post by SuperSonic4 on 2009-05-04
You can also mount a server folder on your own desktop by following ubuntu-geek's guide: [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

### Post by ptn107 on 2009-05-04
Give this[1] a read over to help you secure your ssh server a bit more.  The default settings for Ubuntu are good, but some holes in /etc/ssh/sshd_config need to be plugged.  Most notably changing 'Protocol' to '2' and setting 'PermitRootLogin' & 'PasswordAuthentication' to 'no'.

[1]_[http://it.toolbox.com/blogs/locutus/shh-securing-ssh-howto-10640](http://it.toolbox.com/blogs/locutus/shh-securing-ssh-howto-10640)_

---

### Post by decoherence on 2009-05-04
another handy trick...

ssh -X username@host

now you can run graphical programs from your remote host and they will display on your local machine. very handy!

---

### Post by taavikko on 2009-05-04
YAHT (Yet Another Handy Trick)

```
cat .ssh/config 
host devil
 hostname www.example.org
 user devil
 port 8000

host kapsi
 hostname kapsi.fi
 user myusername

host server
 hostname 192.168.0.101
 user serv
 port 8080

```

and so on, now for the trick, connecting is simply this
```
ssh devil
```
So you dont have to remember user names and hostnames and such.

More info is to been found in: "man ssh_config"

---

### Post by Drenriza on 2009-05-04
Thanks for all the greath replies guys.

I will probably read this over a couple of times, but im sure i will be able to use all this :)

---

