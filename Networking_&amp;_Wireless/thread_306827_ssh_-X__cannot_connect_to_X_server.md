---
title: "ssh -X:  cannot connect to X server"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by walding on 2006-11-25
Hi,

I am able to connect to my other PC via ssh, but I cannot connect to the X server.  

connecting works.
ssh username@ip-address

connecting with -X works:
ssh -X username@ip-address
(ditto for -Y)

However, if I want to invoke something like amarok, it won't allow it:
ssh -Xf username@ip-address amarok
returns:
~ cannot connect to X server

Can anyone help please?

AW

---

### Post by BatteryCell on 2006-12-03
bump

---

### Post by walding on 2006-12-04
Thanks for the bump!  I'm still stuck with this.  I can connect to the X server if I do the commands from the other PC to this one upstairs, but that's not what I want to do!

---

### Post by frisket on 2006-12-04
I have the same problem. I've been using FC4 on machines foo and bar and I just installed Edgy on foo. I need to be able to ssh from foo to bar and run Emacs on bar and have the window display back on foo. 

As normal, I have set xhost bar on foo, and then on bar I type emacs -display foo:0.0 & which always used to work. IPtables on foo also contains the rules
-A INBOUND -s <ip-for-bar> -p tcp -m tcp --dport 6000:6015 -j ACCEPT 
-A INBOUND -s <ip-for-bar> -p udp -m udp --dport 6000:6015 -j ACCEPT 
which is all I've ever needed in the past.

Now, with Ubuntu on foo, when I log into bar and type the emacs command above, I get 
  emacs: Cannot connect to X server foo:0.0.
  Check the DISPLAY environment variable or use `-d'.
  Also use the `xhost' program to verify that it is set to permit 
  connections from your machine.
This is obviously wrong (the X server is correct, DISPLAY=:0.0, xhost is set, and X ports are permitted). I've been doing this between machines for years...what have I missed?

///Peter

---

### Post by frisket on 2006-12-05
Well duuuh, ssh -X does the trick.
Never needed to use it before.

---

### Post by walding on 2006-12-05
Sadly it's not working for me still.  Even after a fresh install.  I give up!

---

### Post by netztier on 2006-12-05
> **walding said:**
> Sadly it's not working for me still.  Even after a fresh install.  I give up!

There's no need to give up as long as it ain't broken. Check the sshd configuration on the machine you're trying to SSH into ([FONT="Courier New"]**/etc/ssh/sshd_config**[/FONT]).

The line with ...

```

X11Forwarding yes

```

... should be there and not commented-out with the # sign. I don't know if this setting is off by default on Ubuntu.

And while you're at it, check for the SFTP Subsystem and add or uncomment the following line:

```
Subsystem sftp /usr/lib/openssh/sftp-server
```

This will allow you to use "Connect to Server" with SSH in Gnome to "mount" a remote folder via SSH or do **[FONT="Courier New"]sftp[/FONT]** and [FONT="Courier New"]**scp**[/FONT] commands from a shell.


regards

Marc

[SIZE="1"]PS: "after a fresh install"? Linux is an open source unixoid operating system. Here, things are found, tracked down and fixed when they don't work. 8) Doing "fresh installs" (or re-installing the latest service pack) to fix misconfigurations is from the Windows world, where it can please go and hide in a corner. And stay there ;)[/SIZE]

---

### Post by Familienvater on 2008-05-26
Hi, I have the same problem. I actually want to start mythtv-setup by:

```

frontend@ubuntu:~$ ssh -X backend@192.168.1.10 /usr/bin/mythtv-setup 

```

My frontend is running on Ubuntu 8.04. My backend is installed on Debian Etch.

On the backend, my /etc/ssh/sshd_config looks like:

```
X11Forwarding yes

Subsystem sftp /usr/lib/openssh/sftp-server 
```

I always get the following message:

```
mythtv-setup: cannot connect to X server 
```

What am I missing? Please help me on that! 

Thanks,

FV

---

