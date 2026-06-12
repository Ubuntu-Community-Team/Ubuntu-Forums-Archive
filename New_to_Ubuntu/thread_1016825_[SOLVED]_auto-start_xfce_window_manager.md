---
title: "[SOLVED] auto-start xfce window manager"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2008-12-20
After messing around abit with compiz, I decided to not have compiz and emerald due to lack of system resources. The problem now is that I have no idea how to start the default xfce window-border manager start. Firefox also auto-starts at each log-in, though that may be unrelated.

Help please?

---

### Post by stoogiebuncho on 2008-12-20
This really depends on how you set compiz to start up by default.  Do you remember how you did it?

There are a couple of things to try if you can't remember.

1.  Go to Applications->Settings->Autostarted applications, and see if you changed anything there.  You would look for something that said "compiz --replace" or "emerald --replace".  If you see either of those, remove them.

2. I found this on a website explaining how make compiz start by default on Xubuntu:
> The more-difficult-but-better way

So… You prefer the scary stuff? Well, it’s not that difficult, actually. You just press Alt+F2 and enter

gksudo "mousepad /etc/xdg/xfce4-session/xfce4-session.rc"

Basically, that opens the file xfce4-session.rc with root rights with the text editor mousepad.

In this file, all you have to do is replace:

Client0_Command=xfwm4

…with:

Client0_Command=compiz

So it would make sense that doing the opposite would switch you back to XCFE's default window manager.  So open a terminal, and enter

```
gksudo "mousepad /etc/xdg/xfce4-session/xfce4-session.rc"
```

Then replace the 

Client0_Command=compiz

with

Client0_command=xfwm4

3.  One other thing you could try would be to open up your Synaptic Package Manager and just uninstall compiz and emerald.

---

### Post by stoogiebuncho on 2008-12-20
Oh, and for the firefox issue, I'd start by looking in the autostarted apps area as well.  It's probably there somewhere.

---

### Post by Mr.Kuchinawa on 2008-12-20
Thanks, I just typed in "xfwm4" in the terminal and everything seem to work fine.

---

### Post by SynonM on 2012-01-29
Very helpful. Thanks for listing that last command. Other than the occasional login problem where the window manager doesn't load, I really like xfce.

Good command, it's very useful, and hey, I say the simpler, the better.


:KS

---

