---
title: "KDE Theme"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-02-08
Hello!

I've tried to install a new login screen theme in Kubuntu and failed.

1.) I tried "Get new themes" in System Settings > Login Screen. I'm able to browse through the themes, they download & install, but even after a reboot they don't show up under "Themes" - there is still only the "Ethais" theme.

2.) I tried downloading the tar.gz file directly from kde-look.org and installing it via "Install new theme". Whether I choose the tar.gz file or (after unpacking it) any file from the archive, I get a "Not a valid KDE theme" error message.

3.) I tried that on three different computers, all running Kubuntu 10.10 (one with Plasma Netbook), but it doesn't work on any of them.

Any ideas? Maybe I just misinterpret the meaning of "Themes" and "Get new themes" or something.

Thank you very much,

Blutkoete

---

### Post by cascade9 on 2011-02-08
You cant change the login screen as a user, you have to be root. 

Alt + F2 (brings up 'krunner') 

kdesu systemsettings

Advanced-> Login Manager-> Theme-> 'install new theme' or 'get new theme'.

---

### Post by Blutkoete on 2011-02-08
Thank you for your suggestion, but that didn't help.

I did what you said and it shows the same behaviour: I called krunner, kdesued myself into ksettings, went to the Themes tab, opened "Get new theme", installed the theme I wanted - it's now marked as installed but it doesn't show up in the Themes tab.

---

### Post by herophuong on 2011-09-19
If you have solved the problem or anyone knows the workaround, plz post it here because I also have the same prob.

---

