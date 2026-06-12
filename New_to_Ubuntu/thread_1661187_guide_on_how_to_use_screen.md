---
title: "guide on how to use screen?"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-01-06
anyone know of a guide on how to use screen? the man is not helpful i need to see some examples.

---

### Post by WRDN on 2011-01-06
I regularly use screen so I can ssh into my server, launch a download, then quit the ssh session.

My workflow:

Start screen:

```
screen
```

*Do something . . . .*

Detatch the screen by pressing **Ctrl + A then D**. The screen is still running in the background. It is a virtual tty.

I would then exit the ssh session. Later, if I wanted to check the progress of the job, I could ssh back into the server, and type:

```
screen -ls
```

This lists the current running screen sessions.

```
screen -r <session-name>
```

If only one screen is running, just typing "screen -r" will reattach it.
You can add the screen ID or fullname as a parameter to reattach to a specific screen.

Hope this helped.

WRDN

---

### Post by seawolf167 on 2011-01-06
Screen is pretty easy once you've used it a couple times.

Here are two links, the [first ]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/")is a basic how to, the [second ]("http://www.pixelbeat.org/lkdb/screen.html")is a list of the screen keyboard shortcuts

---

### Post by nothingspecial on 2011-01-06
Try the screen users manual

[http://www.gnu.org/software/screen/manual/screen.html](http://www.gnu.org/software/screen/manual/screen.html)

---

### Post by bodhi.zazen on 2011-01-06
Since your google seems to be broken

[http://www.pixelbeat.org/docs/screen/](http://www.pixelbeat.org/docs/screen/)

[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

---

### Post by Jebajseti on 2011-05-25
how to trigger with command which i would put in name.sh and ill make it to do cron job on every few hours

so how to do with command automaticly via name.sh file which will be execed with cron
screen -r
say mytext
and deatach from screen?

---

### Post by bodhi.zazen on 2011-05-25
screen -d -r your_program

See man screen and [http://fak3r.com/geek/howto/howto-start-a-detached-process-in-screen-on-boot/](http://fak3r.com/geek/howto/howto-start-a-detached-process-in-screen-on-boot/)

---

### Post by dieter-erich on 2011-05-28
Hi,
   does anybody know whether it is possible to also see different xwindows created during a SCREEN session? When I start a program in SCREEN that creates output in form of several xwindows, these are lost when resuming screen. I just see what happened inside the terminal. I'd like to have something like VNC but our cluster does not allow to install a VNC server......

Thanks for hints, D-E

---

### Post by bodhi.zazen on 2011-05-28
> **dieter-erich said:**
> Hi,
   does anybody know whether it is possible to also see different xwindows created during a SCREEN session? When I start a program in SCREEN that creates output in form of several xwindows, these are lost when resuming screen. I just see what happened inside the terminal. I'd like to have something like VNC but our cluster does not allow to install a VNC server......

Thanks for hints, D-E

Sounds as if you need to talk to your system administrator.

You might consider using ssh -X

---

