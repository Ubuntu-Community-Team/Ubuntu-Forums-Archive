---
title: "Can't find the open window bar!"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Dula on 2009-10-09
I am an absolute beginner with Ubuntu 9.04.  Recently I was using the virtual desktop, but I think something went wrong.  Now, when I open Ubuntu I cannot see the bar at the bottom of the desktop which tells me which windows are open and what programs are running.  Can anyone help me find it?  What should I do?  BTW, I haven't changed any monitor settings.

---

### Post by macabrem on 2009-10-09
> **Dula said:**
> I am an absolute beginner with Ubuntu 9.04.  Recently I was using the virtual desktop, but I think something went wrong.  Now, when I open Ubuntu I cannot see the bar at the bottom of the desktop which tells me which windows are open and what programs are running.  Can anyone help me find it?  What should I do?  BTW, I haven't changed any monitor settings.


Are you able to right click on the desktop and get a menu?  Can you put folders and icons on the desktop - or if you already had some there, are they visible?

Also, what hardware are you using?  Is it a netbook by any chance?

---

### Post by Dula on 2009-10-09
I can get a menu by right clicking and my USB drive shows up on the desktop.  I'm using a Dell Dimension 3000 desktop with onboard graphics (ie: not a PCI card) and an HP L1706 monitor.  Everything worked in the past, so I think it has something to do with the switchable virtual desktops included in Ubuntu.  Incidentally, I'm using the Gnome environment.

---

### Post by macabrem on 2009-10-09
Hmm, I'm really not sure.  I hope somebody else can chime in.  But, I've seen some people suggest opening a terminal and typing:

```
gnome-panel
```

I've had a problem with this before, but in addition, no icons would display on my desktop and I couldn't right click to get a menu on the desktop.  

What I did was ensure all users were logged out, deleted the offending account, and re-created it.  Made sure everything was displaying correctly, and the restarted one more time just to ensure my panels were working correctly...

---

### Post by Dula on 2009-10-09
Thanks macabrem.  The gnome-panel didn't work, it returned that a shell was already running.  However, I simply created a new user account and now the screen is back to normal.  Thanks for your help.

---

### Post by CatKiller on 2009-10-09
> **Dula said:**
> Now, when I open Ubuntu I cannot see the bar at the bottom of the desktop which tells me which windows are open and what programs are running.  Can anyone help me find it?  What should I do?  BTW, I haven't changed any monitor settings.

Have you lost the whole panel, or just the Window List? Do you still have your top panel?

If you've got the bottom panel but no Window List, you can right-click on the panel and select Add to Panel... &#8594; Window List.

If you've got the top panel but you've erroneously deleted the bottom panel, you can right-click on the top panel and select New Panel.

If you've got no panels at all, you need to restart them them by running **gnome-panel**.

If your panel configuration is completely FUBARed then you can restore the panel settings to their defaults with ```
gconftool-2 –recursive-unset /apps/panel gnome-panel
```

Switching workspaces doesn't generally kill the panel, although it's possible that you've got "show windows from current workspace" set rather than "show windows from all workspaces" in your Window List. You can right-click on the Window List handle and select Properties to change this option.

It's difficult to give any more concrete advice without a clearer description of the problem you're experiencing.

---

