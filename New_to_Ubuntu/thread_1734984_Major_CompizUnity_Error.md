---
title: "Major Compiz/Unity Error"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by lockettowl on 2011-04-20
I just did something stupid that I knew I shouldn't have. I tried to figure out how to use the "Desktop Cube" feature with Unity, and now it appears that I have no windows manager and no way to open applications.

What do I do?

---

### Post by rcayea on 2011-04-20
Can you Ctrl+Alt F1?

If so, you could try to go there and simply apt-get remove compiz.

---

### Post by Larkspur on 2011-04-20
Or compiz --replace, which will show if the problem is temporary.

---

### Post by lockettowl on 2011-04-21
> **rcayea said:**
> Can you Ctrl+Alt F1?

If so, you could try to go there and simply apt-get remove compiz.

I did this, and it appears that compiz was removed, but I still don't know how to turn unity back on.

---

### Post by Toafan on 2011-04-21
> **lockettowl said:**
> I did this, and it appears that compiz was removed, but I still don't know how to turn unity back on.
Did you try rebooting yet? It's amazing how often that'll solve a problem :)
Otherwise, I'm not sure. You might be able to kick-start your GUI from the command line (same place you removed compiz) by entering the command-line name of the windowing system/manager (eg if you had KDE installed, you might try running 'kde' on the command line. I don't recommend installing anything for that purpose, however).  Try looking for a man page for unity (man unity) and seeing if it tells you what to run.

---

### Post by r-senior on 2011-04-21
> **rcayea said:**
> Can you Ctrl+Alt F1?

If so, you could try to go there and simply apt-get remove compiz.

I'm curious as to what the thinking is here? Attempts to enable the cube can disable the Unity plugin in Compiz. Resetting Unity should re-enable it. Alternatively, logging in again with a Classic desktop session would allow recovery via a Gnome desktop by running CCSM again. What's the idea of removing Compiz? Unity depends on Compiz.

---

### Post by camurgo on 2011-04-21
> **lockettowl said:**
> I just did something stupid that I knew I shouldn't have. I tried to figure out how to use the "Desktop Cube" feature with Unity, and now it appears that I have no windows manager and no way to open applications.

What do I do?

I've updated from 10.10 to 11.04 just now, and then tried the same things as you.. and had the same problem.

I gave up on messing with desktop cube, for now. I got my windows manager back on by running 'unity --reset' on the terminal.

---

### Post by lockettowl on 2011-04-21
> **Cameigons said:**
> I've updated from 10.10 to 11.04 just now, and then tried the same things as you.. and had the same problem.

I gave up on messing with desktop cube, for now. I got my windows manager back on by running 'unity --reset' on the terminal.

Thanks. This worked perfect.

---

