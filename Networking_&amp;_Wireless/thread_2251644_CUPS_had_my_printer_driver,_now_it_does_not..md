---
title: "CUPS had my printer driver, now it does not."
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by NNitely on 2014-11-05
Installed Ubuntu server 14.04.1 LTS about a week ago, no problems.

When I configured CUPS thru the web interface on another network machine,
it found my printer driver with a little (recommended) flag next to it at the top of the list.
HP Laserjet P1505n - Worked like a champ too!

That's great, however... I really played around _a lot_ with Ubuntu and installed and configured a ton of garbage.
At this point I figured I would take it back to a fresh install and just install what I really needed.
It's a headless machine so, just this for now: SSH, Samba, Cups, Openfire.

Installed at this point:
SSH, Samba, Cups

Went to configure Cups, and alas... Nothing even close to my printer in the drop down list. (HP Laserjet P1505n)
I've tried other drivers that may be close, and no dice. Couldn't even print a test page.

[U]Why would it be listed once, and then never again?
[/U]
Also having a difficult time trying to get a PPD file.
Feeling like an idiot, and just want this to work again.

---

### Post by tgalati4 on 2014-11-06
Try installing *hplip*.  That should have most of the HP printer drivers.

---

### Post by NNitely on 2014-11-06
> **tgalati4 said:**
> Try installing *hplip*.  That should have most of the HP printer drivers.

Is it possible to install hplip without a GUI? This is where I'm banging my head against the wall.

---

### Post by tgalati4 on 2014-11-06
Open a terminal:

```
apt-cache policy hplip
```

To see if it is already installed.

```
sudo apt-get install hplip
```

Open a browser:  [http://localhost:631](http://localhost:631)

Use the "Administration" tab to add the printer.  Use your User name and sudo password to log in.

---

### Post by NNitely on 2014-11-06
That was too easy...
A million thanks, wow.

---

### Post by tgalati4 on 2014-11-06
Most things are in Linux.  You just have to know the magic.  I'm glad you can print now.  Now I can take a nap.

---

