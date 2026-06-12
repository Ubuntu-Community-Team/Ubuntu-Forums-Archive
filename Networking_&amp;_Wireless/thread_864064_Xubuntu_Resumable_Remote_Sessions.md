---
title: "Xubuntu Resumable Remote Sessions"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by jcr1 on 2008-07-19
I have been trying to use this HOWTO with varying success...

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

I seem to run into a similar problem quite often. 

I logged in yesterday (over the internet) and got the gdm login screen, logged in, great! full control on display:1. I could log out (using the button for logging out inthe remote window) and log back in later. or I could lock the screen and close the vncviewer.

But sometimes (well quite often) something seems to get upset and I can't get the viewer to open up again. I try the viewer, get prompted for a vnc password, but then get an error:

The connection closed unexpectedly.

And nothing I do now seems to let me get back...

So I tried the following:

```

jonrserv@jcrserver2:~$ vnc4server :1
A VNC server is already running as :1
jonrserv@jcrserver2:~$ sudo /etc/init.d/xinetd stop
[sudo] password for jonrserv:
 * Stopping internet superserver xinetd                                                      [ OK ]
jonrserv@jcrserver2:~$ sudo killall Xvnc
Xvnc: no process killed
jonrserv@jcrserver2:~$ sudo /etc/init.d/xinetd start
 * Starting internet superserver xinetd                                                      [ OK ]

```

thinking, this would kill the vnc session, starting afresh and I could log in...but it makes no difference. The only way I have solved this is by rebooting my server, but obviously this is not a nice option.

Question is basically, why is it doing it and how do I rectify it when it happens? How do I kill it off so its like the first time I am trying to log in?

Hope you can help!

---

