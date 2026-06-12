---
title: "Make headless server beep when ready to login?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by flatland2d on 2009-08-22
I recently setup a headless home server that runs Jaunty (desktop version) to act as a file/backup/media server and the only annoying this is waiting around for the login screen to come up.  Since there is no screen, I just wait about a minute and try logging in.  I know I can hit the backspace key, which should cause a system beep if it is ready for me to log in (like when asking for username) but I was wondering if there was a way to make it beep automatically.  So basically, when you would normally here the drum sound (if you had speakers) I would like a system beep.  Is this possible?

Is there a better way to do this?  Is it possible to remotely log in through SSH?

Thanks for any advice!

---

### Post by RetchingRabbit on 2009-08-23
If it is doing server duty, why isn't it ALWAYS ready? Are you shutting it down at night or something?

---

### Post by flatland2d on 2009-08-23
I'm still in the process of getting it set up, and have to do an occasional reboot for testing.  The "why" is really irrelevant though.  I just want to know how.

---

### Post by nerr on 2009-08-23
Actually this is very easy to do!

```
sudo apt-get install beep
```

Then just add a command to your crontab to have the system beep at reboot!

```
@reboot beep -r 5
```

For example, the above code makes your machine beep five times when ready.  You can tweak beep a lot, or even use many beep commands together to play a melody when the machine is ready.

---

### Post by inobe on 2009-08-23
had an intel board that did this, it really depends on hardware and system bios features, really has nothing to do with operating systems.

it's a bios setting and the motherboard needs a speaker.

when entering the wrong password' it would also beep...


i have no more knowledge.

edit: haha, nice one nerr

---

### Post by flatland2d on 2009-08-23
> **nerr said:**
> Actually this is very easy to do!

```
sudo apt-get install beep
```

Then just add a command to your crontab to have the system beep at reboot!

```
@reboot beep -r 5
```

For example, the above code makes your machine beep five times when ready.  You can tweak beep a lot, or even use many beep commands together to play a melody when the machine is ready.

That is awesome!  It will be a very useful tool for monitoring a lot of other automated things I want to do.  Thanks for sharing!

---

### Post by 3rdalbum on 2009-08-23
On my home server (headless), X doesn't come up unless there is a monitor plugged in and turned on. How do you accomplish it?

---

### Post by inobe on 2009-08-23
xorg detects the monitor i presume, basically the server should text base CLI.

xserver/xorg may need editing or removed.

no graphical interface.

---

### Post by nerr on 2009-08-23
> **flatland2d said:**
> That is awesome!  It will be a very useful tool for monitoring a lot of other automated things I want to do.  Thanks for sharing!

You're welcome!  A friend and I actually enjoyed playing around with beep so much that we wrote a few little scripts that play some melodies.  You can use these as you please, but they're just a little more fun than the average beep.

[https://nerr.ath.cx/sftp/](https://nerr.ath.cx/sftp/)

---

### Post by HermanAB on 2009-08-23
Howdy,

I'm just wondering why you want need to log in?

If your machine is headless, then it should be running in runlevel 3.  It should boot up all the way and no login should be necessary.  to connect to it for remote administration, use SSH or Webmin.

---

