---
title: "Gnome Power Manager failed to install properly"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by jcox87 on 2010-05-19
Hi.
I installed Ubuntu yesterday, as a complete newcomer to linux.
I was moving some files from windows to ubuntu when the error message that the gnome power manager had failed to install its configuration settings appeared and i could no longer log in.

Does anyone know how this can be fixed? I really don't want to re-install as I'd rather not lose the files I've copied over (my windows os is currently running in safe mode/blue screening, so the files copied were most recent ones not backed up on a disk) and I don't fully understand the fixes for this error that I've come across.

I posted this in the General Help forum, but didn't get any helpful replies.
Please help me!

---

### Post by mikewhatever on 2010-05-19
You can try to login at the console and reinstall just the gnome-power-manager package. At the login screen, press ctrl+alt+f1, login with your username and password, then use the following command:

sudo apt-get install --reinstall gnome-power-manager

---

### Post by jcox87 on 2010-05-19
Hi, Thanks!

I have just tried this.
I did encounter a problem logging in at the console: it keeps telling me my login is correct, even though i type in the exact same username/password as to log in normally.
However, I ran in the recovery mode and managed to reinstall the package, but it didn't work; the error still shows up and doesnt let me log in. - is this because i couldn't/didn't log in at the console?

---

### Post by jcox87 on 2010-05-19
Just to add to this:
I opened it up in recovery mode and attempted to repair broken packages, i notced that it is saying I need 1,000kb or so of space in /var/cache/apt/archives/
I've tried using sudo apt-get clean but nothing is happening.
Also, when I tried re-installing the package, it said I needed 75mb?
I'm so confused :(

---

