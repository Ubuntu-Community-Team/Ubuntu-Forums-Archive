---
title: "KDE pwmanager fails on Jaunty"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Billy Pilgrim on 2009-05-13
I posted the following message in a different area, and I think I should have put it in this area.   Any help would be greatly appreciated:

I was running Hardy, and upgraded to Jaunty, and the upgrade to new distribution went very smooth.

However, when it upgraded my KDE 3.X to 4.X I lost my KDE pwmanager (Password Manager). I still have my encrypted file with my passwords, but I can't seem to find the updated version of KDE pwmanager. Without the application, I can't access my encrypted password file, (which is giving me an anxiety attack, right now).

I typed "pwmanager" into the KPackageKit and it brought up "kde-pwmanager 1.2.4 Oubuntu4 (i386)", but had no focus on the "apply" button.

Reading through the description it said:

Package Name:
kde-pwmanager
Group:
Admin tools
Details:
With PwManager you can easily manage your passwords. PwManager saves your passwords blowfish-encrypted in one file, so you have to remember only one master-password instead of all. Instead of the master-password you can use a chipcard, so you don't have to remember a password to access the list. PwManager has a KWallet emulation layer, available on systems with KDE-3.2.
Homepage: [http://passwordmanager.sourceforge.net/](http://passwordmanager.sourceforge.net/)
Size:
344.9 KiB

Does this mean that there is no version for Jaunty? Is there a way to access my ".pwm" file with any other password Manager?

I've tried looking for help in these forums, and on the Web with Google, but I'm not getting anywhere.

Does anyone have any ideas? I would really appreciate any help.

---

### Post by Zorael on 2009-05-13
Well, it's certainly there; [http://packages.ubuntu.com/jaunty/kde-pwmanager](http://packages.ubuntu.com/jaunty/kde-pwmanager). Try to install it via a terminal.
```
$ sudo aptitude install kde-pwmanager
```

---

### Post by Billy Pilgrim on 2009-05-13
> **Zorael said:**
> Well, it's certainly there; [http://packages.ubuntu.com/jaunty/kde-pwmanager](http://packages.ubuntu.com/jaunty/kde-pwmanager). Try to install it via a terminal.
```
$ sudo aptitude install kde-pwmanager
```


God Bless you, Zorael.  It was missing from the upgrade, because I looked for it.  It works now.  **_Many thanks!_**

-Billy Pilgrim

---

