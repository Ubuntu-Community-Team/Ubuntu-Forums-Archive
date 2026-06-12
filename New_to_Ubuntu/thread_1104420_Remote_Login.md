---
title: "Remote Login"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Al Fischer on 2009-03-23
I think I have read every post on the subject of remote login and am able to connect quite successfully from XP to Ubuntu. However, I (amongst many others) am looking for a way to login to a user ID that is available on the system and not already logged in. Yes, on a machine that may be sitting on a log on screen after being restarted. Ideally, more than one user could log in to his/her own ID as a user.

Or is Ubuntu incapable of doing this?

---

### Post by kanikilu on 2009-03-23
I think FreeNX will do what you want...check out this page:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

I installed the FreeNX server from the PPA, and use the free client from NoMachine's website.

---

### Post by Al Fischer on 2009-03-23
Thanks for the guidance. I just installed it and a client for XP on my laptop. Looks like I need to configure it so thats my next step. Looks like it may need to be started.

This is one I have not tried as there seems to be a lot of comments about it being difficult to set up. Can't be worse than all the other attempts that have not solved my problem!

---

### Post by bodhi.zazen on 2009-03-23
> **Al Fischer said:**
> I think I have read every post on the subject of remote login and am able to connect quite successfully from XP to Ubuntu. However, I (amongst many others) am looking for a way to login to a user ID that is available on the system and not already logged in. Yes, on a machine that may be sitting on a log on screen after being restarted. Ideally, more than one user could log in to his/her own ID as a user.

Or is Ubuntu incapable of doing this?

I am guessing from your post yo uare trying something like VNC.

You can easily log in as any user with ssh.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Use Putty from windows.

In terms of forwarding X applications, you can forward them with -X

here is but one example :

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

If you are on windows you will need a X server, I use cygwin.

If you wish to use VNC, install vnc4server. As it turns out there are different VNC servers. The default (vino) requires one to be logged in, as you say, as does x11vnc.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Here is how I suggest you do it :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by Al Fischer on 2009-03-23
Well, I have spent 3+ days trying to understand, install and configure various packages including a variety of VNC that wouldn't dowhat MOST people are trying to do. Just log in like you can easily do from Remote Deskto Connection in windows. This should not be brain surgery to accomplish. Much negative about FREENX.

The worst problem I had was inputting the required repository info and when I did that right it was get, install, download client, and connect. EASY. Actually easier that setting up RDC in windows where I ran into a problem with a registry setting that has been problems for years and never fixed by M$.

People were saying to do remote login some combination of SSH, or PuTTY, or VNC (some flavor) and nothing seemed to work for me. Yes, I am a wet behind the ears newbie to Linux but quite experienced in many other aspects of the IT world. (back as far as CPM, the Altair and DOS 1.0)

So I thank you for putting me on the path to success. I needed a WIN the week!

Now off to install the secure keys before some bozo tries to hack my server. THAT would really tick me off.

---

### Post by bodhi.zazen on 2009-03-23
Yes, we understand your frustration.

It is a matter of installing the correct VNC server. And yes, if you are new to Linux (and even if you are not so new) it is not intuitive which vncserver to install.

---

### Post by dcparham on 2009-04-09
error: 

i have 2 boxes: 1 unbuntu 8.04 at work, and work xp-pro laptop i use from home and i need to access the ubuntu box from outside work.  using: the https website help.ubuntu.com/community/FreeNX, i followed the instructions until i had an error: when performing "/etc/init.d/ssh restart", the error is:
---
open: Permission denied
 * Restarting OpenBSD Secure Shell server sshd                                                                                                               start-stop-daemon: warning: failed to kill 5223: Operation not permitted
open: Permission denied
                                                                                                                                                      [ OK ]
/etc/init.d/ssh: 168: cannot create /proc/5223/oom_adj: Permission denied
---
i changed the port listened to, from 22 to 8888, but get same error.

unable to get any farther at this point; would like to access the ubuntu box from home starting tomorrow for the weekend - any ideas?

---

### Post by bodhi.zazen on 2009-04-09
Use sudo ...

```
sudo /etc/init.d/ssh restart
```

---

### Post by dcparham on 2009-04-13
Thank you very much for your reply - after using "sudo", the procedure led me to several levels of more problems with FreeNX; then tried Putty, and getting "connection refused" error. As is sometimes the case, something that doesn't work right away requires many more steps of troubleshooting which makes the procedure so much more different than things that work with relatively few steps.  Now the time spent on it is precluded by more urgent priorities.  Thank you, Bodhi, for being there, and to the Community for continued efforts to help one another.  I will circle back around later:|.

---

