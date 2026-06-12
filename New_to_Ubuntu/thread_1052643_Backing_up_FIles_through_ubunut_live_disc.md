---
title: "Backing up FIles through ubunut live disc"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-27
i need to back up files on my broken ubuntu system,,im using the ubunut live disc,,how can i do that? also some files wont open because of a user restriciont. how can i clear it?

---

### Post by Izek on 2009-01-28
if you're having trouble moving the files, in terminal...
```
sudo nautilus
```
make sure you copy and paste or something in the SAME INSTANCE. Otherwise you have to run two sudo nautilus instances from two terminals.

if you want to change permissions, what do you prefer? GUI or terminal?

---

### Post by itsvan on 2009-01-28
i use the terminal better

---

### Post by rraj.be on 2009-01-28
Its better to use 

```
sudo nautilus
```
Its really heavy and much powerfull . . .

---

### Post by itsvan on 2009-01-28
HI im on ubuntu live disc,,and i need to back up files from a broken ubunut system,,but i dont know how to burn them on to a disc or get the user right to move my files..please help!!!!!!!!!!!!!

---

### Post by itsvan on 2009-01-28
HI im on ubuntu live disc,,and i need to back up files from a severely damaged ubuntu system,,but i dont know how to burn them on to a disc or get the user right to move my files..please help!!!!!!!!!!!!! i must save these important files

---

### Post by brsmits on 2009-01-28
You have a flash drive or ipod?

---

### Post by itsvan on 2009-01-28
yes i do,,problem is, i cant move some files,well most of them,,because it says its restricted,,waht do i do?

---

### Post by kshtjsnghl on 2009-01-28
hey try checking the permissions of the files that you want to move
it must be read write to move.

---

### Post by itsvan on 2009-01-28
i cant,,it says im not the owner i cant change the permision..i need to overrule it or something

---

### Post by phrostbyte on 2009-01-28
Go superuser with sudo, sudo can override any permissions.

You can do this easily by hitting ALT-F2 and typing "gksu nautilus" in the window that appears.

---

### Post by itsvan on 2009-01-28
for some reason is still not letting me!!

---

### Post by kshtjsnghl on 2009-01-28
You should prefix the chmod command with sudo to change the permissions of the file of which you are not owner. The password is the same as your user password.
edit ; oh that has already been suggested.

---

### Post by Rocket2DMn on 2009-01-28
Threads merged.

---

### Post by presence1960 on 2009-01-28
This has worked for me in the past when i had similar issues for a few files : open terminal and cd to directory containing files.  My user name is raz and the group is raz. so I did this > sudo chown raz:raz filename. I don't know how many files you need to change permission on, if it is a lot I am sure someone can show you a better way.

---

