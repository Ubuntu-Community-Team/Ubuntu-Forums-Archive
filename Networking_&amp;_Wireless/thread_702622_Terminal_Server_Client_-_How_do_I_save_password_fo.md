---
title: "Terminal Server Client - How do I save password for VNC connection?"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-02-20
Ubuntu's built in Terminal Server Client:

When I select to use a VNC connection (which is all I use it for actually) I can't type anything into the Password area.

At the top I have the name of the computer I'm connecting to.
Then the Protocol (VNC)

My Username (which is filled in)

But the next line PASSWORD is greyed out.

All I can do it hit the CONNECT button which causes the main window to go, and a small window to pop up, with USERNAME (which is greyed out) and Password, which I have to click in and type my password. Every Single Time!

It only seems with VNC that the password line is greyed out in the main panel.

Does everyone have this?
Anyway to save my password?

Thanks.

---

### Post by freelinuxhelp on 2008-02-20
I don't think that tsclient will let you save a password, but as it is simply a front end for rdesktop and vncviewer, you could write a script that calls vncviewer with the appropriate parameters.
Try this in a terminal window for more info.
```
vncviewer --help
```

---

### Post by freelinuxhelp on 2008-02-21
Have you had any luck with this?

---

### Post by PiggiePaul on 2008-02-21
> **freelinuxhelp said:**
> Have you had any luck with this?

Thanks for the follow up and I did what you said from the terminal, had a wild stab in the dark, but at my current level I'm not really up to getting this working this way.

Perhaps at a later date when I'm more used to using the command line.

---

### Post by freelinuxhelp on 2008-02-21
There's no better way to learn it than to dive right in.
:-)

---

