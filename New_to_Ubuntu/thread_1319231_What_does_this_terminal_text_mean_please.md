---
title: "What does this terminal text mean please?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-08
henry@DELL-laptop:~$ apt-get install frozen-bubble
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

(I was trying to install Frozen-Bubble)

Should I be worried about this code?

Thanks

---

### Post by bacardiandwatermelon on 2009-11-08
It means you need administrator to install it.. To do this use the switch user command... i.e.
sudo apt-get install frozen-bubble

---

### Post by MelDJ on 2009-11-08
you are installing without being root.
type sudo before apt-get

---

### Post by Hetepeperfan on 2009-11-08
You should precede your command with 'sudo'. When using apt-get you need the permissions of the super user to install them.

If you run it like sudo apt-get install frozenbubble then you will be prompted for the password of the superuser and then you can install the game. Don't know wheter i spelled frozenbubble corectly.

best hetepeperfan.

apt-get a good way to install new software you can also find the game in synaptic 

System > administration > synaptic

Try to search for frozen bubble there and then you can install it in a GUI way

---

### Post by listerdl on 2009-11-08
Thanks! I guess you learn something new everyday...so that is what SUDO meant! Thanks!!

---

### Post by Paqman on 2009-11-08
> **listerdl said:**
> so that is what SUDO meant! Thanks!!

sudo = **S**uper **U**ser **DO**

---

