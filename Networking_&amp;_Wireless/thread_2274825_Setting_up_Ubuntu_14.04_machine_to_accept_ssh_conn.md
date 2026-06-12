---
title: "Setting up Ubuntu 14.04 machine to accept ssh connections from a Win 7 box"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by IZavorin on 2015-04-22
I've been using Unix/Linux off an on for a few years but this is really the first time I am trying to config/admin a new Ubuntu system. 

I just installed Ubuntu 14.04 64bit version on a desktop. This is a work computer that has a wired connection to the Internet but it's not part of my corporate network.

I have a Win 7 box with Cygwin installed on it and I would like to ssh and scp to the Ubuntu machine from it. This box is on the corporate network (in case that makes any difference).

I ran ifconfig on Ubuntu and grabbed the eth0-inet address (let's call it FOO.BAR). Tried "ssh [EMAIL="username@FOO.BAR"]username@FOO.BAR[/EMAIL]" and got 


[INDENT]ssh: connect to host FOO.BAR port 22: Connection refused

[/INDENT]


What do I need to install/configure/run on the Ubuntu box to enable ssh/scp?

Thanks much!

---

### Post by TheFu on 2015-04-23
Install openssh-server and fail2ban packages on the "server".
Open any firewall settings for port 22/tcp on the "server".

On the client, install putty (cygwin is just too slow), and follow the instructions for putty to create ssh-keys.
Push the public ssh-key to the "server" ... sorry, I'm weak on the details because between linux systems we just used **ssh-copy-id** to do this - it puts in into the right file, in the correct directory and doesn't mess up directory or file permissions as often happens when people manually do it (like I think you will have to).

First time you ssh in, use the ip address and password. Once you get the keys pushed over, then you'll never need to know the password again. Plus passwords are highly non-secure - keys are 2048x more secure (actually more than that). Always use key-based authentication on networks.

There are other steps to secure that ssh connection, but cause if it is on a network, someone will try to brute force in.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by IZavorin on 2015-04-23
Thanks. I'll try that. As a temp measure, I got access using these commands:

```

sudo apt-get update
sudo apt-get install openssh-server
sudo ufw allow 22

```

But I agree, this is not the best method. Thx

---

### Post by TheFu on 2015-04-23
Please, please, please, please install fail2ban. The default settings will protect you 1000x more than nothing and do ZERO harm.

---

