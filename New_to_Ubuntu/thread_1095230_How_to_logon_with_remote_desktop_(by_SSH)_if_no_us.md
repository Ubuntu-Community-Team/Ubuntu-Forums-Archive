---
title: "How to logon with remote desktop (by SSH) if no user is loggod on?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by JeroenG on 2009-03-13
Hello,

I configured a SSH tunnel to be able to acces my PC's at home from my office spot. For this I use an Ubuntu distribution on an old laptop.

After my Ubuntu server rebooted, nobody was loggod on and I could not reconnect with remote desktop anymore. 

Is there a way so logon with remote desktop client (VNCViewer) when there is no active user logon? (look for command line commands I can run after my SSH logon)


Thanks,
Jeroen :popcorn:

---

### Post by Peter09 on 2009-03-13
firdt, ssh should be able to login with no user on the 'target machine. Have you installed openssh-server on the target.

Issuing the command 

```
ssh -X <your username>@<target machine> xterm
```

should give you and xterminal on your local machine which is running on the client.

Once you have ssh working install on the client nxclient

```
sudo apt-get install nxclient
```

and on the 'target' do

```
sudo apt-get install nxclient nxnode nxserver
```

running nxclient on the local machine will allow you to establish a desktop on the remote machine.

---

### Post by kpatz on 2009-03-13
Install x11vnc from the repositories.

Then from your ssh shell run:
> sudo /usr/bin/x11vnc -q -safer -nopw -auth /var/lib/gdm/:0.Xauth -display WAIT:1280x1024:0 &

Change the numbers after WAIT to the desired (or actual) screen resolution.

Set up a port 5900 tunnel in your ssh client, and use VNC to view your desktop.

I use xinetd to launch x11vnc for me so it doesn't have to run all the time, using this line in inetd.conf:

vnc     stream  tcp     nowait  root    /usr/bin/x11vnc -q -inetd -ncache 10 -safer -once -nopw -auth /var/lib/gdm/:0.Xauth -display WAIT:1280x1024:0 -o /tmp/vnc.log

The only issue I have is, if the desktop is logged out, I can log in but then it drops the VNC connection.  I just reconnect and I'm in.

---

### Post by DonaldJ on 2009-03-13
A few minutes ago, I wiped the keys, and the screen came up while it was locked and asking for my password..  and there's no way I wiped my password...  

I wonders which key(s) bypassed the password..?  I scrubbed the keyboard quite briskly...

---

### Post by kpatz on 2009-03-17
> **DonaldJ said:**
> A few minutes ago, I wiped the keys, and the screen came up while it was locked and asking for my password..  and there's no way I wiped my password...  

I wonders which key(s) bypassed the password..?  I scrubbed the keyboard quite briskly...

:confused:  What are you trying to say?  You were cleaning your keyboard and your (locked screen) password prompt appeared?

Hitting a key while locked will bring up the prompt AFAIK.  Now if you said that the password prompt appeared and then the screen UNlocked... I have no idea unless you "entered" your password while cleaning the keys...

---

### Post by betrunkenaffe on 2009-03-17
You may have accidentally switched to another user.

Is nxclient/nxserver faster than VNC?

If you add -C2 to your ssh then it should speed up your connection via vnc.

---

### Post by darksideforge on 2009-03-17
> **kpatz said:**
> 
vnc     stream  tcp     nowait  root    /usr/bin/x11vnc -q -inetd -ncache 10 -safer -once -nopw -auth /var/lib/gdm/:0.Xauth -display WAIT:1280x1024:0 -o /tmp/vnc.log


kpatz,

Is there a reason not to use vinagre since it's already installed with the distro?

Here's my question on all of this: I don't have any problem getting into work server from my home laptop (20 miles away) using

```
ssh username@domain.com
```

What I have a problem with is then using VNC to view the desktop on my server. After I've established the ssh in my terminal, how then do I bring up the VNC viewer so that it recognizes my connection?

In other words, should I attempt to launch vinagre or gtk-vnc-viewer thru my console, or should I go up to Applications-->Internet--> and choose it there? I've noticed that on older distros of Ubuntu (8.04/8.10) there is a second line in vinagre that allows you to specify which port (5900, etc) you wish to use. Part of my problem may be that in v9.04, the second window is gone in vinagre and typing :XXXX after my domain entry isn't working either (on the top line for domain/host, that is).

It seems that I must be missing an xstart or startx command somewhere on my terminal prior to attempting to get VNC to run properly.

Any suggestions?

---

