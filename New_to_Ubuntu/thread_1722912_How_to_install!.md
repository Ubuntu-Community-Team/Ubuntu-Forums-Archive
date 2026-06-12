---
title: "How to install?!"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by sarafimov21 on 2011-04-06
I installed Ubuntu 11, downloaded ktechlab and extracted it on the desktop. 
Please tell me how to install it now?
Im noob. :KS
Tnx!

---

### Post by arochester on 2011-04-06
Available from Repository. See [http://joysofprogramming.com/install-ktechlab-ubuntu/](http://joysofprogramming.com/install-ktechlab-ubuntu/)

---

### Post by sarafimov21 on 2011-04-06
When i try to install, i get this:
boris@Sarafimov:~$ sudo apt-get install ktechlab
[sudo] password for boris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ktechlab
:confused::confused::confused:

---

### Post by el_koraco on 2011-04-06
try doing sudo apt-get update before you install.

---

### Post by ubudog on 2011-04-06
Or one big command:

```
sudo apt-get update && sudo apt-get install ktechlab
```

---

### Post by sarafimov21 on 2011-04-06
I did everything you told me, and still **NOTHING!** :(

---

### Post by arochester on 2011-04-06
Are you connected to the Internet when you try the command?

---

### Post by sarafimov21 on 2011-04-06
of course! 
I'm not that noob -.-

---

### Post by techunit on 2011-04-06
Why is he using the terminal if he is a noob. He should be using the Ubuntu Software Center. If he was able to download the ktechlab from the internet he is likely connected to the internet.

Is Ktechlab located in Universe or MuliUniverse? If so he probably needs to activate them.
That can be done under the source center in the  Ubuntu Software Center.

---

### Post by Fraoch on 2011-04-06
> **sarafimov21 said:**
> I did everything you told me, and still **NOTHING!** :(

The instructions assume the computer you are installing it to has Internet access.  But if you've added the .deb package to the desktop, just double-click on it.

If all it does is show the contents of the package, right-click on it and select "Open With >" "GDebi Package Installer".

In the future, you don't have to copy packages to your desktop to install them.  Go through the Ubuntu Software Centre.

---

### Post by oldos2er on 2011-04-06
I can't find ktechlab in Natty's repositories, however it's in Maverick's: [http://packages.ubuntu.com/maverick/ktechlab](http://packages.ubuntu.com/maverick/ktechlab)

---

### Post by ubudog on 2011-04-06
Hmm... weird.

---

### Post by oshman on 2011-11-30
-BUMP-

Does anyone know if KTechLab will be added to Oneiric (11.10) repositories?

---

### Post by chronos00 on 2011-12-23
Are there any plans to re-include KTechLab to Ubuntu repositories?

Is KTechLab still an active project?

And most important of all:
**Does anyone know a viable alternative?** At least a proprietary and/or closed source, but that works on Linux / Ubuntu.

Regards

---

