---
title: "Remote access ubuntu."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-27
Hi guys,

I have two computers at home both with ubuntu 9.04 installed (one with 64bit and the other with 32bit) What is the best way of using my other laptop remotely? THX, /A

---

### Post by sahabcse on 2009-08-27
Hi

GO system >> Preference >> Remote Desktop

or 

Install open-ssh client

---

### Post by wojox on 2009-08-27
Do you have a router and lan set up?
OpenSSH is good. Both through the terminal and graphicaly.
There's another tightVNC I think?

---

### Post by nothingspecial on 2009-08-27
```
sudo apt-get install openssh-client openssh-server
``` on both machines.

Gui way

Places > connect to server

In the top box change it to ssh

In the second box type username@ipadress
You can find out your laptops ip adress by right clicking on the network icon and choosing connection information.

There is an option to add a bookmark so you don`t have to do this again.

Click connect.

Command line
```

ssh -X -C -c blowfish username@ipaddress
```

---

### Post by fishy6969 on 2009-08-27
If you want a full remote desktop FreeNX is definitely the way to go. Details here - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by lover_of_sc on 2009-08-27
I have a home network using a router access to internet (virgin media router). I have installed SSH on both computers and used (user name on remote computer)@192.168.1.3 - an error message appears with  

Cannot display location "sftp://hp@192.168.1.3/" Connection refused by server.

??

Thx for your help guys

---

### Post by fishy6969 on 2009-08-27
I'm a bit confused. Are you trying to access the machine from the same LAN or over the internet?

---

### Post by mapes12 on 2009-08-27
> **lover_of_sc said:**
> Hi guys,

I have two computers at home both with ubuntu 9.04 installed (one with 64bit and the other with 32bit) What is the best way of using my other laptop remotely? THX, /A
What do you want to do, share files or take control of the remote desktop, or both?

---

### Post by lover_of_sc on 2009-08-27
Sorry for not being clear enough, yes I would ideally like to take full control over my other laptop and share files between them both located on the same network, I have a broken screen on my second computer and have it connected to my tv. I would like to use that via my other laptop.

---

### Post by fishy6969 on 2009-08-27
Understood. Is the openssh server installed on the machine you want to connect to? If not then -

```
sudo apt-get install openssh-server
```

---

### Post by mapes12 on 2009-08-27
> **lover_of_sc said:**
> Sorry for not being clear enough, yes I would ideally like to take full control over my other laptop and share files between them both located on the same network, I have a broken screen on my second computer and have it connected to my tv. I would like to use that via my other laptop.For remote desktop control I use [http://www.yuuguu.com/home](http://www.yuuguu.com/home) and for file sharing I use [http://www.getdropbox.com/](http://www.getdropbox.com/) :P

If you ever get ssh to work over the internet then please post back because I tried for ages and failed :(

---

### Post by lover_of_sc on 2009-08-27
Oh fantastic, that helped I can now access all files on the other computer. How do I control so that I can for example start playing a movie on the other computer? Thx

---

### Post by ayenack on 2009-08-27
This should help you.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by nothingspecial on 2009-08-27
> **nothingspecial said:**
> ```
sudo apt-get install openssh-client
``` on both machines.

Gui way

Places > connect to server

In the top box change it to ssh

In the second box type username@ipadress
You can find out your laptops ip adress by right clicking on the network icon and choosing connection information.

There is an option to add a bookmark so you don`t have to do this again.

Click connect.

Command line
```

ssh -X -C -c blowfish username@ipaddress
```

oops forgot that bit. Edited original post.

---

### Post by lover_of_sc on 2009-08-27
Ah it's working now, vinagre worked like a charm!! Problem sorted. Thx all.

---

