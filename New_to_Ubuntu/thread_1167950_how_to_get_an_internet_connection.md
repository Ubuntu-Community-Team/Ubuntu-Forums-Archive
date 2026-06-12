---
title: "how to get an internet connection"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by unnisheva on 2009-05-23
hey guys ..............i am new to kubuntu....................and i was wondering how i wud be able to connect to the internet................i have a broadband connection.................thanx for the help in advance.

---

### Post by LikwidSteel on 2009-05-23
> **unnisheva said:**
> hey guys ..............i am new to kubuntu....................and i was wondering how i wud be able to connect to the internet................i have a broadband connection.................thanx for the help in advance.
I'm new with Linux and such, but I know for Windows that it would most probably be that you need the drivers for your mobo. Or if you don't have an integrated network card, the drivers for your network card. It may be hard to find Linux drivers though. Good luck. =]

---

### Post by cerealtx on 2009-05-23
> **unnisheva said:**
> hey guys ..............i am new to kubuntu....................and i was wondering how i wud be able to connect to the internet................i have a broadband connection.................thanx for the help in advance.

its kinda impossible to help you, because we know nothing except that u wanna get on the internet, are u trying wireless? wired? do u see a network when u run kwifimanager?
posting the output of ```
lspci
``` might help us help you after you tell us what type of connection ur trying to make

---

### Post by orky7 on 2009-05-23
if u have a wired broadband connection then i think u should go with "sudo ppoeconf" and if it shows ur connection that will be eth0 or something like.....and then just follow the instruction and after that when it's all over u can start the connection with "sudo pon dsl-provider" and end the connection with "sudo poff dsl-provider" use "ifconfig" for status good luck....if u have a wireless connection i don't know but i think u can use the above instruction.

---

