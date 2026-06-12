---
title: "I have really broken my linux."
date: 2009-02-12
forum: New to Ubuntu
---

### Post by navic101 on 2009-02-12
I have hardy installed for some time on my other system and tonight i decided to install virtualbox. After installing it and getting a error messge about not having the correct permissions etc and reading some of the furums. i Uninstalled it.

This has now left my system to boot with no wireless network detectable, no sound and a hideous resolution which i can't alter. The drivers for much of this seem to have been uninstalled along with vbox.

Can you please help?

---

### Post by Tek-E on 2009-02-12
Have you tried to re-install the missing drivers?

---

### Post by mc4100 on 2009-02-12
Provided you have wired Internet access, the following will reinstall any packages which may have been removed:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by navic101 on 2009-02-12
Thanks for the input guys.. However i theo nly way i can get my sound and my internet back is if i esc. on boot up and then choose 8.0.4.1 kernel 2.6.24-23 generic from the list which is about 3 or 4 down then i boot with sound and inertnet again. Graphics are still awful and the Nvidia display is disabled on the hardware settings.

As soon as i reboot i'm back to the case before with no sound,internet or proper display..

as suggestions?

---

### Post by cariboo on 2009-02-12
You may have to reinstall the last kernel, not knowing what the last kernel you are running is , you would probably be best off using synaptic to search for it , mark it fro reinstallation. Just type linux-image in the search box, and pick from there.

Jim

---

