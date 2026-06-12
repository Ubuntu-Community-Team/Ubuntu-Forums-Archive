---
title: "msttcorefonts package broken"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by alexlafreniere on 2009-07-15
Hi all,

I have tried installing the msttcorefonts package multiple times on multiple installations of Xubuntu, and the installer always gets stuck downloading andale32.exe. Here's an excerpt from the terminal:

```

--2009-07-15 08:01:50--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.

```

The installer repeats this about ten times before finally giving up and quitting.

After I try installing the package and it inevitably fails, I get a crash report notifier in my panel that annoys me every single time I boot, and I have absolutely no idea how to remove it. The msttcorefonts package has always served me well, and I don't know why it would suddenly stop working. Any help with this would be greatly appreciated.

---

### Post by AbtZ on 2009-07-15
You might already have thought about this, but have you tried downloading the package from a different server?

System->Administration->Synaptic Package Manager

Then
Settings->Repositories

Now click the rolldown menu after "Download from:", select "Other" and select another server to try.

You could also try the "Select best server" button, as it may change your server; I live in Sweden, but my best repo server apparently is in Denmark.

---

### Post by alexlafreniere on 2009-07-15
I have tried that, even on different systems and fresh installs, same thing happens. The installer can't fetch andale32.exe and consequently crashes.

---

