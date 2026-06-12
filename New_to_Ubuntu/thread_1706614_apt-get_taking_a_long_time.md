---
title: "apt-get taking a long time"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by xCiDiC on 2011-03-14
Hi, i have just installed ubuntu server 10.10

With it i installed openssh & lamp

I wanted to install more packages so i did

```
sudo apt-get update
```and its now into the 5th hour

is that a normal time frame?

---

### Post by milindo on 2011-03-14
What's the connection speed?

---

### Post by mcduck on 2011-03-14
I suppose that depends on the speed of your Internet connection. Still, it would have to be pretty slow one for that to take *hours*, it's roughly 5-10 seconds for me...

Is it actually doing anything? Did you install LAMP & openssh from the repositories? In that case they should be working, but without seeing the output from apt-get update it's pretty hard to say what could be the problem on your system. Sounds like some kind of connection issue, though.

---

### Post by xCiDiC on 2011-03-15
my max speed i can get is 2.4/mbs so its pretty fast

---

### Post by wojox on 2011-03-15
You type in 

```
sudo apt-get update
```

and it just sits there? Are you using a proxy?

---

### Post by xCiDiC on 2011-03-15
No i do not sue a proxy it displays 
0% waiting for headers

---

### Post by wojox on 2011-03-15
Ctrl+C will stop it. What does this look like:

```
cat /etc/apt/sources.lst
```

---

### Post by Paqman on 2011-03-15
In the Software Sources window (accessible through Synaptic or Update Manager) you can get it to scan for the fastest available server.

---

