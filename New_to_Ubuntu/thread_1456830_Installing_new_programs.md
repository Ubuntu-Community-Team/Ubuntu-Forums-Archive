---
title: "Installing new programs"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by brotherwolf1388 on 2010-04-17
I have been trying to install a program called think or swim and I can download it but I don't know how to actually install it to the computer. Some suggestions?

---

### Post by nmaster on 2010-04-17
> **brotherwolf1388 said:**
> I have been trying to install a program called think or swim and I can download it but I don't know how to actually install it to the computer. Some suggestions?

would you care to give us some more information?  a link to the download would be helpful.

---

### Post by brotherwolf1388 on 2010-04-17
Well how do I download a package and install it?

---

### Post by jaco223 on 2010-04-17
> **brotherwolf1388 said:**
> Well how do I download a package and install it?

Is it a Linux program? or a windows application you're trying to download and install
to Ubuntu?
Normally you could open a terminal window and at the prompt type:

```
sudo apt-get update
sudo apt-get install (name of program/package)
```If it is a windows application you would first need to install "wine"

```
sudo apt-get install wine
```Wine is an emualator that runs windows application.

Hope this helps.

Jaco

---

### Post by cuberts on 2010-04-17
> **brotherwolf1388 said:**
> I have been trying to install a program called think or swim and I can download it but I don't know how to actually install it to the computer. Some suggestions?a little more info...
but is it some thing in the Ubuntu software center? then just find it there and just click the arrow to install.

but wow more info...

---

### Post by nmaster on 2010-04-17
why won't you tell me where you got it?  different packages can be installed in different ways and i need to know what you have in order to help you. 

here is a general overview.  it seems like you are a new to linux... or maybe even computers since you didn't find this through a search engine:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

since this isn't FOSS, you could try calling customer service.

---

### Post by jaco223 on 2010-04-17
> **brotherwolf1388 said:**
> I have been trying to install a program called think or swim and I can download it but I don't know how to actually install it to the computer. Some suggestions?


Try this link and go to the Linux install instructions  for "think or swim"
there is a specific section for installing on Ubuntu.

[https://mediaserver.thinkorswim.com/installer/install.html](https://mediaserver.thinkorswim.com/installer/install.html)

If you downloaded the thinkorswim_installer.sh file, navaigate to the directory where you saved the download
and try to execute the program using the terminal window.
Hope that helps.

Jaco

---

