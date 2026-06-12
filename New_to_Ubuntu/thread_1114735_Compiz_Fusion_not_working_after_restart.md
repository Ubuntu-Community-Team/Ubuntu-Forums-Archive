---
title: "Compiz Fusion not working after restart"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Gp. on 2009-04-03
Hi,
For some reason compiz fusion just doesn't work after I restart.

I have to right click on the compiz icon and choose "reload window manager" to get it working again...

Seems it's all corrupt or something, and I don't get why?

---

### Post by Lunx on 2009-04-03
Just check your visual effects setting under system preferences, sometimes this changes for no apparent reason, happened to me a couple of times in Intrepid. Not sure this is the solution, but someone the other day had similar problem and this fixed it.

Edit: Sorry, re-read OP and since you can eventually get it to work I doubt my post helps much. Maybe consider removing and reinstalling?

---

### Post by schmidtbag on 2009-04-03
I've had similar issues, but what I noticed is I just made some tiny changes that ruined the whole thing.  If you don't know what a feature is but you know it isn't an effect, don't change it.

At least you don't get the issue I have, which is compiz will randomly decide I don't have the a rasterizer and will just refuse to start up.

---

### Post by lexe-cc on 2009-04-03
i had some similar issues lately, but im not sure if this is the same problem. 
Despite i actived compiz via "appearance" it didnt start.

I also had a session for fusion-icon. (command: "fusion-icon -n")
-n makes sure it doesnt reload the windowmanager. (if compiz is the default window manager it reloads when fusion-icon has started, you should see some flikkering)

anyhow, the correct way to use compiz as your default windowmanager should be like this:
1) in sessions (jaunty: startup apps) you create a entry with the command "fusion-icon -n"
2) hit "alt+F2" and type "gconf-editor", run it
3) navigate to: "/desktop/gnome/session/required_components" and set windowmanager to "compiz" (dont know if this is the same for intrepid, im on jaunty beta, normally it should)
4) navigate to: "/desktop/gnome/applications/window_manager" and set default to "/usr/bin/compiz"

hope this works

cheerio!

---

### Post by LowSky on 2009-04-03
try using this command from terminal

```
compiz --replace
```

---

### Post by Gp. on 2009-04-06
Yeah I've tried all these things, even re-installed and it works for the session but after restart it's not working again. I think I'll be reinstalling, but using Mint.

---

### Post by presence1960 on 2009-04-06
> **LowSky said:**
> try using this command from terminal

```
compiz --replace
```

Go to System > Preferences > Sessions. Under Start up apps tab click add and use the command LowSky posted.

---

