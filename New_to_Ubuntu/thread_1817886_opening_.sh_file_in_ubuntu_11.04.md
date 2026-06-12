---
title: "opening .sh file in ubuntu 11.04"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by user_linux on 2011-08-03
I'm trying to open a file named dell.sh. It's on my desktop. How can i open it?
PS: Just to clarify again, it's a printer driver file, so I'm trying to run it to set up my printer I think.

---

### Post by fdrake on 2011-08-03
> **user_linux said:**
> I'm trying to open a file named dell.sh. It's on my desktop. How can i open it?

make sure that you trast this file and it's source

```
chmod +x ~/Desktop/dell.sh
cd Desktop
./dell.sh
```


edit: ops I thoungt you meant how to run a sh.......  :P

```
gedit ~/Desktop/dell.sh
```

---

### Post by Furball588 on 2011-08-03
> **user_linux said:**
> How can i open it?

Any text editor would work.  

I use gedit, but I'm sure other people have their favorites too...

---

### Post by 3rdalbum on 2011-08-03
Open it, or run it?

---

### Post by Furball588 on 2011-08-03
> **fdrake said:**
> edit: ops I thoungt you meant how to run a sh.......  :P

```
gedit ~/Desktop/dell.sh
```

I'm reminded of this...[http://www.guzer.com/pictures/findx.php](http://www.guzer.com/pictures/findx.php) :P

---

### Post by fdrake on 2011-08-03
> I'm reminded of this...[http://www.guzer.com/pictures/findx.php](http://www.guzer.com/pictures/findx.php) 

[IMG]http://www.guzer.com/pictures/findx.jpg[/IMG]

LOL

---

### Post by user_linux on 2011-08-04
v

---

### Post by user_linux on 2011-08-04
Ok, if I have to open from root ie by sudo command, what do I do?
> **fdrake said:**
> make sure that you trast this file and it's source

```
chmod +x ~/Desktop/dell.sh
cd Desktop
./dell.sh
```
edit: ops I thoungt you meant how to run a sh.......  :P

```
gedit ~/Desktop/dell.sh
```

---

### Post by Enigmapond on 2011-08-04
> **fdrake said:**
> [img]http://www.guzer.com/pictures/findx.jpg[/img]

lol

lol

---

### Post by jtarin on 2011-08-04
In a terminal run the commands as outlined

```
chmod +x ~/Desktop/dell.sh
```
```
cd Desktop
```
```
sudo ./dell.sh
```
It will ask for password....type your password and hit the "enter" key.

---

### Post by computerandu on 2011-08-05
> **fdrake said:**
> [IMG]http://www.guzer.com/pictures/findx.jpg[/IMG]



I liked this pic....lol

---

