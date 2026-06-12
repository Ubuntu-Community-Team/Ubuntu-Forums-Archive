---
title: "search file"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by maroofi on 2010-06-22
ok i know this is a silly question.i am realy sorry.
i know how to search file in ubuntu but i wanna use ls command and filters to do that...
assume that i want to find a .flv file so i write this in / directory(root):
```

sudo ls -R | grep .flv

```and this is the result :

```

2NQjtMjhV9Q.flv
a.flv
libgstflv.so
x-flv.xml

```i have 2 flv file : a.flv and 2NQjtMjhV9Q.flv but i just find the names and i dont know where they are.
in windows cmd you can type :
```
dir/b/s *.flv
```and you have the full path and the name of the file/s.
how we can do this with ls command?

---

### Post by tarps87 on 2010-06-22
In theroy yo could use
```
sudo ls -Rl | grep .flv
```
or you could just use
```
sudo find / -name *.flv
```
```
sudo find *locationToSearchIn* -name *.flv
```

---

### Post by maroofi on 2010-06-22
sudo ls -Rl | grep .flv
doesnt work .it just print the filename.
sudo find / -name *.flv     works fine.
but i wanna know is there any way to search a file with it's name using ls command?

---

### Post by tarps87 on 2010-06-23
That make sense, it only lists the files details and you wanted the path oops, you could try using the following in combination with the grep command
```
for i in `ls -1`; do echo $PWD/$i; done
```
Is there any reason you want to use ls instead of find?

---

### Post by Legendary_Bibo on 2010-06-23
try tracker, it's a gui method, but you can make it index all your files for you (took 20 minutes for me), and then you can just click it and find it, and it lists all searches related to it and you can open it up from there. It also shows its file path as well.

---

