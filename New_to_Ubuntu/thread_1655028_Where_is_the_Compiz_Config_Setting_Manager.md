---
title: "Where is the Compiz Config Setting Manager?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by sauwen on 2010-12-29
So, it's been awhile since I played with the compiz program.  I remember it being under System -> Preferences -> CompizConfig Settings Manager.  Now it is gone.  However, my ubuntu software center says that I have installed the program.  I've tried the Alt+F2, ccsm, but nothing comes up.  I don't know if after such a long time, one of the Ubuntu updates messed around with the program?

Any suggestions?

Thanks!!! :KS

---

### Post by MartyBuntu on 2010-12-29
Can you pull up the icon?

**Applications--->System Tools--->Compiz Fusion Icon**

It should then show the Compiz icon in your taskbar.
You can right-click the icon and select **Settings Manager.**

---

### Post by matt_symes on 2010-12-29
Hi

Open a terminal and type 

```
ccsm
```

Post back any errors.

Also, from a terminal, type...

```
which ccsm
```

and post back the response.

Kind regards

---

### Post by corncob on 2010-12-29
Go to System > Preferences > Main Menu (or type alacarte in the terminal). Once there go to System > Preference and make sure the box for CompizConfig Settings Manager is checked,

---

### Post by philinux on 2010-12-29
> **sauwen said:**
> So, it's been awhile since I played with the compiz program.  I remember it being under System -> Preferences -> CompizConfig Settings Manager.  Now it is gone.  However, my ubuntu software center says that I have installed the program.  I've tried the Alt+F2, ccsm, but nothing comes up.  I don't know if after such a long time, one of the Ubuntu updates messed around with the program?

Any suggestions?

Thanks!!! :KS

Just to clear things up!
It is not installed by default now even though compiz itself is. Either use software centre or synaptic or open a terminal.

```
sudo apt-get install compizconfig-settings-manager
```

It then appears in System>Prefs

---

