---
title: "networking ubuntu and powerbook?"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Digitallysick on 2007-03-24
My powerbook can see that ubuntu is on the network, when i click on it (on my mac) it will ask for host, username and password

usually its 

MSHOME
Adam
xxxxxxxxxx


i assume the name and pass its looking for is my ubuntu login and pass, and then it will say "network not found"

On the ubuntu side, when i try to connect the powerbook, it shows it in networking, when i click powerbook, it doesnt show anything.

---

### Post by souki on 2007-03-25
let's say your ubuntu machine is called "ubuntu", then, can you ping it in a terminal from os x ?
```
ping ubuntu
```if you cannot ping it, then, you have a dns configuration problem on your lan
but you should be able to connect from the finder's menu "Goto > Connect to server"
and then use "smb://xxx.xxx.xxx.xxx/"

---

