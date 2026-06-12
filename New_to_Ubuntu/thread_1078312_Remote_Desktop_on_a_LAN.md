---
title: "Remote Desktop on a LAN"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by expatCM on 2009-02-23
I can use remote desktop between the viewer and the host.  But that is not exactly what I want to do.

On the lan there are a four clients which I need to look after.  On each client there is my administrator account and three user accounts.  The user normally logs in and that is more or less at the same time that I want to do some administration.....  so I would like to access the machine from the lan.

I cannot use  remote desktop to log in to anything other than the logged in user account.

Is there any way I can access my administrator account whilst the client is used by another user?

---

### Post by issih on 2009-02-23
1) make sure each box has an ssh server on it.

2) ssh into the box you want to adminster as your admin account user:
```
ssh -l username 192.168.0.1
```

Obviously using your username and the ip address of the machine to be administered. 

3) start a vncserver with your ssh terminal.

4) connect to that vnc session

The exact details of 3 and 4 will vary with the program used to initiate the vncserver and also what ports are open on the lan in terms of whether you will need to use ssh tunnelling.

but that is the basic idea.

hope that helps

---

### Post by expatCM on 2009-02-23
That certainly does sound to be an interesting approach.  Thank you for suggesting it.  I will try that out and let you know how it works :)

Amazing really ....  12 minutes between asking a question and getting a solution ...

---

### Post by issih on 2009-02-23
Hopefully it should work, its how things are done on the compute servers in a lab I use. I don't think there is any special configuration on those servers to allow it to function, but I might just be wrong, worth a whirl anyway :)

---

### Post by The Cog on 2009-02-23
This is not a full desktop, but enough for my remote management needs:
SSH to the remote machine  but use the -Y option like this:
> ssh -Y admin@1.2.3.4
This sets up X tunneling back to your desktop so you can do things like nautilus, gksudo nautilus, gksudo synaptic etc.

---

### Post by bodhi.zazen on 2009-02-23
You can forward the entire desktop via ssh and on a LAN speed is not too bad.

You can start a new X session or use Xephyr

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by peterLinux on 2009-02-24
Check out NX.

There is a free and not so free version.
[www.nomachine.com](www.nomachine.com)

or google for freeNX
freenx.berlios.de

PeterLinux

---

