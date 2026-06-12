---
title: "Update manager not showing new release"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-08-14
My update manager is not displaying the notice for Lucid Lynx. I have the default settings - Show new distribution releases for all normal releases. 

Is there anything wrong? I know there are other ways to upgrade my system, I'm just worried that my update manager is not displaying all the updates. 

Thanks

---

### Post by Windflower. on 2010-08-17
I have the same problem....

---

### Post by bkratz on 2010-08-17
> **Windflower. said:**
> I have the same problem....

Have you gone to System>>Administration>>Software sources then selected Updates and is "Check for updates " set to daily "

---

### Post by Calash on 2010-08-17
What version are you running now?

---

### Post by Fifthmarch on 2010-08-18
Check for updates IS set to daily. Otherwise, I won't get notifications for any update! My problem is that I see everything else except the new distribution release. 

Currently running Karmic

---

### Post by Spice Weasel on 2010-08-18
> sudo apt-get dist-upgrade

^ Does this work? ^

---

### Post by boof1988 on 2010-08-18
> **Spice Weasel said:**
> ^ Does this work? ^

The code...
```
sudo apt-get dist-upgrade
```
... will only perform the package updates within the same version.  And does not upgrade to a newer distribution.

I'm not sure which command line code will upgrade to the newer version (i.e. Karmic to Lucid).

EDIT:
See...
```
man apt-get
```

---

### Post by KdotJ on 2010-08-18
try this...

Press Alt+F2 to get up the run dialog window, and type:

```
update-manager -d
```

After the update manager window opens, you may have to give it a few seconds for it to show the available upgrade

---

### Post by Fifthmarch on 2010-08-21
I don't know what happened, but the issue resolved by itself. Thanks, though!

---

