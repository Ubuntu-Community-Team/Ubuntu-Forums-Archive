---
title: "Ubuntu 20.04 + LXDE + XRDP : Blank Desktop (no decorations or menus)"
date: 2021-01-14
forum: Networking &amp; Wireless
---

### Post by Conzar on 2021-01-14
I have been using lubuntu with LXDE and XRDP successfully with Ubuntu 16.04 and 18.04.  After upgrading to Ubuntu 20.04, logging in via rdp produces a single terminal without any windows, window decorations, menus, or docks.

[[IMG]https://i.imgur.com/41FLkwLm.png[/IMG]]("https://i.imgur.com/41FLkwL.png")
[https://i.imgur.com/41FLkwL.png]("https://i.imgur.com/41FLkwL.png")

Note, I have tried this with a fresh install of Ubuntu 20.04.

**Orchestration**

Here are the packages that I install:

[LIST]
[*]xrdp
[*]lubuntu-desktop
[*]lxde
[*]tightvncserver
[/LIST]

The /etc/xsession_global file contains the following:
```

lxsession -e LXDE -s Lubuntu

```

The /etc/X11/Xsession file has been updated with the following:
USERXSESSION=/etc/xsession_global


**LOG FILES**

xsession-errors
[https://pastebin.com/epEwdA0w](https://pastebin.com/epEwdA0w)

run.log
[https://pastebin.com/PrDgdf31](https://pastebin.com/PrDgdf31)

Any ideas what is different about Ubuntu 20.04 that might cause this issue?

---

### Post by guiverc on 2021-01-15
Lubuntu hasn't used LXDE since Lubuntu 18.04 LTS.

If you look at `lubuntu-desktop` ([https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)) you won't find any LXDE packages there.

Lubuntu since 18.10 uses the LXQt desktop; GTK2 being declared EOL, the LXDE devs joining with the Razor-Qt team creating the LXQt project. If you want more details, I'd recommend [https://phab.lubuntu.me/w/faq/](https://phab.lubuntu.me/w/faq/)

Your details in `/etc/xsession_global`refers to a Lubuntu session, which I would not use as Lubuntu is now LXQt, and any configuration settings now in Lubuntu won't help LXDE.  I would instead use the default LXDE.

Yes Lubuntu still uses Openbox, but there will be nothing useful for a LXDE session found in the `lubuntu-desktop` configuration wise, only potential issues, so I don't understand why you added it if you intend using LXDE and not Lubuntu/LXQt.   They are different desktops.

---

### Post by Conzar on 2021-01-17
> **guiverc said:**
> Lubuntu hasn't used LXDE since Lubuntu 18.04 LTS.

If you look at `lubuntu-desktop` ([https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)) you won't find any LXDE packages there.

Lubuntu since 18.10 uses the LXQt desktop; GTK2 being declared EOL, the LXDE devs joining with the Razor-Qt team creating the LXQt project. If you want more details, I'd recommend [https://phab.lubuntu.me/w/faq/](https://phab.lubuntu.me/w/faq/)

Your details in `/etc/xsession_global`refers to a Lubuntu session, which I would not use as Lubuntu is now LXQt, and any configuration settings now in Lubuntu won't help LXDE.  I would instead use the default LXDE.

Yes Lubuntu still uses Openbox, but there will be nothing useful for a LXDE session found in the `lubuntu-desktop` configuration wise, only potential issues, so I don't understand why you added it if you intend using LXDE and not Lubuntu/LXQt.   They are different desktops.

Ok, I have installed the following instead:

[LIST]
[*]xrdp
[*] lubuntu-lxqt-desktop
[*] lxqt
[*] tightvncserver
[/LIST]

How do I start lxqt?

For LXDE, I used the following:

```

lxsession -e LXDE -s Lubuntu'

```

lxsession is a LXDE command.  I have tried lxqt-session but that fails.

---

### Post by Conzar on 2021-01-17
I tried startlxqt which seems to work.  I selected mutter but when I click on virtual desktop 2 or 3, the screen stop rendering anything except the desktop background.  Any ideas?

---

### Post by Conzar on 2021-01-17
If I select openbox then xrdp works!  Thank you, marking solved.

---

### Post by guiverc on 2021-01-17
You might want to check your installed packages, I see no package `lubuntu-lxqt-desktop`

[https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-lxqt-desktop](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=lubuntu-lxqt-desktop)

and if are/were installing `lubuntu-desktop`, I don't see why you then installed the meta package `lxqt` ... if your intention is trying to achieve a minimal install, check out [https://discourse.lubuntu.me/t/what-happened-to-the-meta-mackage-lubuntu-core-in-20-04-lts/1045](https://discourse.lubuntu.me/t/what-happened-to-the-meta-mackage-lubuntu-core-in-20-04-lts/1045)

---

