---
title: "Problem installing wine"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by lolzomgz on 2011-06-24
As i understand it these are the steps taken to install wine:

Go to Software sources> Thrid party software> Add
Then enter [I]ppa:ubuntu-wine/ppa then click "Add source" the problem is that the "Add source" button is greyed out, any help? 
[/I]

---

### Post by Neoncamouflage on 2011-06-24
All I had to do was go to the terminal and type in:
```
sudo apt-get install wine
```

---

### Post by lolzomgz on 2011-06-24
> **Neoncamouflage said:**
> All I had to do was go to the terminal and type in:
```
sudo apt-get install wine
```
  
Terminal? (Sorry im very new to this. >.> )

---

### Post by Neoncamouflage on 2011-06-24
The terminal is the command line for Ubuntu. It's where you give commands directly to the system. You want to install wine, so you type:

```
sudo apt-get install wine
```

sudo - Runs as root user, meaning it can add to, remove, and change things in your hard drive

apt-get - Tells it that you want to access the software repositories, a massive collection of useful things for Ubuntu

install - Tells it you want to install a package

wine - What you want to install

You can find the terminal under Applications > Accessories > Terminal

---

### Post by lolzomgz on 2011-06-24
Thanks for the help :D

---

### Post by Neoncamouflage on 2011-06-24
Anytime man, happy it worked for you.

---

