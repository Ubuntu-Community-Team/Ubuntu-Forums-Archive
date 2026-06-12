---
title: "How to start an Ubuntu system in console mode"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Lawand on 2009-02-10
I have recently installed Ubuntu 8.10,
and am reading the Linux User's Guide as an introduction.

Now I need to boot the system in console (text) mode to try out basic login/logout operation.

How do I do that?

---

### Post by donkyhotay on 2009-02-10
If you want to practice logging in and out with the CLI then I would recommend pressing ctrl-alt-f2 which will switch you out of the GUI. Pressing ctrl-alt-f7 will switch you back again. For non-learning regular usage of the terminal I would just open a terminal window right from the GUI. The only way to really 'start' ubuntu with a CLI is to boot into recovery mode but this isn't good for learning as it forces you into root.

---

### Post by Lawand on 2009-02-10
Thanks for the info,
but isn't there any way to actually start the system in text mode (without being forced into root) ?

---

### Post by boof1988 on 2009-02-10
> **Lawand said:**
> Thanks for the info,
but isn't there any way to actually start the system in text mode (without being forced into root) ?

You are probably not being "forced into root".  What are the indicators that you are operating as root?

You shouldn't have to use root to login at the command line.  Just use your usual *username* and *password*.

---

### Post by amauk on 2009-02-10
one way is to disable execution of GDM (the gnome display manager)

I do this when installing custom display drivers

Disable GUI
```
sudo chmod 644 /etc/init.d/gdm
```

Enable GUI
```
sudo chmod 755 /etc/init.d/gdm
```

---

### Post by donkyhotay on 2009-02-10
> **Lawand said:**
> Thanks for the info,
but isn't there any way to actually start the system in text mode (without being forced into root) ?

Not without disabling GDM, the method listed above is probably the easiest method of doing so without uninstalling your GUI. Personally though I wouldn't recommend doing that for 'training' since you might have problems turning it back on unless you know what you're doing. For learning about the CLI using ctrl-alt-f2 is your safest option that will teach you the most.  


> **boof1988 said:**
> You are probably not being "forced into root".  What are the indicators that you are operating as root?

You shouldn't have to use root to login at the command line.  Just use your usual *username* and *password*.

When you boot into recovery mode it automatically logs you in as root.

---

### Post by Lawand on 2009-02-10
> **boof1988 said:**
> You are probably not being "forced into root".  What are the indicators that you are operating as root?

You shouldn't have to use root to login at the command line.  Just use your usual *username* and *password*.

I got 5 options in recovery mode, which one should I choose?
[LIST]
[*]resume.....Resume normal boot
[*]clean.....Try to make free space
[*]fsck.....File system check
[*]root.....Drop to root shell prompt
[*]xfix.....Try to fix X server
[/LIST]

Because, when trying "resume" the system boots in GUI mode..

---

### Post by lazyart on 2009-02-10
Do as mentioned above.

Log into the GUI.

Once in, hit ctrl-alt-F2.  You will find a login prompt. Log in from there.  When you're all done type exit, then use ctrl-alt-F7 to return to gui.

This is easiest way in or out as it doesn't change anything.

---

### Post by Lawand on 2009-02-10
> **amauk said:**
> one way is to disable execution of GDM (the gnome display manager)

I do this when installing custom display drivers

Disable GUI
```
sudo chmod 644 /etc/init.d/gdm
```

Enable GUI
```
sudo chmod 755 /etc/init.d/gdm
```

This worked perfectly, thanks :)

---

### Post by boof1988 on 2009-02-10
> **donkyhotay said:**
> If you want to practice logging in and out with the CLI then I would recommend pressing ctrl-alt-f2 which will switch you out of the GUI. Pressing ctrl-alt-f7 will switch you back again.

If the user logs in after pressing ctrl-alt-f2, they are not logging in as root.

(Generally) When the prompt shows a "$" user is *user*, when the prompt shows "#" user is *root*.

> **Lawand said:**
> Thanks for the info,
but isn't there any way to actually start the system in text mode (without being forced into root) ?

There's no need to use the recovery mode (in this situation).  See lazyart's post.

---

### Post by OffAxis on 2009-02-10
I haven't used gnome in a while, but can't you just select 'Console' from the login screen under 'Session Type'?

---

