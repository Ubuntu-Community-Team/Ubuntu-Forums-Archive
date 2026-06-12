---
title: "Access mounted SSH drive from terminal"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by marksoccer on 2008-04-05
I am using Gusty Gibbon and have mounted the drive of my school account through the ubuntu menu under Places->Connect to Server...   This works great, I can access my files and everything and it logs in as soon as I login to ubuntu.  However, is there a way I can access this drive from the terminal.  The only way I know how to currently is through the GUI, by going to Places->"NAME OF SHARE"

---

### Post by Eiríkr on 2008-04-06
If it's a ssh account you're logging into, as noted in your subject line, then simply open a terminal and type in:
```
ssh USERNAME@SERVER
```
Replace the caps as appropriate.  You'll be prompted for your password, and then you're in.

HTH,

Eiríkr

---

### Post by marksoccer on 2008-04-06
Yeah, I knew I could do that, but I figured since I am already logged in, there must be a way to access the share through the terminal.  The way you suggested requires me to relogin.

---

### Post by koenn on 2008-04-06
I don't think you can do that. 
ssh isn't a file sharing protocol or a network file system. 
What you see in Nautilus is just a graphical representation of a file/directory hierarchy - 
I imagine nautilys executing a number of commands over ssh (such as ls, cd, or something similar... ) and use that information to build you that folder tree you see.
So what you see only exists inside nautilus, and you can't really access it from a shell. 
Tthe command line equivalent would be to use ssh, scp, ... as you normally do. 

Of course, this is just a guess, and I could be completely wrong

an alternative would be to use sshfs, a 'filesystem' built on top of sftp, which is an ftp through an ssh channel. That would allow you to mount remote directories in your local directory tree, pretty much like nfs or smbmount.

---

### Post by Perkins on 2008-04-14
The problem is that, so far as I know, when you use the "connect to server" option in Gnome, it doesn't actually mount anything anywhere.  It just gives you access to it on the fly.  Which means that the only programs which will recognize the "mountpoint" are ones which can interface with gnome.

from the command line, at this point in time, using sshfs is probably your best bet.  I don't know if there's a good explanation of how to make it work here somewhere...  It was broken at one point, but seems to be fixed now.  Unfortunately it seems to work differently, and I haven't managed to figure it out yet...  Is there anyone out there who can point us in the right direction?

---

### Post by marksoccer on 2008-04-14
Is there anyway I can mount the SSH drive then, or a way that I can login to my ssh server without entering my password and everything?  Like one simple command that is easy to remember.

---

### Post by bbukh on 2008-04-14
You can login into ssh server without being prompted for password if you copied your private key to to .ssh/authorized_keys file on the remote server.  Just search google for "authorized_keys" for instructions how to do that.

---

### Post by marksoccer on 2008-04-15
Thanks, I will give that a try.

---

