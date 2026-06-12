---
title: "Is there a way to replace Nautilus Elementary with the regular Nautilus?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-05
I installed Nautilus Elementary file manager, but I want the original Nautilus file manager back.

I've looked for a way to do it, and I even tried (what I thought was) uninstalling and then reinstalling it, but that didn't work.  Although maybe I didn't do it right.

---

### Post by jtarin on 2011-04-05
Edited for clarification:
Uninstall instructions

"ppa:am-monkeyd/nautilus-elementary-ppa"
Remove the above PPA from your sources list (System > Admin > Software Sources > Other Software): -
Then run the following commands: -
sudo apt-get update
sudo aptitude install nautilus

---

### Post by vanadium on 2011-04-05
If that does not work, a "harder" way to reset things is to boot to a recovery root prompt with networking, and remove, then reinstall nautilus (you need to have removed the elementary ppa first as indicated in the previous post).

```

apt-get purge nautilus*
apt-get install ubuntu-desktop

```

---

### Post by Learning Linux 2011 on 2011-04-06
> **vanadium said:**
> If that does not work, a "harder" way to reset things is to boot to a recovery root prompt with networking, and remove, then reinstall nautilus (you need to have removed the elementary ppa first as indicated in the previous post).

```

apt-get purge nautilus*
apt-get install ubuntu-desktop

```

Hi, 

How do you get a recovery prompt in Ubuntu Linux?

---

### Post by Learning Linux 2011 on 2011-04-06
Do you know if there is a way to remove the PPA without going into GNOME?

Part of my problem is that I royally screwed up my system and it won't boot into GNOME anymore.  It gives me a graphical login, as if it is ready to login to GNOME, but then won't actually log in.

I was trying to install that new "Elementary" theme and I didn't really understand that Elementary Nautilus was part of it, and when I tried to get rid of it, my system got totally hosed.

I think that ubuntu-desktop might have gotten removed too, that sounds familiar.

---

### Post by beew on 2011-04-06
Ubuntu-desktop is just a meta-package, it could be removed with no issue. I have done it many times. Something else was removed. 

Also I think you have already removed the ppa if you have struck it from sources.list.d so no point in doing it again.

I don't know how to restore your graphic interface, but if you run into a similar situation next time you should use ppa-purge install of 'sudo apt-get purge package" because ppa-purge safely downgrades your packages instead of removing crucial packages and leaves you with no fall back in the meantime (with non system software it doesn't matter, but anything system related, you don't want to be dangled in mid air after one version is removed but before the other is installed!)

You should have run in the terminal

```
sudp apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```Sorry I can't be more helpful in getting you the desktop back.

---

### Post by Learning Linux 2011 on 2011-04-06
> **beew said:**
> Ubuntu-desktop is just a meta-package, it could be removed with no issue. I have done it many times. Something else was removed. 

Also I think you have already removed the ppa if you have struck it from sources.list.d so no point in doing it again.

I don't know how to restore your graphic interface, but if you run into a similar situation next time you should use ppa-purge install of 'sudo apt-get purge package" because ppa-purge safely downgrades your packages instead of removing crucial packages and leaves you with no fall back in the meantime (with non system software it doesn't matter, but anything system related, you don't want to be dangled in mid air after one version is removed but before the other is installed!)

You should have run in the terminal

```
sudp apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```Sorry I can't be more helpful in getting you the desktop back.


Ahh, ok, that sounds like some information I was looking for and should have done.  
I think I started running into problems when I tried to just remove the PPA.

I think I did try to purge nautilus-elementary by itself, maybe that is what did it.

---

### Post by vanadium on 2011-04-06
In order to be able to log back in into your system, you probably will need the recovery prompt now.

Boot your computer, and while it starts, hold the shift key pressed. This will display the grub boot menu. Select a line with "Recovery". At some point, you will see a few options. Choose "root prompt with networking".

* to check whether your elementary PPA is removed, you can open the config file /etc/apt/sources.list. This is where the PPA's are activated.
```

nano /etc/apt/sources.list

```
If you still see the PPA of elementary, place comment signs, #, before the lines. Then save the file.

* Then purge nautilus
```

apt-get purge nautilus*

```

* and reinstall the default ubuntu desktop.

```

apt-get install ubuntu-desktop

```

after which you should be able to login into your system. If still you do not have the default nautilus, then you will need to check whether you did all things right, and if you did, you will need to remove and reinstall some more of the desktop (I have been though this myself ...)

---

