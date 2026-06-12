---
title: "help moving file"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by rodneymullen on 2010-01-16
Hi

i'm trying to install java runtime and the site instructions want me to put the file in /usr/java/ so i made the folder but i'm having trouble moving the file into that folder. Whatever i do i can't seem to get the permission to move it. Could someone help me out and give me the command line? The file name is jre-6u17-linux-i586.bin and the folder is /usr/java.

thank you

---

### Post by Miljet on 2010-01-16
In answer to your question, you have to put sudo in front of the command to move or alter any files owned by root.
```
sudo mv /path/to/jre-6u17-linux-i586.bin /usr/java/jre-6u17-linux-i586.bin
```

General observation: there is a much easier way to install Sun java. You can install it from the Synaptic Package Manager by just selecting the packages and clicking on install. Or from the terminal do this. 
```
sudo apt-get update
```
It will ask for your password. Enter that and wait for the prompt. Then
```
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
```

---

