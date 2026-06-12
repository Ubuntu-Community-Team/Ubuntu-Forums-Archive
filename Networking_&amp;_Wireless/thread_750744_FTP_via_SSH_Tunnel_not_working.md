---
title: "FTP via SSH Tunnel not working"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Das Oracle on 2008-04-09
I have a server at home running an ssh server and proftpd. 

1. I opened port 21 on my router and connected remotely = Success.
2. Closed port 21 since I will be tunneling via ssh
3. Installed SSH and opened port 22 on my router
4. Connected remotely via ssh = Success
5. Connected via ```
ssh -L 5950:127.0.0.1:21 -l username hosturl
``` = success
6. tried to connect to ssh->ftp tunnel via  [ftp://username@127.0.0.1:5950](ftp://username@127.0.0.1:5950) = Failure

Problem: it will say connecting for a long period of time and eventually time out. Any ideas?

---

### Post by Eiríkr on 2008-04-10
If you're using a browser, and if you haven't done any fancy port rejiggering (which it looks like you might with the 5950 suffix), you can just type the following into Nautilus:
```
sftp://USERNAME@IP.ADD.RE.SS
```

Cheers,

Eiríkr

---

### Post by Das Oracle on 2008-04-10
that is a good thing to try, however when I am away I am usually on a MAC w/ safari and so I need to get that ssh tunnel working. I will try the nautilus in my ubuntu install, but I still need a working solution. Thanks!

---

### Post by Eiríkr on 2008-04-10
I just tried on my own old iBook.  Safari doesn't recognize the sftp protocol, so I tried typing in ftp instead.  Safari just sat there, but then Firefox popped up open to the link I'd just typed into Safari... :confused:  Anyway, if you can afford the disk space to install Firefox on your Mac, Firefox can definitely get into my ssh server via FTP, so it'll probably work for you too.  

Cheers,

Eiríkr

---

### Post by Das Oracle on 2008-04-11
i'll definitely give it a shot, thanks

---

### Post by Iowan on 2008-04-11
I don't have all the SSH options in front of me, but the general logon is something like ```
ssh -p *portnumber* username@hostname
```


Don't mind me...I'm just a little confused about using the -L option.

---

### Post by The Cog on 2008-04-12
Try this command on the remote host (after setting up the SSH session):
**telnet localhost 5950**
and see what the fail reason is. I would have thought your FTP tp port 21 should be able ot connect - the config looks right to me.

However, you shoudl be aware that any FTP transfer doesn't just use port 21. It opens a separate TCP connection for passing data - the connection on port 21 is just the control channel. So even if you get your port 21 tunneling working, you will not be able to transfer files, or even directory listings.

Since you have an SSH server running, why not just use SFTP instead?

---

