---
title: "vnc packages"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by tullmejs on 2009-01-26
Hi, I have installed xubuntu and want to use vncserver. Now, if I type vncserver in terminal window, I am told that vncserver is not installed but can be found in two packages, tightvnc & vnc4server.

Cool.

But I do not find those packages, nor any other containing VNCserver, seeking for it or them in synaptic and the add/remove thing.

Please explain, why does not those two packages show? (I only see a couple of viewers)

(I post in absolute beginners since part of the confusement is not understanding packages management. I do find the app online.)

---

### Post by jpoRS on 2009-01-26
I don't know if it will be different for Xubuntu (I doubt it will be but I just wanted to put that disclaimer out there).

Try putting this into a terminal:

```
apt-cache search vncserver
```

this searches the available packages for install and should show what you are looking for

If that does show the program you are looking for, type in

```
sudo apt-get install "program name"
```

Then enter your password, and it should install the program.

After that you should just be able to run the program from terminal.

Good luck!
jim

---

### Post by tullmejs on 2009-01-26
That was smooth, thanks! 

But still, what packages can be found in / by Synaptic, what is the logic  behind it?

---

### Post by jpoRS on 2009-01-29
I am not sure what the hard rule is, but I believe Synaptic only shows GUI packages, whereas the terminal method I recommended has access to everything.

Again, I am not positive that that is the case, but that is the impression that I have been given.

Glad things are working for you, and enjoy,
jim

---

### Post by cariboo on 2009-01-29
You may want to update your package list, when I type vnc in synaptics quick search bar, checkout the screenshot for the results I get. To refresh the package list click the reload button.

Jim

---

### Post by tullmejs on 2009-01-29
> **jpoRS said:**
> I am not sure what the hard rule is, but I believe Synaptic only shows GUI packages, whereas the terminal method I recommended has access to everything.

Again, I am not positive that that is the case, but that is the impression that I have been given.

Glad things are working for you, and enjoy,
jim

Thank you :-)

> **cariboo907 said:**
> You may want to update your package list, when I type vnc in synaptics quick search bar, checkout the screenshot for the results I get. To refresh the package list click the reload button.

Jim

First I tried, and still got just two hits for vnc. Then, I am not sure why, I reloaded again - and then I got the lot. Curious, but nice all the same. Thanks!

---

