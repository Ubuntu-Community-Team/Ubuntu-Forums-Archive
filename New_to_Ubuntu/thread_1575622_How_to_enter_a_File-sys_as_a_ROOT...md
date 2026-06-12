---
title: "How to enter a File-sys as a ROOT..?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-16
[SIZE=2]*I want to access the File-system as a ROOT,how can i do it **CLI**?*
because whenever i want to create a directory or something else,i Cant do that..

therefore, i want to know about the commands which allows the user to have **privileges** that of ROOT.

thankx:p
[/SIZE]

---

### Post by ZootNerper on 2010-09-16
You could:

gksudo nautilus

Then enter your password. This will open the file browser as root. But be very careful as File System is where Linux lives.

I don't know what you want to do, but better to use a separate partition, like /home, for your own directories and files.

-- Zoot

---

### Post by tajiknomi on 2010-09-16
[SIZE=2][I]Actually i just want to copy my Gnome theme to distination usr/share...

therefore i need it...

anyhow,i can use sudo su..
[/I][/SIZE]

---

### Post by tajiknomi on 2010-09-16
[SIZE=2][I]Till now i m hearing about these two Commands that they gives privileges to the** user**....but i don't know about their **Difference**?
 [/I][/SIZE]
[SIZE=2]Is Sudo-su use only in CLI ?[/SIZE]

---

### Post by coffeecat on 2010-09-16
All, and more, is explained: :)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by QLee on 2010-09-16
> **tajiknomi said:**
> [SIZE=2][I]Actually i just want to copy my Gnome theme to distination usr/share...

therefore i need it...

anyhow,i can use sudo su..
[/I][/SIZE]
This will explain that Ubuntu is configured to allow you to do administration tasks with temporary root permissions safely. It is a good idea to understand why Ubuntu uses sudo.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by overdrank on 2010-09-16
Threads merged. :)

---

### Post by mikewhatever on 2010-09-16
Hi tajiknomi, the command you are looking for is **sudo cp /source /destination** , where sudo is the prefix that gives admin privileges.

---

