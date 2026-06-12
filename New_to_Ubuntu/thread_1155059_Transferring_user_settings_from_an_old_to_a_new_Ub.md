---
title: "Transferring user settings from an old to a new Ubuntu"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Alexandre76 on 2009-05-10
:confused:

Hello Everyone!

Somebody gave me an Ubuntu computer which they tried to upgrade from 8.10 to 9.04 when they got the notification, but the upgrade process failed and they were unable to logon after the upgrade.

In an attempt to try to help them, I did the following: 
 - I booted on the computer with a live CD 
 - Went into the folder /home/rubens/, pressed CRTL H to show the hidden  files/folders, 
- Selected them all and copied to an external hard disk
- Installed a fresh Ubuntu 9.04 by completely erasing the existing failed upgrade.
- Created the same username and after the install was complete I copied from the external hard disk the users files&folders

At first boot, I get the following warning : ```
Your home directory is listed as '/home/rubens' but it does not appear to exist. Do you want to login with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session
```

If I press yes, I get the following screen: ```
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users
```

I press OK on this message and it remains on a blank screen, then nothing happens.

WOuld anyone be able to help me solve this problem? The user is bugging me to get his computer back...

Many thanks in advance for your time.

---

### Post by Pjotrovitz on 2009-05-10
You can try this command:

sudo chown rubens:rubens /home/rubens

This sets rubens as the owner of the folder.

---

### Post by spiderbatdad on 2009-05-10
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

