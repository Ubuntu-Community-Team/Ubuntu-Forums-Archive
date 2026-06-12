---
title: "How do I install Krepton?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by mikethebike on 2009-09-26
Please help, I'm trying to install Krepton 4.1 on Ubuntu 9.04. Can anyone help me please.

---

### Post by pedro3005 on 2009-09-26
That is a KDE app. If you use Ubuntu, you probably have GNOME. But don't panic, you can still run it. You will need some KDE stuff though, I'm not sure what. But you can download Krepton here: [http://www.keelhaul.me.uk/krepton/downloads/krepton-4.1.tar.gz](http://www.keelhaul.me.uk/krepton/downloads/krepton-4.1.tar.gz)
Then there is probably a readme inside that with instructions. If you want you can also just get KDE by running ```
sudo apt-get install kubuntu-desktop
```, logging out and choosing KDE as a session.
EDIT: Just checked, the instructions are named INSTALL.

---

### Post by mikethebike on 2009-09-26
Thank you very much, thats got me a bit closer. Now its telling me:-

checking how to run the C++ preprocessor... /lib/cpp
configure: error: in `/home/mike/krepton':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

Any ideas please?

---

### Post by pedro3005 on 2009-09-26
Try installing build essentials with:
```
sudo apt-get install build-essential
```
Then try again.

---

### Post by mikethebike on 2009-09-26
Thanks for your patients but i'm now getting :-

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by pedro3005 on 2009-09-26
Just to check, are you running KDE or GNOME?

---

### Post by mikethebike on 2009-09-26
I'm running Gnome as far as I know.

---

### Post by steveneddy on 2009-09-26
> **mikethebike said:**
> Thanks for your [COLOR=Red]**patients**[/COLOR] 

[COLOR=Red]**Patients**[/COLOR] are the people a doctor sees during the course of his day.

[COLOR=SeaGreen]**Patience**[/COLOR] is a virtue and the word you meant to put here.

---

### Post by mikethebike on 2009-09-26
Wow help with my spelling too. Cool.

---

### Post by steveneddy on 2009-09-30
> **mikethebike said:**
> Wow[COLOR=Red]**! H**[/COLOR]elp with my spelling, too[COLOR=Red]**?**[/COLOR] Cool[COLOR=Red]**!**[/COLOR]


And grammar.

No charge

:popcorn:

---

