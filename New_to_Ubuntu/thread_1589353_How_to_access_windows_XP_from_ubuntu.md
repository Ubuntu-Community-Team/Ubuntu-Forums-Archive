---
title: "How to access windows XP from ubuntu"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-06
I have read many tutorials but nothing seems to get work..How to access windows from ubuntu...?

---

### Post by Morbius1 on 2010-10-06
Across the network?

Or in a dual boot?

---

### Post by HermanAB on 2010-10-06
Install Virtualbox, make a VM and install Windows XP.

---

### Post by k33bz on 2010-10-06
> **HermanAB said:**
> Install Virtualbox, make a VM and install Windows XP.

I do not think that is what the OP was referring to. And like was posted above, we would need to know how you are trying to access Windows from Ubuntu. Through a network (on a different computer) or is it Dual Boot (on same computer)?

---

### Post by karthick87 on 2010-10-06
Through a network on different computer.

---

### Post by k33bz on 2010-10-06
Have you tried installing VNC Server to both your Linux machine and Windows machine?
Also have you tried ssh to your windows machine?

---

### Post by karthick87 on 2010-10-06
how to ssh to windows machine..?

---

### Post by nikefalcon on 2010-10-06
[QUOTE=[getyourkarthick]("http://ubuntuforums.org/member.php?u=891422")]I have read many tutorials but nothing seems to get work..How to access windows from ubuntu...?
[/QUOTE]
What exactly does "access windows XP from Ubuntu mean?". Do you want to access another PC with windows on it from Ubuntu or do you want to run windows "inside" Ubuntu using a VM? or do you want to dual boot? or do you just want to access the windows disk?
Please explain you problem in more detail.

---

### Post by Morbius1 on 2010-10-06
What happens when you go to Places > Network ?

Do you not see the Windows machine?

---

### Post by k33bz on 2010-10-06
you need to download and install an ssh client for windows (install on windows) here is a good free one
[http://www.putty.org/]("http://www.putty.org/")

Once that is done, you need to find out what your windows machine's IP address is. For example lets say it is 192.168.1.2.

Now go to your terminal on your Linux machine
```
ssh windowsusername@192.168.1.2
```
(replace windowsusername with a usersname account that is on windows)
it will ask for a password, enter the password of the users account. And wala! Your in!

If you need a gui then
```
ssh -x windowsusername@192.168.1.2
```

---

### Post by karthick87 on 2010-10-06
i want to access another windows pc from ubuntu.

---

### Post by Morbius1 on 2010-10-06
Is it just me or is this beginning to resemble the pakleds episode on star trek next generation.

**[Pakled Captain Grebnedlog]("http://www.imdb.com/name/nm0490383/")**: We look for things.   
 **[Commander William T. Riker]("http://www.imdb.com/name/nm0000408/")**: What were you looking for?  
 **[Pakled Captain Grebnedlog]("http://www.imdb.com/name/nm0490383/")**: Things we need.  
 **[Commander William T. Riker]("http://www.imdb.com/name/nm0000408/")**: Can you be more specific?  
 **[Pakled Captain Grebnedlog]("http://www.imdb.com/name/nm0490383/")**: Things that make us go...

---

### Post by Calash on 2010-10-06
> **getyourkarthick said:**
> i want to access another windows pc from ubuntu.

Access the files or Access the desktop and remote control?

---

### Post by karthick87 on 2010-10-07
I have downloaded putty for windows,what settings should i give in windows...

---

### Post by luvshines on 2010-10-07
You can't ssh into Windows since there is no sshd running on windows.
Did you try remote desktop ?? I always use krdc client to connect to windows from Ubuntu
You may also opt for vncserver running on windows and vncclient on ubuntu

---

### Post by karthick87 on 2010-10-07
> **k33bz said:**
> you need to download and install an ssh client for windows (install on windows) here is a good free one
[http://www.putty.org/](http://www.putty.org/)

Once that is done, you need to find out what your windows machine's IP address is. For example lets say it is 192.168.1.2.

Now go to your terminal on your Linux machine
```
ssh windowsusername@192.168.1.2
```(replace windowsusername with a usersname account that is on windows)
it will ask for a password, enter the password of the users account. And wala! Your in!

If you need a gui then
```
ssh -x windowsusername@192.168.1.2
```


karthick@Ubuntu-desktop:~$ ssh windows@14.96.59.178
ssh: connect to host 14.96.59.178 port 22: Connection timed out

---

### Post by luvshines on 2010-10-07
> **getyourkarthick said:**
> karthick@Ubuntu-desktop:~$ ssh windows@14.96.59.178
ssh: connect to host 14.96.59.178 port 22: Connection timed out

What you need is an ssh server on windows. Once that is setup, you can simply ssh from ubuntu machine to windows.

Putty is just an ssh client which requires ssh server on the other side ie the server side to connect to

**I would still opt for remote desktop or vnc server. What exactly do you want to do after ssh'ing to windows ??**

---

### Post by karthick87 on 2010-10-07
Just i want to access the windows desktop,and i want to control it..From where i can get ssh server for windows...

---

### Post by luvshines on 2010-10-07
> **getyourkarthick said:**
> Just i want to access the windows desktop,and i want to control it..From where i can get ssh server for windows...

Then I think you need remote desktop not ssh server.
Try krdc client to connect to the desktop.

There is also a default rdp client with Ubuntu but I don't like it since it uses command line **with weird options** to launch

---

