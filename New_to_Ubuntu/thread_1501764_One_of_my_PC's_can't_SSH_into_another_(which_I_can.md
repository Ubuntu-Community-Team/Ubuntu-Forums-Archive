---
title: "One of my PC's can't SSH into another (which I can SSH into from another PC)"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by diablo75 on 2010-06-04
So I have 3 Ubuntu PCs on my network.  One of them is functioning as a media server and has been configured to accept SSH connections (via openssh-server).  I am able to connect to it from my PC, but my girlfriends laptop (as of today) fails to, where previously she had been accessing it through a shortcut I put in her Places menu.  I attempted to recreate the bookmark that she was using to gain easy access to the server and it produces as error message that says:

> Error

Could not open location 'sftp://[server username]@[server IP address}

ssh program unexpectedly exited

That's all the info I have to go off of.

---

### Post by llawwehttam on 2010-06-04
what is the command you use when you get that error??

It seems to be treating sftp://[server username]@[server IP address] as the location

---

### Post by diablo75 on 2010-06-04
I'm not using a command.  Just the built in connection "wizard" in Places>Connect to server.

---

### Post by bodhi.zazen on 2010-06-04
Firewall ?

Can you connect via the command line ?

If these connections are all on a LAN, and not over the internet, you can take a look at nfs or samba and autofs.

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

The thing that I like about autofs, it automatically mounts the network shares when you access them. Access can be from the command line with a cd or ls or opening the share in places.

If you are paranoid, secure it with kerberos (although kerberos is a bit tricky for "casual" use).

---

### Post by diablo75 on 2010-06-04
I'd rather not resort to an alternative method for sharing files over my LAN until it appears to be the only option left on the table.

I don't suspect a firewall to be the issue as I have not altered any firewall settings on the server and I can still SSH into it from my own PC as well as from my Android cell phone over it's 3G internet connection.  Also, in past experience, if a firewall were blocking the connection, the error message would look different; something like "Unable to find path/Host Unreachable" and not "ssh program unexpectedly exited".  So I really feel like the problem lies with my girlfriends laptop, specifically with whatever module is responsible for SSH via Nautilus file browser and, if possible, I'd like to purge and reinstall whatever packages necessary to "reset" it.

---

### Post by bodhi.zazen on 2010-06-04
open a terminal and run

```
ssh -vvv user@server
```

Also output of :

```
sudo iptables -L -v -n
```

Once you get it sorted, keep an open mind to alternates, you might like them.

---

### Post by diablo75 on 2010-06-04
I ran the command line connection to SSH into the server and it worked, but I had to re-establish the key or hash or whatever it is (can't remember).  After that, I was logged into the account for the primary user on the media server, as I had hoped would happen.  After exiting, I checked the bookmark in my Places folder out and it appears to be working the way it used to.  Just click and it automatically connects.

So, I guess this is "solved" now, ha ha.  Does what I wanted it to so I'm going to consider this done.

Thanks for your help!!

---

