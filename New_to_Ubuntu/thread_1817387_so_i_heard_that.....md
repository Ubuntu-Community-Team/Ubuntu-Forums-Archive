---
title: "so i heard that...."
date: 2011-08-03
forum: New to Ubuntu
---

### Post by ufo2222 on 2011-08-03
linux is multi user right so what does that mean? does it mean that you can use multiple accounts but they cant all be logged in at the same time? or does it mean that you can have 2 accounts and they are logged in at the same time? or something else? thank you for your help in advance

---

### Post by aeiah on 2011-08-03
you can have many accounts logged in at the same time. this is possible on several versions of windows too, of course, but linux and unix is generally referred to as multi-user because this has always been the case, whereas with windows it was kinda added on.

---

### Post by ufo2222 on 2011-08-03
> **aeiah said:**
> you can have many accounts logged in at the same time. this is possible on several versions of windows too, of course, but linux and unix is generally referred to as multi-user because this has always been the case, whereas with windows it was kinda added on.
how would i be able to use this feature? and thanks for explaining it.

---

### Post by nothingspecial on 2011-08-03
If you are using the latest ubuntu, you add a user by clicking the on/off button (top right), then select system settings > users and groups.

When you want to switch users you click the on/off button and select a user from the list......

.....if that's what you mean.

---

### Post by cipherboy_loc on 2011-08-03
From the terminal is a well known one, but you can also have a SSH server running and if bobjoe wants to access LibreOffice + his documents on that computer while you use it (physically), he could tunnel it over SSH. 


Cipherboy

---

### Post by ufo2222 on 2011-08-03
> **cipherboy_loc said:**
> From the terminal is a well known one, but you can also have a SSH server running and if bobjoe wants to access LibreOffice + his documents on that computer while you use it (physically), he could tunnel it over SSH. 


Cipherboy
What is an shh server? and how would i create one?

---

### Post by nothingspecial on 2011-08-03
You need 2 computers.

On one

```
sudo apt-get install openssh-server
```

on the other

```
ssh user@ipadress
```

Where user is the username on the other computer and ip adress is the ip adress of the other computer.

---

### Post by ufo2222 on 2011-08-03
thank you for your help and would i be able to use [terminals]("http://terminals.codeplex.com/") on a windows computer to connect to my server?

---

### Post by skatinjj on 2011-08-03
You could ssh into your linux box from Windows, but to forward the X apps, you would need I believe CYGWIN.

---

