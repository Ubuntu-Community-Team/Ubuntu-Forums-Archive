---
title: "ssh works in terminal but not in GUI"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by ginestre on 2008-01-20
I am setting up a linksys nslu2 ('slug') as a fileserver to the machines at home, and everything so far has gone well. Now I need to ssh into the slug to use its hard disks- and I can, quite happily, from a terminal. But I can't from the GUI on my Feisty machines: I get three tries on the password, and then connection refused. Anyone any ideas why?


[EDIT: moved from beginner's forum as this is probably more appropriate]

---

### Post by blueridgedog on 2008-01-20
What GUI are you using? 

It may be a version issue.  I THINK the ssh command is auto sensing the remote site, but the GUI may be trying SSH 2 when the device only supports 1 or the reverse.

---

### Post by ginestre on 2008-01-20
> **blueridgedog said:**
> What GUI are you using? 

It may be a version issue.  I THINK the ssh command is auto sensing the remote site, but the GUI may be trying SSH 2 when the device only supports 1 or the reverse.

Thanks for the reply. I'm using gnome on the client machines, under Feisty and just trying to connect via Places-> connect to server. If I open a terminal window and do
 ```
 ssh user@192.168.etc  
``` it works fine. The slug is running a thing called dropbear -it has a minimal system- but I could install and run openssh.

---

### Post by blueridgedog on 2008-01-20
We could test the device and see it is only accepting ssh 1 or ssh 2:

```
 ssh user@192.168.XXX.XXX -1
```

tests ssh 1

```
 ssh user@192.168.XXX.XXX -2
```

tests ssh 2

If it accepts 1, but rejects 2, I would wager that the gnome tool is defaulting to 2.  I scanned the help file, but could not see an option to specify.

---

### Post by geirha on 2008-01-20
> **ginestre said:**
> Thanks for the reply. I'm using gnome on the client machines, under Feisty and just trying to connect via Places-> connect to server. If I open a terminal window and do
 ```
 ssh user@192.168.etc  
``` it works fine. The slug is running a thing called dropbear -it has a minimal system- but I could install and run openssh.

Try ```
sftp user@192.168.etc
```
Nautilus uses sftp when you choose Places -> Connect to server -> SSH, so your ssh-server needs to have sftp-support.

---

### Post by holbech on 2008-01-21
Hi

Just used several hours with a similar problem 
"Nautilus cannot display "ssh://admin@192........" ssh from the commandline worked perfect.

Not quite sure if nautilus actually uses sftp, but installing openssh-sftp-server on my nslug and ensuring that both the "box" and my pc had openssh-server installed solved the problem. both SSH and SFTP works.

Hope this helps

 - holbech

---

### Post by jeffus_il on 2008-01-21
If you're interested try sshfs with fuse, here's the link:
[http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)

It maps the sftp remote host to a local folder, and you can browse it with whatever you want, no support needed.

---

