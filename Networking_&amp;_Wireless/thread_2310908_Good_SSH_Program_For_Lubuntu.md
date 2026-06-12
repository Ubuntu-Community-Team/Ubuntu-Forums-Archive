---
title: "Good SSH Program For Lubuntu"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by bigpappajohn1984 on 2016-01-22
I have a bitvise SSH server up and running but I see that bitvise client is only for Windows.  What is a good (easy to understand) SSH client to use in Lubuntu?

EDIT --
What I like about bitvise for windows is the second the connection is succesful, I get a window that pops up showing (I believe I show right order) on the left my host machine and on the right the machine I just SSH into, for quick file copy. Ideally I would like something similar.

---

### Post by 1clue on 2016-01-22
Openssh is already installed.

---

### Post by bigpappajohn1984 on 2016-01-22
How would I use it?  Sorry for my very noobish ?'s

---

### Post by Dennis N on 2016-01-22
You need a tutorial. Here is one, but you can Google "using openssh Ubuntu" for many others.
[https://chrisjean.com/ssh-tutorial-for-ubuntu-linux/](https://chrisjean.com/ssh-tutorial-for-ubuntu-linux/)

---

### Post by bigpappajohn1984 on 2016-01-22
Thank you for that article.  I tried to follow it, but was unsuccesful.
Lets say my the below is true
Host name: fire.homeftp.org 
User name: badapple
Password: testpw
Port: 22

If I input that into a text file as suggested and save.  Then run ssh fire.homeftp.org I get an error of connection refused.

And googling most of the results I see say to install SSH Server, this will be my client PC not my server.

> **Dennis N said:**
> You need a tutorial. Here is one, but you can Google "using openssh Ubuntu" for many others.
[https://chrisjean.com/ssh-tutorial-for-ubuntu-linux/](https://chrisjean.com/ssh-tutorial-for-ubuntu-linux/)

UGGH - I just realized what my issue is.  I am connecting from internal (on my LAN) and the hostname will not always resolve properly this way.

And as a second note all I had to do was open my file browswer and click on GO --> Connect To Server and enter the info at that point.  Then I bookmarked the site for quick access.

Hopefully it will be just the same from outside of my network, except not using IP Ill actually use host name.

---

### Post by 1clue on 2016-01-22
You really need to change your password right now if you shared the real one.

---

### Post by SeijiSensei on 2016-01-23
Edit the /etc/hosts file with "sudo nano /etc/hosts" and add an entry for the machine you're trying to connect to like this:
```
10.10.10.10    myserver somealias anotheralias
```
replacing "10.10.10.10" with the server's IP address. The aliases are optional and "myserver" can be a fully-qualified name like "myserver.example.com" or just a simple hostname.  Then open a terminal and type
```
ssh myserver
```
to connect.

---

### Post by bigpappajohn1984 on 2016-01-23
> **1clue said:**
> You really need to change your password right now if you shared the real one.

Haha, no all of that was garbage.  Even the host name was made up.

> **SeijiSensei said:**
> Edit the /etc/hosts file with "sudo nano /etc/hosts" and add an entry for the machine you're trying to connect to like this:
```
10.10.10.10    myserver somealias anotheralias
```
replacing "10.10.10.10" with the server's IP address. The aliases are optional and "myserver" can be a fully-qualified name like "myserver.example.com" or just a simple hostname.  Then open a terminal and type
```
ssh myserver
```
to connect.

Thank you for this invaluable piece!

---

