---
title: "Ubuntu freezes on boot."
date: 2010-08-01
forum: New to Ubuntu
---

### Post by Sorvahr on 2010-08-01
I installed the latest ATI GPU drivers, and apparently something went wrong.
When I restart my computer, it freezes on a purple screen after the "Ubuntu" splash screen. The keyboard is responsive (I can activate and deactivate caps lock), but I can't do anything.
I tried running in recovery mode and fixing broken packages, but it didn't help.
Also, I waited for 30 minutes on the purple screen to see if Ubuntu was booting very slowly for some reason, but nothing changed :/

Ubuntu version is 10.04 x64.

Any way to solve this without needing to format/reinstall?

Thanks in advance!

---

### Post by cariboo on 2010-08-01
I would suggest you try starting in recovery mode, and once at the menu select resume, once at the prompt login with your user name and password. Next at the prompt type:

```
sudo service gdm start
```

the above command will start X and take you to the login screen. You should then be able to login to your desktop.

Once you have done the above, you should be able to log in normally on the next reboot.

---

### Post by Sorvahr on 2010-08-01
I tried doing that and I got stuck at a black screen.
This would mean X is not staring correctly for some reason, right?
Should I reinstall it running ```
sudo apt-get install --reinstall xserver-xorg
```?

---

### Post by Sorvahr on 2010-08-02
Fixed this issue by uninstalling the ATI drivers, and reinstalling using a super user.

---

