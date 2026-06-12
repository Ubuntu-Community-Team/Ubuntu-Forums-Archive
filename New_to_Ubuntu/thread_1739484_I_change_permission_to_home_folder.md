---
title: "I change permission to home folder?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by rom3lol on 2011-04-26
Well I was messing around and ran this command

```
sudo chown 777 ~/
```And now I get this when I try to open my home folder

> Nautilus could not create the following required folders: /home/usename/Desktop, /home/username/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.I checked the permission and says this 
```
ls -l home
``````
drwxr-xr-x  4 root root 4096 2011-02-11 13:08 Desktop
drwx------ 89  777 rom3 4096 2011-04-25 21:57 rom3
drwxr-xr-x  2 1001 1001 4096 2011-02-10 14:23 test
```

How do I return it to normal ?

---

### Post by jtarin on 2011-04-26
You changed owner.....[Read this for enlightenment]("http://shebangme.blogspot.com/2009/11/chmod-and-chown-777.html").....and quit messing around. :)

---

### Post by crispy_420 on 2011-04-26
So to fix chown back to your user name. So if you can get back a command line replace 777 with your username.

---

### Post by Miljet on 2011-04-26
Your problem started when you used sudo in your home directory. That changes ownership of files to root when they should belong to you.

And you complicated it by using chown (change owner) with 777 which is a parameter for chmod.

The only two files that Nautilus is complaining about is Desktop and .nautilus, so if you change ownership of those two files back to yourself, Nautilus should run.

```
sudo chown username username ~/Desktop
sudo chown  username username ~/.nautilus
```

Then you can look at changing the ownership of other files in your home directory.

---

### Post by rom3lol on 2011-04-26
> **jtarin said:**
> You changed owner.....[Read this for enlightenment]("http://shebangme.blogspot.com/2009/11/chmod-and-chown-777.html").....and quit messing around. :)

Lol Thanks for the link. Messing around teaches you important lessons, such as "their is no such thing as chown 777" lol

---

### Post by rom3lol on 2011-04-26
> **crispy_420 said:**
> So to fix chown back to your user name. So if you can get back a command line replace 777 with your username.

Thank you I fixed it.
```
chown 700 home
``````
chown rom3 rom3
```:popcorn:

Thanks for the reply Miljet I have solve the problem. I didn't think about just changing permission for the files you mentioned thank you guys.

---

