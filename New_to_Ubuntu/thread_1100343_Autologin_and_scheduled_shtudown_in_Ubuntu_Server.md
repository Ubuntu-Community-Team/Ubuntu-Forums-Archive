---
title: "Autologin and scheduled shtudown in Ubuntu Server"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by mha2908 on 2009-03-19
Hi, I've got a brand new PC, which I use as server. It is headless, and I've got my BIOS set up to automatically boot at 8 AM, and since the PC is put away, and has no attached keyboard or mouse, i DO NOT want to type in my credentials. Instead I want it to autologin my user, or at least login using another PC. I was able to do this with the Desktop Edition using XDMCP, but I do n't know how to do it in the Server Edition. I can't access it with SSH as long as its not logged in.

And there's one more thing I want to do: Schedule an automatic shutdown at 24 PM. How do I do that?

Some might ask: Why shut it down? Then you don't have to login!
But, since it is placed in my home, I am paying for electricity, and those 8 hours is just a waste. I've also set up the BIOS to accept the WakeOnLan-signal, so I can turn it on between 24PM and 8AM if I want to.

---

### Post by Zack McCool on 2009-03-19
> **mha2908 said:**
>  I can't access it with SSH as long as its not logged in.

You should be able to without a problem.  Is OpenSSH installed?  Is the sshd daemon set to start on boot?  The console should not need to be logged in for a remote ssh session to work.

> 
And there's one more thing I want to do: Schedule an automatic shutdown at 24 PM. How do I do that?


You'll want to put the shutdown command in root's crontab, set for Midnight.

---

### Post by mha2908 on 2009-03-19
Plz tell me how to. Im a total noob! How do I set the SSH-daemon to start on boot?

And exactly how to that "crontab"-thing?

---

### Post by yeats on 2009-03-19
All server daemon programs, including sshd, should be coming up automatically when your computer starts, so no need to worry.  If your computer is ON, all ssh, printing, file sharing, etc. services that you set up will be available on the network.

Regarding crontab, you will learn much by doing:

```
man crontab
```

You'll want to learn your resources, especially if your new and running in a headless server environment.  Man pages + Google + Ubuntu Forums should be a sufficient combination :-).

---

### Post by mha2908 on 2009-03-19
ty for the replies. I will try to connect to ssh without loging in, even though i've already tried once, but maybe something went wrong. Can't you give me a command to schedule shutdown with crontab?

---

### Post by Oval on 2009-04-09
> **mha2908 said:**
> Can't you give me a command to schedule shutdown with crontab?

This is what the shutdown in my crontab looks like. It shutsdown at 12:01am.

```
1 0 * * * /sbin/shutdown -h now
```


Edit: I didn't see the last post was 3 weeks old until after I posted... #-o

---

### Post by Jakey_TheSnake on 2009-04-09
^ would 

```
/sbin/shutdown -p 00:00
```

not work, just out of interest?

---

