---
title: "Xubuntu 10.04, I pressed the little door in the upper right of the screen"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by displayaway on 2010-07-02
I just installed Xubuntu 10.04 (from the alt install disc) and enjoyed my first boot.
All seemed well until I pressed the little door in the upper right corner of the screen. Now the GUI has disappeared.

The only thing on screen is the blue background with the Trees and birds.
Left or Right mouse clicks do nothing.

The GUI does not reappear when I restart or shutdown. To do so, I must press the power button on the machine.  Upon login, the GUI does not appear if I choose xubuntu session or Xfce session.

The Ubuntu new user documentation does not discuss what is happening.

Can someone please explain to me
the keywords for the issues I am experiencing?  
I can't find answers when I don't know what to look for.

How do I get out of the twilight zone and back into Ubuntu?

---

### Post by cgroza on 2010-07-02
You should submit a bug report to launchpad. This could be a major bug!

---

### Post by cgroza on 2010-07-02
What happens when you press Ctrl+Alt+F1?

---

### Post by Rubi1200 on 2010-07-02
Have you tried

```
startxfce4

```
in the terminal?

---

### Post by displayaway on 2010-07-02
*What happens when you press Ctrl+Alt+F1?*
The same as when I press ctrl+alt+F2,[/br]
 it switches me to a console on tty1, tty2, etc.

No GUI, but otherwise the distribution seems fine. I can login and issue commands. Aptitude is able to reach the internet for repositories and perform updates. Though the upgrades did not solve my problem.

---

### Post by displayaway on 2010-07-02
> **Rubi1200 said:**
> Have you tried

```
startxfce4

```
in the terminal?

When I switch to console on tty1 and issue startxfce4, it responds with...

Fatal server error:
Server is already active for display 0

---

### Post by displayaway on 2010-07-02
OK, so I logged in by choosing xterm.

Issuing startxfce4 starts the GUI, but it is different than the Xubuntu GUI shown on first boot.
I only have one toolbar across the bottom. No upper toolbar. Graphic theme is different.

Unfortunately, rebooting and choosing Xubuntu or Xfce returns me to the missing GUI with unclickable blue trees.

How does it remember that I exited the GUI?
Where is the fact that I touched the little door stored?

---

