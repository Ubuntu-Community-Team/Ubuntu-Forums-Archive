---
title: "Starting kwrite using ssh -X -C how to determine which Window manager is used?!"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by gargl on 2015-09-25
Hi, I hope my question is getting relatively clear from the title.

I have two linux PCs A and B.
When I use ssh -X -C to log in on B (from A) and I start on B a program
(e.g. kwrite) is there any way to determine to say which window manager
should be used?

I ask because on the second machine is KDE 4.XX as well as an old KDE 3.XX (TDE)
window manager installed. Sometimes when I remotely start kwrite it uses
KDE 4 and another time it uses the older (for me preferred) KDE 3 version
on the remote machine (which also determines in which way the remotely
started program appears on machine A).

Do I have any options to determine which WM is used on the
remote machine!?

---

### Post by TheFu on 2015-09-26
The remote machine's WM has nothing to do with the local display. 
Only the local WM matters - that from the "X/Server" - on the machine you sit behind, physically.

The local X/Server is in charge of the display of widgets and all window dressing.  The remote system is the "X/Client" sending display, keybaord and mouse events to the local "server".

---

### Post by tgalati4 on 2015-09-26
When logged in and you get KD4 appearance, capture the following:

```
env
```

Then, when you get 3.5 appearance do the same.  Compare the two lists.  It's possible that an environment variable gets set which will modify the widget set used to display *kwrite*.  There is an ~/.ssh/rc file that you can specify X-Windows resources to modify your window behavior.  Take a look at it and see if it is defined and what is in it.

```
man sshd
```

---

### Post by gargl on 2015-09-30
Hey, sorry for my late response.
I've actually "solved" the problem, by navigating to the file using a file browser
(using ssh protocol) and open it. By that my local WM is used as well as doing
it this way the application also ofc feels a lot faster!

---

