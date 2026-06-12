---
title: "installing .mp3 codec"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by toddlerubu on 2009-05-30
hi guys

i need your support for installing the .mp3 codec, i dont have a regular connection and iam surfing internet fron cafe. i want to install it manually so kindly help me to install it.

---

### Post by juancarlospaco on 2009-05-30
Open **Synaptics**.

Search for " **ubuntu-restricted-extras** "

**Mark for Install**

Go to **File--->Generate download package script**

Save it like *"Mydebs.txt"*, go to internet cafe and **download all links in this TXT**

**install the .debs** *(sudo dpkg -i *.deb)* in the offline machine and play MP3

---

### Post by pastalavista on 2009-05-30
Since you have to go to the cafe to download the script that juancarlo showed you how to make anyway, you could just open a terminal and type ```
sudo apt-get install ubuntu-restricted-extras
```But if you have several things to install, do it his way to make the most of your time. Just mark them all in Synaptic and save the script before you go online.

---

### Post by juancarlospaco on 2009-05-30
If internet cafe have Windows based PC you can use **GNU Wget for windows** a stand-alone .exe

and rename Mydebs.txt to Mydebs.bat and double click it and its kinda automatic now.

---

### Post by toddlerubu on 2009-05-30
thanks guys. i done it........... iam on ma way   to the freedom

---

