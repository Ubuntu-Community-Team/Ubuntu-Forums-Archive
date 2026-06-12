---
title: "Using a USB cable to connect 2 PCs"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by mlthmp on 2009-08-28
Have a question for you guys.

My main system (Desktop) doesn't have a CD Burner on it (how old school is that? lol) Anyway, Im wanting to know if I can use a USB cable to hook my desktop to my Acer laptop (which thankfully does have a CD burner) so I can transfer files from one to the other easily.

Im sure this is likely something fairly easy, but I cannot seem to think up the right combination of words to search for to find the answer. Also, each system is running 8.10

Any help is greatly appreciated.

---

### Post by hansdown on 2009-08-28
Hi mlthmp.

Be very careful to use a "bridged" USB-USB cable.

[http://www.hardwaresecrets.com/article/248](http://www.hardwaresecrets.com/article/248)

[http://www.google.ca/search?q=Using+a+USB+cable+to+connect+2+PCs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Using+a+USB+cable+to+connect+2+PCs&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by achianese on 2009-08-28
These computers are not on a network? Are you sharing an internet connection using a router or something? If so, you wouldn't need the usb cable.

---

### Post by mlthmp on 2009-08-28
> **hansdown said:**
> Hi mlthmp.

Be very careful to use a "bridged" USB-USB cable.

[http://www.hardwaresecrets.com/article/248](http://www.hardwaresecrets.com/article/248)



I do not have a bridged cable ATM, but if I need one I'll get one in a couple of days. Im glas I checked that link before I threw a normal USB cable between them, Thanks! I owe you, lol


[quote=achianese;7863370]These computers are not on a network? Are you sharing an internet connection using a router or something? If so, you wouldn't need the usb cable.[/quote

Yes, both my Desktop and Laptop are running through my LinkSys router (wired connections right to the router) However I would have no clue as how to go about setting anything up like that. While I've used computers for several years I am by far not a wiz with them. Can I transfer files this way through my router?

---

### Post by DFlame on 2009-08-28
Yes, you can. Are both computers running Ubuntu/Linux or does one of them use XP/Vista?

---

### Post by mlthmp on 2009-08-28
> **DFlame said:**
> Yes, you can. Are both computers running Ubuntu/Linux or does one of them use XP/Vista?

Both are running Ubuntu version 8.10 .. thanks again for helping me get pointed in the right direction =)

---

### Post by achianese on 2009-08-28
You definitely can transfer the files over your home network, and I suspect that is easier than using the usb cable. There are several ways you could accomplish this.. Are both computers using Ubuntu?

---

### Post by mlthmp on 2009-08-28
> **achianese said:**
> You definitely can transfer the files over your home network, and I suspect that is easier than using the usb cable. There are several ways you could accomplish this.. Are both computers using Ubuntu?

Yes. both use 8.10

---

### Post by achianese on 2009-08-28
You could do this using NFS or SAMBA, but I'll describe the way I think would be easiest, using ssh and nautilus.

Open a terminal window under applications-accessories. First, install sshd on your desktop by typing:

```
sudo apt-get install ssh
```

Find out the ip address of the desktop. Listed under wlan for wireless or eth0 for wired.

```
ifconfig
```

Then go to the laptop and go to places-connect to server. Choose Service type as SSH, for Server, type your ip address, and enter your username. You should get a Nautilus window showing the other computer, starting in your home folder. You can even create a bookmark to do this multiple times, although your ip address might change.

If I've forgotten any steps, someone please help out (Does ssh need to be started manually once installed?)

---

### Post by achianese on 2009-08-28
Oh, the ip address is listed as "inet", and for most home networks will be something like 192.168.1.xxx

---

### Post by DFlame on 2009-08-28
> **achianese said:**
> If I've forgotten any steps, someone please help out (Does ssh need to be started manually once installed?)

This should work, I almost had it typed out :P The server should start automatically on installation :)

---

### Post by mlthmp on 2009-08-28
> **achianese said:**
> You could do this using NFS or SAMBA, but I'll describe the way I think would be easiest, using ssh and nautilus.

Open a terminal window under applications-accessories. First, install sshd on your desktop by typing:

```
sudo apt-get install ssh
```Find out the ip address of the desktop. Listed under wlan for wireless or eth0 for wired.

```
ifconfig
```Then go to the laptop and go to places-connect to server. Choose Service type as SSH, for Server, type your ip address, and enter your username. You should get a Nautilus window showing the other computer, starting in your home folder. You can even create a bookmark to do this multiple times, although your ip address might change.

If I've forgotten any steps, someone please help out (Does ssh need to be started manually once installed?)

Wow, that really was easy. That totally worked. I was able to access the files on my desktop from my laptop just like that. Thanks! 

I really appreciate it.

---

### Post by achianese on 2009-08-28
Glad I could help.

---

### Post by hansdown on 2009-08-28
Nice work achianese.=D>

---

### Post by bravo sierra echo on 2009-10-08
I've come across this thread while trying to connect two desktops, with the intention of backing one of them up onto the HD of the other one.  The "server" is running Kubuntu Jaunty, the "client" - ie the machine I want to back up - is running Xubuntu Jaunty.  No matter what I try, I get a "connection refused by peer" error.  They *can* ping each other.

Help?

---

### Post by alphaniner on 2009-10-08
Some more details would be helpful.  What command are you running that gives the 'connection refused' error?

---

### Post by bravo sierra echo on 2009-10-08
Sorry, should have been clearer!  I get that using Putty on the Kubuntu machine and Gigolo which is built into Xubuntu.  Something to do with the firewall setup?

I'm a bit out of my depth here, as the last time I tried to do this using sshfs it just worked out of the box, connecting an Ubuntu Hardy machine to a Mac straight away.

---

### Post by alphaniner on 2009-10-08
What do you get if you just do

```
ssh <IP of server>
```

from the client machine?

Also, you should probably start your own topic, you will probably get better support that way.

---

### Post by bravo sierra echo on 2009-10-08
Same again :(

Will do, thanks anyway for your help so far!

---

