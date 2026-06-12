---
title: "SSH X11 Forwarding problem"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by cleam on 2008-08-17
Hello.

I've just installed Ubuntu 8.04 and want to run its x applications remotely from my mac.

I've checked out that /etc/ssh/sshd_config has 'X11Forwarding yes' line. Also it contains following options related to X11:

X11Forwarding yes
X11UseLocalhost no.

But when I try to connect to ubuntu from my mac I have following error during login: 'Warning: No xauth data; using fake authentication data for X11 forwarding.' (I'm using 'ssh -X -Y login@ubuntu-host')

Attempt to run some x11 application produces this

Error: Can't open display: ubuntu-host:11.0.

After that I tried to set display manualy: 'export DISPLAY=client-host:0.0'. I've got the same result: 

No protocol specified
Error: Can't open display: star-6.local:0.0

---

### Post by babounours on 2008-08-17
can you connect without the X11 forwarding?
if yes - did you start X11 on your mac before connecting ? (I think the -Y is sufficient though)
if no : open the ssh/known_hosts and erase the line corresponding to the server ip

---

### Post by cleam on 2008-08-17
Yes, ssh connetcion works fine.

X11 works on mac localy.

---

### Post by SpaceTeddy on 2008-08-17
the error is right there - you need to install xauth on the server for the forwarding to work - you can do that with this command

```
sudo apt-get install xbase-clients
```

This needs to be installed on the server. Then the x forwarding should work

---

### Post by cleam on 2008-08-17
I have ran these commands on client machine and 'Warning: No xauth data; using fake authentication data for X11 forwarding.' disappeared:

/Users/klim% rm ~/.Xauthority 
/Users/klim% xauth list
xauth:  creating new authority file /Users/klim/.Xauthority
/Users/klim% xauth generate `echo $DISPLAY` .
xauth:  creating new authority file /Users/klim/.Xauthority
/Users/klim% xauth list                      
star-6.local/unix:0  MIT-MAGIC-COOKIE-1  370e4a7924014377243a286a195c5e67

But the problem still remains. It's unable to run x11 apps on ubuntu host, even with set DISPLAY:

ubuntu-host:~$ xcalc
Error: Can't open display: ubuntu-host:10.0
ubuntu-host:~$ export DISPLAY=client-host:0.0
ubuntu-host:~$ xcalc
No protocol specified
Error: Can't open display: client-host:0.0

---

### Post by cleam on 2008-08-17
ubuntu-host:~$ sudo apt-get install xbase-clients
[sudo] password for cleam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xbase-clients is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

It seems I already have xbase-clients installed

---

### Post by cleam on 2008-08-17
A bit of clarification: it seems to be not problem of the client. I tried to login to another host and x11 forwarding works well.

---

### Post by cleam on 2008-08-17
Very strange. Following steps was helpful:

ubuntu-host:~$ xclock 
Error: Can't open display: localhost:10.0
ubuntu-host:~$ export DISPLAY=ubuntu-host:10.0
ubuntu-host:~$ xauth generate `echo $DISPLAY`

After that I need to run export DISPLAY=ubuntu-host:10.0 after each ssh login.

I tried to set X11UseLocalhost to 'no' in /etc/ssh/sshd_config on ubuntu host. This sets default value of $DISPLAY to ubuntu-host:10.0 (instead previous localhost:10.0). But x11 forwarding remains malfunctioning!

---

### Post by dmizer on 2008-08-17
> **cleam said:**
> Hello.

I've just installed Ubuntu 8.04 and want to run its x applications remotely from my mac.

I've checked out that /etc/ssh/sshd_config has 'X11Forwarding yes' line. Also it contains following options related to X11:

X11Forwarding yes
X11UseLocalhost no.

But when I try to connect to ubuntu from my mac I have following error during login: 'Warning: No xauth data; using fake authentication data for X11 forwarding.' (I'm using 'ssh -X -Y login@ubuntu-host')

Attempt to run some x11 application produces this

Error: Can't open display: ubuntu-host:11.0.

After that I tried to set display manualy: 'export DISPLAY=client-host:0.0'. I've got the same result: 

No protocol specified
Error: Can't open display: star-6.local:0.0

You should use either -X or -Y, but not both.  For OSx, you may only be able to use -Y which is not as secure.  So, try this:
```
ssh -X login@ubuntu-host
```

If that is not successful, try this:
```
ssh -Y login@ubuntu-host
```

If neither of those are successful, we'll need to take a deeper look at what you're using on OSx for X11. What X11 emulator are you using in OSx?

---

### Post by cleam on 2008-08-18
dmizer, thank you for reply.


> **dmizer said:**
> You should use either -X or -Y, but not both.


I've read it at man pages after first post :)

Now every time I'm trying two variants 'ssh -X ...' and 'ssh -Y...' after that.


> **dmizer said:**
> 
If neither of those are successful, we'll need to take a deeper look at what you're using on OSx for X11. 

I'm using standard x11 system bundled in OSx (X11.app 2.1.1 - (xorg-server 1.3.0-apple5)). But I think  it is not client problem. I checked x11 forwarding at other two hosts (OpenSuse and RHEL) — it works.

---

### Post by dmizer on 2008-08-18
Try comparing the sshd_config files from your OpenSuse and RHEL installs.

Is there possible firewall interference? Check your iptables configuration with the following command:
```
sudo iptables -L
```

---

### Post by cleam on 2008-08-18
Unfortunatelly, I'm not the administrator of these servers so I don't have access to sshd_config.

'sudo iptables -L' returns
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

