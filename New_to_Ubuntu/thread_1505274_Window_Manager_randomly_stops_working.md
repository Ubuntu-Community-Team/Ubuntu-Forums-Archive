---
title: "Window Manager randomly stops working"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by pizza-is-good on 2010-06-08
Hi there,
a coworkers window manager randomly stops working, and the window decorator disappears, making the whole desktop useless. Can't switch workspaces nor close windows. It is fixed by a log out and logging in again. But it happens again.

I had the same problem some time ago, but I just went with a fresh install. He can't do that, as the servers he manages are all configured through that computer.

He has compiz installed.

I'm just looking for a way for when this happens again, he can restart the window manager without having to log out, so that he does not loose productivity.
Something he can do in the terminal???

If there is a permanent fix, that'd be appreciated too.

Thanks,

~pizza

---

### Post by 4Orbs on 2010-06-09
On my system there was one sure-fire way to make the window frames disappear. That was to change screen resolution while compiz effects were enabled.

---

### Post by Peter09 on 2010-06-09
Its not the window manager as much as the windows decorator. If you go into compiz-settings manager and look in the windows decorations (not at my machine so unsure here) you can see the task that does it. Sometimes people replace the standard one with emerald.
 
Next time it time it crashes try opening a terminal and typing
 
```
<name of the task he uses> --replace
```
 
Sorry I cannot be more specific.
 
Note; This may be a problem with a corrupt theme that he is using, try getting him to change the theme.

---

### Post by philinux on 2010-06-09
> **pizza-is-good said:**
> Hi there,
a coworkers window manager randomly stops working, and the window decorator disappears, making the whole desktop useless. Can't switch workspaces nor close windows. It is fixed by a log out and logging in again. But it happens again.

I had the same problem some time ago, but I just went with a fresh install. He can't do that, as the servers he manages are all configured through that computer.

He has compiz installed.

I'm just looking for a way for when this happens again, he can restart the window manager without having to log out, so that he does not loose productivity.
Something he can do in the terminal???

If there is a permanent fix, that'd be appreciated too.

Thanks,

~pizza

Well to stop it happening turn off compiz. System>prefs>appearance>visual effects> Set it to none.

Also look in system>admin>hardware drivers and see if a driver is Recommended.

---

### Post by pizza-is-good on 2010-06-09
Thanks for the replies fellas. I'll have him give them a try.

What is weird is that these problems were happening before I installed compiz on it. I installed compiz hoping to get rid of the problem, and it did, for about a week.

This makes me think that Peter09 might be right, and it is the theme.

---

