---
title: "update -rc.d, but run as speciffic user?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by outleradam on 2010-10-20
I have a service program called /etc/init.d/mythbackend.  I want it to start on startup using the username mythtv.  How can I make user mythtv run this program on startup?

---

### Post by Cuddles McKitten on 2010-10-21
You're looking for the su (or "substitute user") command with the -c switch.  Assuming you've set up the mythtv account you'd want to run:

```
su mythtv -c '/etc/init.d/mythbackend start'
```The easiest place to put this line would be in your /etc/rc.local file to get it to run at startup.

---

### Post by outleradam on 2010-10-21
That's what I'd like to do, but when I try it gives me permission errors.  Apparently you have to be sudo to start it.  It would require a password.  I can't figure out how to do this properly.  
 
It gives permission errors about a PID file and the /var/log dir.  There's no file in /var/log, I deleted them all and I set permissions to 777 mythtv:mythtv.  I deleted the PID in question and it still cannot start the file.
 
I assume the problem has to do with /etc/init.d jobs not being able to start like a standard script because root owns the terminal right?
 
my work around was to bypass the service completely and drop the line ```
 
sudo -u mythtv mythbackend &

```  into the rc.local file.  It feels really hacky though.  I know there's a proper way to start as mythtv and this is not it.
 
 
I need a better way of doing this.

---

### Post by Hippytaff on 2010-10-21
Might editing the sudoers file sort this?
 
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by outleradam on 2010-10-23
I don't think that has to do with it.   Basically, when running the PPAs, they are packaged to be started as a service with the read/write permissions of user mythtv.

When I build from source, I don't know how to replicate this behavior.  It's either, just start (no service), or run as root.

I need to start a service with permissions of a user.

---

### Post by MichaelJay on 2011-03-03
> **outleradam said:**
> I have a service program called /etc/init.d/mythbackend.  I want it to start on startup using the username mythtv.  How can I make user mythtv run this program on startup?

Hello,

I have the same problem

---

