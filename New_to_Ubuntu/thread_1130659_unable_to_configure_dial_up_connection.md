---
title: "unable to configure dial up connection"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by bobin on 2009-04-20
Obviously I am sitting on a windows OS right now as I cannot connect to net  on ubuntu(hence cannot get any update). 
issues- Can't find networking in administration.Only network tools is there which is of no use.
Tried using sudo pppconfig and added myself to dip group but now the terminal is not reacting to the pon command.
PS :i am a newbie

---

### Post by sonu 1807 on 2009-04-20
Can you elaborate... how exactly you configured it.....what port address you gave for your modem....in my case pon worked when i rebooted

---

### Post by bobin on 2009-04-20
I didn't have to give any port adress . It detected the port on its own.

---

### Post by bobin on 2009-04-20
@sonu 
what happened when you gave pon.
And why is network tools present in place of networking?

---

### Post by sonu 1807 on 2009-04-20
one more thing you can pon as a root. When you enter pon xxx and get no error message that means you are connected although the network manager applet may still show no network. after reboot you dont have to  become root to pon.. you can also install gnome pppon

---

### Post by sonu 1807 on 2009-04-20
generally ttyUSB0 is the correct one  

sonu@sonu-laptop:~$ pon BSNL
sonu@sonu-laptop:~$ 

this is what i get....it means i am connected

---

### Post by Vunutus on 2009-04-20
You need to get the program "gnome-ppp". It's been a while since I had dialup but I remember gnome-ppp making my life much simpler. It makes dialup under Linux work as easily as it does in Windows. 

Obviously if you don't have internet you can't fire up the package manager, but I'm sure there's some way to find the package somewhere else and transfer it from Windows.

---

