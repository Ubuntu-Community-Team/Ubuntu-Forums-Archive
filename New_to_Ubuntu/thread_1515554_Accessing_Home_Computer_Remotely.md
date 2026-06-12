---
title: "Accessing Home Computer Remotely"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by zer010 on 2010-06-22
I would like to know how to access my files remotely, from any other internet-connected computer.  Also, is it possible to install new software on the home computer, remotely?

---

### Post by CharlesA on 2010-06-22
Use SSH or FreeNX.

---

### Post by karthick87 on 2010-06-22
I have the same question..Can you explain me a bit more..I am not using a static ip so how to setup SSH...?

---

### Post by bodhi.zazen on 2010-06-22
> **getyourkarthick said:**
> I have the same question..Can you explain me a bit more..I am not using a static ip so how to setup SSH...?

You will need to know your public IP. 

You can then register with a services such as DynDNS

[http://www.dyndns.com/](http://www.dyndns.com/)

There are other options.

Once you register with such a service there are several scripts to update your ip address to dyndns, the service you use will give you the technical details.

You then forward port 22 from your router to your ssh server.

Be sure to secure ssh. At a minimum, I suggest ssh keys, disable passwords, and use denyhosts, fail2ban, or iptables to block dictionary attacks.

---

### Post by kwacka on 2010-06-22
As you don't have a static IP you will need one of the 'Dynamic DNS' name servers:  see [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

For SSH see: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

For FreeNX (my preferred choice) see: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by marbertone on 2010-06-22
Hi,
I use ssh everyday for work. Well... first of all, as someone said, you have to know the ip of the computer you want to connect to. It can be done with the following command:

```
 ifconfig | grep inet 
```

you will understand what is your ip between the three or four that will appear (127.0.0.1 won't be your ip, not even 192.167.0.1 or something like this, a more probable ip should be 97.63.x.x - I just invented it).

Well... you should install OpenSSH (you can find it in the repositories), then you will have to write on the pc you want to use to access the other pc the following commands:

```
 ssh username@96.73.c.c -X 
```

(I use the -X option to have the X terminal, say the graphics: if you'll write 'firefox' the browser loaded onto your remote pc will appear in the local pc.)

I assume that you must have created a username (it is created *automatically* w/ Ubuntu, i.e. if you have Karmic on both the pc's (but also other linux distros) you just have to install OpenSSH: the username of the remote pc will be the username you usually log in when you're physically there.

Other commands, very useful:

to transfer files:

```
 scp (local file) username@(ip address):/home/username/(folder) 
```

it can be used also in the reverse way:

```
 scp username@(ip address):~/path/ ~/username/local\ folder 
```

(use scp -r to enable the recurse folder option)

to sync two folders:

```
 rsync -avz ~/username/local\ folder username@(ip address):~/user2/path 
```
 
(-avz for recurse folder)

Also rsync can be used in the reverse way (I omit the example :P)

Hope this helps!
Cheers,
Mario Alberto:popcorn:

---

### Post by marbertone on 2010-06-22
Of course, once you are logged in the remote computer, you can clearly type ```
 sudo apt-get install (...) 
```

and also

```
 sudo apt-get upgrade 
```

Cheers!
M.A.

---

### Post by CharlesA on 2010-06-22
An easier way to get your external IP address is to go to something like whatismyip.com.

As for your internal one, ifconfig or checking that router works for that.

---

### Post by zer010 on 2010-06-22
ok, say i'll go with ssh, can i access my ubuntu comp from a Win comp?

---

### Post by bodhi.zazen on 2010-06-22
> **zer010 said:**
> ok, say i'll go with ssh, can i access my ubuntu comp from a Win comp?

yes, use putty

---

### Post by zer010 on 2010-06-22
cool, i guess i got a lot more research ahead of me...lol

---

