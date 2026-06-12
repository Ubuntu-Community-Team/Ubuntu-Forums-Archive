---
title: "dual boot problems"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by michaelalmond on 2010-08-25
Hi,

I hope I'm in the right forum. I'm definitely a newbie to Linux and Ubuntu.

I have bought a new computer with two hard disc drives so that I can run Ubuntu studio and Windows 7 on the same machine. I have installed Ubuntu Studio v. 9.04 but I can no longer access Windows 7 and Ubuntu studio is being very temperamental when it boots. It often freezes on the Ubuntu studio screen.

If anybody can help I would be so grateful.

---

### Post by dtoronto on 2010-08-25
to help you get your windows 7 to load you may want to open a command line and:
```
sudo update-grub
```

you should have a selection of options to boot to the next time you boot your computer assuming Grub picked up your other HDD and windows install

---

### Post by Verbeck on 2010-08-25
maybe the startupmanager package could help.
sudo apt-get install startupmanager
After installation it is in the system>administration menu

---

