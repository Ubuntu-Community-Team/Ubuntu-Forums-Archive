---
title: "Keeping a script running after exiting SSH session"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by NixNightmares on 2011-04-14
I have an Ubuntu 10.10 box that I'm currently using as a server, particularly a minecraft server. I SSH in, run 'sudo service gdm stop' (because I don't want gnome eating resources), then run my script. Is there anyway to keep a script running after exiting my SSH session? Is there a better way of doing this?

---

### Post by seawolf167 on 2011-04-14
Much better way = *screen*, can't ssh without it! ([how-to link]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/"))

```
man screen
```

---

### Post by grants on 2011-04-14
I herd there was a few commands that might do this. 

I think disown?

I' ran something in the the background with "&" at the end, that seemed to keep the process going. Check it with ps aux. Mine stayed running while closing my laptop lid for a few hours and when I opened it I seemed to still be logged in. Not sure why this is. 

I also tried doing the same thing from work and once I got home it killed the process. Not sure if this was because I was now on a new IP. 


I'd like to know the right way to do this though.

---

### Post by seawolf167 on 2011-04-14
> **grants said:**
> I' ran something in the the background with "&" at the end, that seemed to keep the process going. Check it with ps aux. Mine stayed running while closing my laptop lid for a few hours and when I opened it I seemed to still be logged in. Not sure why this is. 

The '&' at the end of your command frees that terminal to be used even though it has opened an application. Try starting your application with that then closing the terminal, the application still closes.

Same goes for opening a terminal and starting a script or process that runs in the terminal - if you log off, the terminal closes and the process stops.

You want *screen* as well, simply start screen, start your process, then detach the console containing the process [CTRL][A] - [D].

You can then keep that script/process running, and reattach to it later (see the previously linked how-to)

---

### Post by bodhi.zazen on 2011-04-14
In order of complexity:

nohup
disown
detach
screen 

```
nohup script &
```

---

### Post by NixNightmares on 2011-04-14
> **seawolf167 said:**
> Much better way = *screen*, can't ssh without it! ([how-to link]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/"))

```
man screen
```

Screen is absolutely perfect, I feel like there are so many more possibilities now. Thank you so much.

---

### Post by seawolf167 on 2011-04-14
No problem, happy SSHing!

---

