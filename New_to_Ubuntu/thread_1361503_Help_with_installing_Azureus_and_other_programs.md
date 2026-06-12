---
title: "Help with installing Azureus and other programs"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by tidus21 on 2009-12-22
Well i am new to Ubuntu and have not quite gotten the hang of all the terminal usage. Basically I am trying to instal Azureus a bit torrent program and the VLC media player to watch the videos. however when i put this command in which I am told is the correct one I get an error

glen@glen-laptop:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azureus
glen@glen-laptop:~$ 

If anyone could help and tell me what I am doing wrong, it will very much be appreciated.

---

### Post by sikander3786 on 2009-12-22
try

sudo apt-get update

sudo apt-get install vuze

---

### Post by talsemgeest on 2009-12-22
> **tidus21 said:**
> Well i am new to Ubuntu and have not quite gotten the hang of all the terminal usage. Basically I am trying to instal Azureus a bit torrent program and the VLC media player to watch the videos. however when i put this command in which I am told is the correct one I get an error

glen@glen-laptop:~$ sudo apt-get install azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package azureus
glen@glen-laptop:~$ 

If anyone could help and tell me what I am doing wrong, it will very much be appreciated.
To find the name of an app that you can install with ```
sudo apt-get install
``` you can search in synaptic. The name in synaptic is the same as with apt-get.

---

### Post by Devlin67 on 2009-12-22
Take a look here [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
This should answer your question and more

---

### Post by tidus21 on 2009-12-22
> **sikander3786 said:**
> try

sudo apt-get update

sudo apt-get install vuze

Thank you that really worked, I appreciate the help.

---

