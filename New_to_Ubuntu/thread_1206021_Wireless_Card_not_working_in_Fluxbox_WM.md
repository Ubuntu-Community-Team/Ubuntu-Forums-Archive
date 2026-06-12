---
title: "Wireless Card not working in Fluxbox WM"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by c49 on 2009-07-06
I have a Dell Mini 9 netbook with Ubuntu 8.04, the only difference being that I installed fluxbox via "sudo apt-get install fluxbox" because I am trying to optimize my very limited resources. However when I boot into Ubuntu with fluxbox I cannot access my wifi and there is no graphical way to manage my wifi connection. I am fairly new to Linux so could someone please post a VERY detailed step-by-step instruction to enable wireless connections in fluxbox?

---

### Post by c49 on 2009-07-07
halp ples

---

### Post by kerry_s on 2009-07-07
you just need to add-> **nm-applet &** <-to your ~/.fuxbox/startup file.

open your file manager & press ctrl+h to see those hidden folders/files.
once you open it in your text editor you should see a place where they have samples, put it there.

i can't be detailed i haven't used fluxbox in a while.

---

### Post by Pogeymanz on 2009-07-07
I also haven't used fluxbox is a while, so I wont be any more helpful.

Basically, the graphical tool your looking for is call nm-applet. It's the thing that sits in your system tray and allows you to change your network.

When you log into fluxbox, hit ALT+F2 and type nm-applet in there.

To avoid doing this every time you log in, you need to edit a config file in your home directory. There is a hidden folder called .fluxbox/ and in there is a file called startup. I don't remember what syntax fluxbox uses, but you basically just have to add nm-applet into that file.

---

