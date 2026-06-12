---
title: "Re-run upgrade"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by lsaplai on 2010-05-25
Hello all

During a recent upgrade from 9.10 to 10.04, my laptop suddenly lost power and the process was interrupted. I was able to reboot into a recovery mode and finish enough of the upgrade process to get a working environment but some functionalities are missing: for instance, there is no sound applet (but sound is working though), no Gwibber and no MeButton. There are probably other things missing too.

Is there anyway I can "re-run" the installation so that I complete the upgrade in full without having to reinstall my whole system?

Thanks in advance for your insight.

Cheers!

---

### Post by bodhi.zazen on 2010-05-25
Possibly - sometimes such a system is unusable.

Try```
apt-get install -f
apt-get install --reinstall ubuntu-desktop
```

---

### Post by lsaplai on 2010-05-26
Tank you for the suggestion Bodhi. I ran these commands and  they executed alright. My system is still usable, which is good news but it doesn't seem to have changed anything to the installation.

Would you happen to have another suggestion?

TIA

---

### Post by bodhi.zazen on 2010-05-26
Your configuration files may be corrupt.

You can test this by creating a new user and logging in as the new user. If things seem to be working with a new user, back up any data you wish to keep in your home directory, boot to recovery mode and remove all the files in $HOME.

Then reboot and the config files should be recreated. Log in and restore your data.

The only hitch would be if you use an encrypted home, that may be more complex.

---

