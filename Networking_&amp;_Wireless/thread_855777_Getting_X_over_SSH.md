---
title: "Getting X over SSH"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Wayfarer247 on 2008-07-10
Hey, my friend and are messing around with a computer.  I want to get X (Gnome) over SSH.  I can ssh into the computer, that is fine.  But when I run an application, I get:

```
$ xclock
Error: Can't open display: 
```

So I have tried:  $ ssh -x user@ipaddresss

Same thing.  I have tried to start Gnome and X.
```

$ gnome-session
(gnome-session:17396): Gtk-WARNING **: cannot open display: 
```

```
$ startx
xauth:  /home/epic/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/epic/.Xauthority
xauth:  error in locking authority file /home/epic/.Xauthority
xauth:  error in locking authority file /home/epic/.Xauthority

X: user not authorized to run the X server, aborting.
No protocol specified
giving up.
xinit:  Permission denied (errno 13):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/epic/.Xauthority
Couldnt get a file descriptor referring to the console
```

The computer we are working with does not have a monitor setup, but Gnome does work (We set it up and all that).

Any ideas?  I would really like to get X working over SSH!

---

### Post by goexplode on 2008-07-10
> So I have tried: $ ssh -x user@ipaddresss

The options "-x" and "-**X**" work differently. "-x" disables X11 forwarding, while "-**X**" allows X11 forwarding. Try is with the capital X.

Furthermore, check "/etc/ssh/sshd_config" and be sure you have "X11Forwarding yes" somewhere in there.

---

### Post by Wayfarer247 on 2008-07-10
Hmmmm, I have tried both.  For testing's sake though, I tried again.

I got this message upon logging in:

```
$ ssh -X user@IPADDRESS

/usr/bin/X11/xauth:  /home/epic/.Xauthority not writable, changes will be ignored
```

So then I try again:

```

$ xclock
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0
```

I tried the other stuff too again:

```
$ sudo gnome-session
[sudo] password for user: 
X11 connection rejected because of wrong authentication.

(gnome-session:17646): Gtk-WARNING **: cannot open display: localhost:10.0
user@IPAddress:~$ startx
xauth:  error in locking authority file /home/user/.Xauthority
xauth:  error in locking authority file /home/user/.Xauthority
xauth:  error in locking authority file /home/user/.Xauthority
xauth:  error in locking authority file /home/user/.Xauthority

X: user not authorized to run the X server, aborting.
No protocol specified
giving up.
xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/user/.Xauthority
Couldnt get a file descriptor referring to the console

```

Kinda confused here, but thank you for that reminder!  So, any other ideas?

---

### Post by Wayfarer247 on 2008-07-11
Bump!

---

### Post by quantumstitch on 2008-07-11
what are the permissions of .Xauthority? Should be,
```

[quantumstitch@dethklok:~]$ ls -l .Xauthority 
-rw------- 1 quantumstitch quantumstitch 376 2008-07-09 13:40 .Xauthority

```

---

### Post by Wayfarer247 on 2008-07-11
Thanks for getting back to me.  I ran the same command:

```
epic@computer:~$ ls -l .Xauthority
-rw------- 1 root root 122 2008-07-10 20:17 .Xauthority


```

I am not logged on as root.

**Edit**

Also, when I run the command "$ ssh -X user@computer" on Mac OS X (10.5.4) the X11 icon appears on the dock, which, to me, means that X is getting forwarded to my computer, or at least the information that x SHOULD be forwarded is being sent.  I have been testing this on Fedora9 and OS X.

---

### Post by prem1er on 2008-07-11
Remove the .Xauthority file.  A new one will be created next time you ssh in.  Tell me if that works.

---

### Post by prem1er on 2008-07-11
If that doesn't work I there is a post on another forum that I have seen work before too.  Try this.  I have seen this problem sooooo many times and usually just removing the file works for me.

"Actually there is a faster solution to this(but has a potential disadvantage).

You just need to copy the .Xauthority file from the home directory of the user you have logged in to the root's homefolder.

As root do:
cp /home/username/.Xauthority /root/

Note that this allows the root to launch x-programs from all the machines that the user is allowed(something you might not want to do).

Since xdm creates a new mit-magick-cookie the Xauthority every time it is launched this should be done every time you restart X (or reboot)."

---

### Post by timcredible on 2008-07-11
if you want, run xNest instead of individual apps so you can get the normal desktop.  

```
ssh -X user@host
after login,
xNest :30 -display 0:0 -query localhost
```

it's been a while since i've done this over ssh tunnel, so the 0:0 may be something else when using ssh, i forget.

---

### Post by Wayfarer247 on 2008-07-11
Success!  I deleted the file, and now it works!  Hurray for me!  Thank you, thank you.

So.... now, I'm always looking for more.  I would like to have a complete desktop view of the computer I am sshing into.  I tried running xNest (on the server and my laptop) but it didn't recognize the command.  Is there some other way to get the entire desktop to appear?  I tried "gnome-session" but that didn't end well.  :D

Ideas?

And thank you again for getting me this far!

---

### Post by Wayfarer247 on 2008-07-11
*Bump*

Unbelievable how many people post on this forum!

---

### Post by Wayfarer247 on 2008-07-11
*Bump*

---

### Post by neurostu on 2008-07-11
Is there any particular reason why you need to do it over ssh?  If you want to get access to the Desktop you should probably consider using VNC.  

I personally only used X forwarding to forward individual applications, and used VNC when I wanted the desktop.

---

