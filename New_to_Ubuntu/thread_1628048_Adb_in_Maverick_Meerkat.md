---
title: "Adb in Maverick Meerkat"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by blancoisgod on 2010-11-22
Does anyone have it working? If so I need your help.

---

### Post by cariboo on 2010-11-22
What's adb? We need more info.

---

### Post by WienerWuerstel on 2010-11-22
Do you mean [that]("http://developer.android.com/guide/developing/tools/adb.html")?

---

### Post by blancoisgod on 2010-11-22
yes.

---

### Post by blancoisgod on 2010-11-22
Alright, I have the android sdk extracted to my home folder, i edited my .bashrc file, and still nothing..

---

### Post by igotsanevo4g on 2010-11-22
Easy, i have mine on my desktop, so i enter

cd ~/Desktop/AndroidSDK/tools

and youre in.

Im a small time ROM dev, so if you got any other snags all help ya.

---

### Post by blancoisgod on 2010-11-23
hey thanks man!
It worked. I found out what i was doing wrong though;always make sure you run everything as sudo.

so when you have everything extracted, and you have changed the directory(I.E cd ~/Desktop/AndroidSDK/tools)in terminal, type in sudo ./adb kill-server then type sudo ./adb start-server and youre done.

I found that before every adb command, i must use ./

---

