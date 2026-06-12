---
title: "X forwarding, then exiting, but without closing X"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by WitchCraft on 2011-01-24
Question:

I have a server where I connect to via ssh.
It works fine, and also, X-forwarding works fine (in the local network).

Now I wanted to run a server program under wine. because it's a winoze application, it doesn't run on the command line, so I have to start it via x-forwarding. So far not a problem, works wonderfully.

My problem is I connect to the target computer with X-forwarding, like this: ssh ip.of.target.computer -X

then I start gnome-session from the ssh terminal, then I can start the server. But when I want to logout from the X-forwarding, that closes the gnome-session (and the server X-window-application)...

How can I login, start a X-window application, and then logout ssh without closing the X-application ?

---

### Post by WitchCraft on 2011-01-25
will 

```

background_job &

```


that is to say
```

gnome-session &

```

suffice ?

---

### Post by bodhi.zazen on 2011-01-25
I think for the functionality you want you should look at tunneling a VNC connection over ssh.

If you are running a command line application you would use something like screen.

Alternates might be nohup or dtach.

[http://chithanh.blogspot.com/2010/07/three-way-mini-shootout-between-gnu.html](http://chithanh.blogspot.com/2010/07/three-way-mini-shootout-between-gnu.html)

---

### Post by WitchCraft on 2011-01-26
> **bodhi.zazen said:**
> I think for the functionality you want you should look at tunneling a VNC connection over ssh.

If you are running a command line application you would use something like screen.

Alternates might be nohup or dtach.

[http://chithanh.blogspot.com/2010/07/three-way-mini-shootout-between-gnu.html](http://chithanh.blogspot.com/2010/07/three-way-mini-shootout-between-gnu.html)

nohup 
[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)
seems to be what I'm searching for. Will see about that this evening.

If I decide I want to stop gnome-session started on the server via ssh with nohup, how do I do that ?




On serverfault, somebody recommended the -N ssh option:
[http://serverfault.com/questions/226857/how-to-start-remote-xorg-gnome-via-ssh-xforwarding-then-close-ssh-but-without](http://serverfault.com/questions/226857/how-to-start-remote-xorg-gnome-via-ssh-xforwarding-then-close-ssh-but-without)

After reading it twice to three times, I'm still not sure if that's what I need.

---

### Post by bodhi.zazen on 2011-01-26
> **WitchCraft said:**
> nohup 
[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)
seems to be what I'm searching for. Will see about that this evening.

If I decide I want to stop gnome-session started on the server via ssh with nohup, how do I do that ?




On serverfault, somebody recommended the -N ssh option:
[http://serverfault.com/questions/226857/how-to-start-remote-xorg-gnome-via-ssh-xforwarding-then-close-ssh-but-without](http://serverfault.com/questions/226857/how-to-start-remote-xorg-gnome-via-ssh-xforwarding-then-close-ssh-but-without)

After reading it twice to three times, I'm still not sure if that's what I need.

If you are wanting to connect to X applications I think VNC over ssh is the best option, otherwise I think all X apps will terminate when you close the X session.

Otherwise, dtach, nohup, disown, screen, others ...

---

