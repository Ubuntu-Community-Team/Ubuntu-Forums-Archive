---
title: "Cant get new webcam to work"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by jinba.ittai on 2011-02-20
10.10 64-bit

Just got a new Ihome 5mp webcam. Ive tried the system>admin>additional drivers and got nothing.


Ive also tried the software center but i keep getting an error saying something about installing untrusted files.

HALP!

---

### Post by no2498 on 2011-02-21
look in applications, sound and video for the program cheese webcam booth
if its not install open a terminal type 
sudo apt-get install cheese click enter
password you dont see anything as you type click enter
try the cam in cheese first

---

### Post by seawolf167 on 2011-02-21
Most new[er] webcams don't need additional drivers to work in Ubuntu, the simplest way to check if it is working and recognized or not is to do what no2498 said and use the program Cheese to test it

```
sudo apt-get install cheese
```

You can also find it by searching the software center (Applications -> Software Center).

Once installed, run Applications -> Sound & Video -> Cheese

---

### Post by gordintoronto on 2011-02-21
See issue 44 of Full Circle Magazine, the Q&A column.

---

