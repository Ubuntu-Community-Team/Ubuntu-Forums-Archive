---
title: "X11 + SSH fowarding problems !!!!!!!!!!!!!!!!!!!!"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by pavanakumar on 2008-04-13
Hi
I know that many have posted the same thing again and again I read all of them and tried it out but it never worked for me...
I installed Kubuntu 7.10 on my laptop it found all my devices (including my wireless) and everything works seanlessely. The problem is running remote X app thro SSH.

I am giving the response I got 

I tried ssh -X user@localhost and also ssh -Y user@localhost both returned the same thing

pxm260@localhost's password:
Warning: No xauth data; using fake authentication data for X11 forwarding.
Linux (none) 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

Last login: Sun Apr 13 14:35:13 2008 from localhost
/usr/bin/X11/xauth: (stdin):1:  bad display name "unix:10.0" in "remove" command
/usr/bin/X11/xauth: (stdin):2:  bad display name "unix:10.0" in "add" command
prompt:> xclock
pxm260@:~$ X11 connection rejected because of wrong authentication.
X connection to localhost:11.0 broken (explicit kill or server shutdown).

I tried with a remote server 
ssh -X or -Y user@remotehost

Warning: No xauth data; using fake authentication data for X11 forwarding.
prompt:> xclock &
X11 connection rejected because of wrong authentication.
X connection to localhost:52.0 broken (explicit kill or server shutdown).


I tried the following based on the problems and solutions reported in the forum

1) Installed openssh-server
    sudo apt-get install openssh-server

2) change the options in the sshd_config (for me it is)

   X11Forwarding yes
   X11DisplayOffset 10
   PrintMotd no
   PrintLastLog yes
   TCPKeepAlive yes

3) Tried to put the following options in ssh_config

Host *
    ForwardAgent yes
    ForwardX11 yes
also with just
    ForwardX11 yes

4) Also tried this option in ssh_config

Host *
   XAuthLocation /usr/bin/xauth
 
5) Also tried with the option   in sshd_config

  X11UseLocalHost yes

6) also tried adding the forwardx11 option in ~/.ssh/config 

 7) Finally I tried to remove the .Xauthority from the home directory of both the remote system and mine and reconnect 

all the above failed with the same error 

I have spent about 48 hours trying to figure out and hence decided to post this ... I was previously running  Knoppix and it worked fine. I have similar problems with Gentoo I installed in my office PC and tried everything in their X11 forwarding wiki. Please help he with his....

---

### Post by pavanakumar on 2008-04-13
I solved my problem 

I just typed 
xhost + 

on my laptop and tried to connect WOW !!!! it connected ..... :guitar:

---

