---
title: "How do I stop VINO ? - or all GUI related programs for that matter.... (Xubuntu)"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by flameproof on 2010-11-10
I want to close all GUI related applications and run Xubuntu as a pure webserver and control it via SSH. I want to control that then with a start.sh and stop.sh script.

First issues I face, how do I stop vino-server? This does **not** work:

/usr/lib/vino/vino-server stop

And while I am at the topic, what else I can close down, and how? 

I guess XCFE is not needed too. How do I close that?

---

### Post by sandyd on 2010-11-10
> **flameproof said:**
> I want to close all GUI related applications and run Xubuntu as a pure webserver and control it via SSH. I want to control that then with a start.sh and stop.sh script.

First issues I face, how do I stop vino-server? This does **not** work:

/usr/lib/vino/vino-server stop

And while I am at the topic, what else I can close down, and how? 

I guess XCFE is not needed too. How do I close that?

easy.
```

sudo apt-get remove xserver-xorg-core
```

---

### Post by flameproof on 2010-11-10
> **sandyd said:**
> easy.
```

sudo apt-get remove xserver-xorg-core
```

Oh, I made a mistake here! I don't want to remove the GUI forever, just for the current session till reboot.

I want to use the PC sometimes as a desktop (at least till I'm really comfortable with command line). So I want to start the PC as a normal desktop (it has no monitor, but I can use Vino to connect) - but then as an option I want to close all GUI related programs (incl. Vino) via SSH and keep only the basic server functions (Apache etc.).

---

### Post by sandyd on 2010-11-10
> **flameproof said:**
> Oh, I made a mistake here! I don't want to remove the GUI forever, just for the current session till reboot.

I want to use the PC sometimes as a desktop (at least till I'm really comfortable with command line). So I want to start the PC as a normal desktop (it has no monitor, but I can use Vino to connect) - but then as an option I want to close all GUI related programs (incl. Vino) via SSH and keep only the basic server functions (Apache etc.).

```

sudo update-rc.d -f xorg-common remove

```anytime you wanna enable it again

```

sudo update-rc.d xorg-common defaults

```
and I *think* its called xorg-common. I use gentoo, so make sure you double check.

---

### Post by grooverider on 2012-12-11
old threat, regardless maybe someone like me will come across it, to kill vino just type "killall vino-server" from the command line and the service will stop. vino comes back up again if you start the service manually from command line or reboot.

---

