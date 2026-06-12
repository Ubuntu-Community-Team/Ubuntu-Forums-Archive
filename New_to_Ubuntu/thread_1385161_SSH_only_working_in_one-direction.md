---
title: "SSH only working in one-direction"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by rawny on 2010-01-19
Hi there,

I'm having some difficulty with SSH. My setup is as follows:

rawny-desktop:
- Karmic desktop edition
- Behind a router, port 22 is being forwarded to this computer

rawny-server:
- Karmic server edition
- In a different location behind another router, port 22 is being forwarded to this computer

I have SSH from rawny-desktop to rawny-server working fine and using a set of encryption keys. But if I SSH into rawny-server and attempt to SSH back to rawny-desktop I get the following message:
```
ssh: connect to host rawny-desktop port 22: Connection refused
```Using firestarter on rawny-desktop I added a rule to allow SSH connections from rawny-server on port 22, so it should be allowed in.

I would like to be able to SSH into rawny-desktop from rawny-server so I can use rsync to backup some files to rawny-server.

Where should I start trying to fix this?

Thanks,
Rawny

---

### Post by myth1914 on 2010-01-19
If this is a fresh install:

sudo aptitude install openssh-server

on the machine that can not be connected to.

---

### Post by rawny on 2010-01-19
openssh-server is installed on both machines.

---

### Post by myth1914 on 2010-01-19
What is your output from 
netstat -lnptu

---

### Post by rawny on 2010-01-19
On rawny-desktop:
```
rawny@rawny-desktop:~$ netstat -lnptu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:5050          0.0.0.0:*               LISTEN      3753/python     
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      3746/dropbox    
tcp        0      0 127.0.0.1:15550         0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:9000          0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           3746/dropbox    
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:53277           0.0.0.0:*                           -               

```On rawny-server:
```
rawny@rawny-server:~$ netstat -lnptu
(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               

```They appear to be both listening on port 22, so that's a good sign right?

---

### Post by b0b138 on 2010-01-19
I;m just guessing cause I'm not really sure, but, wouldn't it need to be a different port since rawny-desktop is already using port 22 for ssh cliet side?

Why wouldn't you just ssh into server to backup files?

---

### Post by rawny on 2010-01-19
Sorry, I should have explained that more clearly, I want to use cron on rawny-server to run a backup script automatically. It uses rsync to pull stuff across from rawny-desktop.

I had this setup working when both machines were part of the same local network, but now that they are not, I have been unable to get everything to work in the same way. I have probably screwed up my SSH configuration slightly while attempting to fix the problem...

As far as I can tell my iptables on rawny-desktop (set via firestarter) allow SSH from both the local and the remote IP addresses for rawny-server, so I'm not sure why its connection attempts are being refused.

Thanks,
Rawny

---

### Post by bodhi.zazen on 2010-01-19
Turn off your firewall and try again.

If it works, you need to configure your firewall.

If it does not work, are you using anything such as denyhosts or fail2ban ?

post the output of 

ssh user@server -vv(the -vv option gives up more verbose output).

---

### Post by rawny on 2010-01-19
I stopped the firewall in Firestarter and tried again, but it didn't work.

I'm not using denyhosts or fail2ban.

```
rawny@rawny-server:~$ ssh rawny@rawny-desktop -vv
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to rawny-desktop [***.***.***.***] port 22.
debug1: connect to address ***.***.***.*** port 22: Connection refused
ssh: connect to host rawny-desktop port 22: Connection refused
```

---

### Post by alejaaandro on 2010-01-19
might be a stupid question, but can you ping your desktop from the server? 
also, is ssh server running on port 22 on your desktop? you might have changed it and not remember, or you could try changing it see if that works..

---

### Post by rawny on 2010-01-25
Hi thanks for the replies, sorry I haven't been about, to get back to  it...

> **alejaaandro said:**
> might be a stupid question, but can you ping your desktop from the server? 
also, is ssh server running on port 22 on your desktop? you might have changed it and not remember, or you could try changing it see if that works..

No, a ping results in 100% packet loss.

Yes it is on port 22, at least that's how it appears from the results of  "netstat -lnptu" and is also how it is set in "/etc/ssh/sshd_config"

Running SSH over a different port produces exactly the same results. :(

I guess my next question is: how do I go back to a completely clean SSH setup, i.e. no-SSH related configuration files/keys etc. on any of my computers?

Is it just a case of removing all openSSH packages and removing "~/.ssh" and "/etc/ssh/", or are there any other directories/files that need removing?

That is unless anyone has a better idea (than complete SSH removal and restart) towards recovering from the current situation.

Cheers,
Rawny

---

### Post by t0p on 2010-01-25
The fact you can't ping the desktop tends to indicate that the computer is not visible, so this isn't just an SSH config issue.

Are you sure your ISP isn't blocking traffic from the outside internet (you said the computers are on different networks so I'm assuming their traffic passes over the internet)?

If your ISP is blocking traffic on port 22, you may be able to get past this by getting the SSH server on rawney-desktop to listen on a non-standard port.   Look [here]("http://www.itworld.com/nls_unixssh0500506") for info on what to do.

---

