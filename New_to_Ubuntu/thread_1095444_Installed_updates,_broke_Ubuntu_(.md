---
title: "Installed updates, broke Ubuntu :("
date: 2009-03-13
forum: New to Ubuntu
---

### Post by jaguax on 2009-03-13
lol, I just keep running into more and more problems, but I suppose that comes with being new to Linux.

I installed the 279 updates that popped up, then I restart and the nvidia video drivers seem to have been messed up so I have to revert to basic graphics mode.

So I figure that reinstalling the video drivers can't hurt.

I use this process to install the drivers:

Downloaded the *.run file from Nvidia.
Used CTRL ALT F1 to open a terminal.
Used sudo /etc/init.d/gdm stop to stop the x server.
Installed drivers using sh blah.run

Then I restart the computer and it boots into the [dos-like] terminal rather than the graphical GNOME evironment. I can't seem to get back into graphical mode. What did I do??? :(

---

### Post by martrn on 2009-03-13
Use :

```
sudo /etc/init.d/gdm start
```

to restart the x11 server

---

### Post by taurus on 2009-03-13
Which release are you running, hardy or intrepid?

Did you install an nvidia driver for your graphic card before you did the "big" updates?

What happens if you try to start X from the prompt, after you have logged in?

```
startx
```

---

### Post by Miljet on 2009-03-13
When you issued the command:

```
 sudo /etc/init.d/gdm stop 
```

you stopped the gui. 

So I would try:

```
 sudo /etc/init.d/gdm start 
```

to start it again

---

### Post by jaguax on 2009-03-13
Yeah I tried the start thing. It said something like starting GNOME and then it said [OK]. Still no GUI though.

startx gave me some kind of error, I'll post back with the details...

How do I know which release I have?

edit - And yes I installed the original nvidia driver before the big updates. I also noticed that after the updates it added another version of Ubuntu in the boot menu.

---

### Post by martrn on 2009-03-13
> **jaguax said:**
> .. How do I know which release I have? ...

type

> uname -r

and it should tell you what version of the kernel you are running.

---

### Post by taurus on 2009-03-13
> **jaguax said:**
> 
How do I know which release I have?


> **martrn said:**
> type

and it should tell you what version of the kernel you are running.

```
lsb_release -a
```

---

### Post by jaguax on 2009-03-13
I fixed it by reinstalling the video driver yet again, starting gnome, then using startx. Go figure.

---

