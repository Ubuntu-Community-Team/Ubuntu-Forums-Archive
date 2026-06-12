---
title: "messed up screen"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by bob brazie on 2011-02-12
Ubuntu 10.10.

Does this look like a hardware or a software problem?

I don't know if a fresh install aloud cure this or not.

Thanks in advance. Bob

---

### Post by davidmohammed on 2011-02-12
have you loaded a newer kernel than the default kernel that comes with maverick?

Maybe you've been playing with new graphics drivers - have you got the x-edgers or x-swat ppa enabled?

---

### Post by quadproc on 2011-02-12
> **bob brazie said:**
> Ubuntu 10.10.

Does this look like a hardware or a software problem?


We could use a little more info to help narrow down the possibilities.  I *think* that you have a software problem but let's try to figure it out.

Did you get that kind of behavior when you logged in (assuming that you set up your system to require a login)?

Does that behavior occur every time you log in?

Does that behavior occur if you do a restart without turning the power off?

Does the problem go away as you use the system?

Does your system behave normally when you use a command line (e.g., ctrl-alt-F1)?

What graphics driver are you using?

What graphics hardware are you using?

You might be seeing a problem which I have with 10.10, namely that sometimes something goes wrong with the startup and just before the login screen should appear, I get corrupted video.  I am presently running the default Mesa driver.  I filed a bug report on this; it is launchpad bug # 711056.

quadproc

---

### Post by metalf8801 on 2011-02-12
You can find out if its a hardware problem by booting from a live CD/DVD and seeing if you get the same results. Otherwise see what quadproc wrote

---

### Post by bob brazie on 2011-02-12
I haven't been playing with any new drivers.

The Kernel is the updated one that came trough the normal updates.

Do I find the PPA's under software sources and what specifically am I looking for.

Thanks, Bob.

---

### Post by bob brazie on 2011-02-12
We could use a little more info to help narrow down the possibilities. I think that you have a software problem but let's try to figure it out.

Did you get that kind of behavior when you logged in (assuming that you set up your system to require a login)?

-I log in automatically at start-up-

Does that behavior occur every time you log in?

-every time I re-boot-

Does that behavior occur if you do a restart without turning the power off?

-don't know yet-

Does the problem go away as you use the system?

-no-

Does your system behave normally when you use a command line (e.g., ctrl-alt-F1)?

-don't know yet-

What graphics driver are you using?

-not sure how to tell-

What graphics hardware are you using?

-not sure how to tell-

You might be seeing a problem which I have with 10.10, namely that sometimes something goes wrong with the startup and just before the login screen should appear, I get corrupted video. I am presently running the default Mesa driver. I filed a bug report on this; it is launchpad bug # 711056.

-do you have a link to this bug report I could use?-

quadproc

---

### Post by quadproc on 2011-02-12
I asked:  What graphics driver are you using?
> 
-not sure how to tell-
There are a few ways to find out.  I suggest using the hardinfo program; if you don't have it already installed then you can get it using Synaptic.  Run hardinfo from a terminal and choose the Display selection then scroll down to the OpenGL category and look at the Renderer entry.  If you are using the default Mesa driver in Ubuntu 10.10 it will say Mesa.

I asked: What graphics hardware are you using?
> 
-not sure how to tell-
You should be able to get that from running
```
lspci | grep VGA
```That should produce a little text which identifies your graphics hardware.
> 
-do you have a link to this bug report I could use?-
Based on your responses I do not think that you are seeing the same problem, but here is how you can access launchpad:
[https://launchpad.net](https://launchpad.net)
In the search box, enter the bug number (711056 in this case).  Then click on the exact match.  You can read the description and compare with your symptoms.

quadproc

---

