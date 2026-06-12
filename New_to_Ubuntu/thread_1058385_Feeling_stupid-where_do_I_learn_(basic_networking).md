---
title: "Feeling stupid-where do I learn? (basic networking)"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by pstrbrc on 2009-02-02
OK, I have a dual-boot on my laptop w/8.04. I am trying to set up a converted desktop unit to work as a server, and have loaded 8.04 and apt-got (can I say it that way?) LAMP-server, SSH-server, and DNS-server. OK so far. When I open Firefox and go to "localhost" I get the "It works!" message, so at least *something's* working right! 
But there's so much more to learn! 
Problem #1: My internet provider has given me a static IP. I am using a Belkin router, which I have successfully set up for this. When I'm running Ubuntu on my laptop and am plugged into the network, I can find the other office computer, as well as the router. (under places/network through the task bar.) BUT... no server. And from my server, I can't find the laptop or the windows desktop. These seem to be things I need to straighten out before I can run my laptop/ as an SSH client for my server. Help!!

---

### Post by yeats on 2009-02-02
You might want to read through this thread, which has some similar questions:

[http://ubuntuforums.org/showthread.php?t=1055723]("http://ubuntuforums.org/showthread.php?t=1055723")

but it sounds like you would do well learning about Samba, in which Linux uses the SMB protocol (that Windows uses) to make itself available to Windows clients.  Here are some basics:

[http://us3.samba.org/samba/]("http://us3.samba.org/samba/")
[http://tinyurl.com/cs3bxe]("http://tinyurl.com/cs3bxe") (a Google books version of Using Samba)

and it's in the repos:

```
sudo apt-get install samba
```

---

### Post by pstrbrc on 2009-02-02
> **chrissharp123 said:**
> You might want to read through this thread, which has some similar questions:

[http://ubuntuforums.org/showthread.php?t=1055723]("http://ubuntuforums.org/showthread.php?t=1055723")


Hmmm...
Been through that post, that's the stuff I already found out about. Yes, my router is set for static IP, I've changed the etc/network/interfaces file to reflect the fixed ip. But I can't find it when I go to [places/connect to server/ssh] on the Ubuntu laptop.
otoh, I'm on the internet right now through a network cable to the router, and the laptop's etc/network/interfaces file reads as follows:
> auto lo
iface lo inet loopback

Shouldn't it read something like
> auto eth0
iface eth0 inet dhcp

Help! Someboty through me a rope! I'm over my head!:-s

---

### Post by albinootje on 2009-02-02
> **pstrbrc said:**
> But I can't find it when I go to [places/connect to server/ssh] on the Ubuntu laptop.

Did you try sftp://ip_address/ in the location bar of the file manager ?
See attached screenshot.
Are you using ip addresses or hostnames ? 
If the latter, how is your DNS configured exactly ?
> 
otoh, I'm on the internet right now through a network cable to the router, and the laptop's etc/network/interfaces file reads as follows:


For a server you would to edit /etc/network/interfaces manually (although I've read that wicd seems to be able to work on a server without GUI too), but for a desktop with NetworkManager you normally don't need to edit that file.

---

### Post by handydan918 on 2009-02-02
I would suggest opening a terminal and doing ```
ssh 192.168.1.4
```or whatever the ip address is of the host in question. If this doesn't work, try pinging the box.

---

### Post by jimmy the saint on 2009-02-02
+1 for starting out by pinging the box
```
ping <ipadress>
```

That can save you a lot of time trying to ssh into a box you can't even connect to!

---

### Post by handydan918 on 2009-02-02
```
ping -c 3 <ipaddress>
```

And you won't have to worry about doing CTRL c to stop it!

---

### Post by pstrbrc on 2009-02-03
OK, I've pinged and sshed. 
> pstrbrc@pstrbrc-laptop:~$ ping 192.168.2.4
PING 192.168.2.4 (192.168.2.4) 56(84) bytes of data.
64 bytes from 192.168.2.4: icmp_seq=1 ttl=64 time=0.248 ms
64 bytes from 192.168.2.4: icmp_seq=2 ttl=64 time=0.238 ms
64 bytes from 192.168.2.4: icmp_seq=3 ttl=64 time=0.246 ms
64 bytes from 192.168.2.4: icmp_seq=4 ttl=64 time=0.243 ms

--- 192.168.2.4 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.238/0.243/0.248/0.019 ms
pstrbrc@pstrbrc-laptop:~$ ssh 192.168.2.4
The authenticity of host '192.168.2.4 (192.168.2.4)' can't be established.
RSA key fingerprint is 9b:7f:45:65:a7:ae:8c:f5:99:c5:e9:30:23:90:d8:b9.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.
pstrbrc@pstrbrc-laptop:~$ 


If I read this correctly, my laptop was able to send a ping to the server, and got it back correctly. Right? So what's the next step in setting up the ssh relationship?

---

### Post by hovzio on 2009-02-03
You have to type "yes" for host based auth.. Then you will be logged in, literally type yes, a y wont do.

EDIT: syntax for ssh is also wrong, syntax goes:

ssh user@192.168.2.4

replace user with the username of remote box and use proper ip.

---

### Post by handydan918 on 2009-02-03
> **hovzio said:**
> You have to type "yes" for host based auth.. Then you will be logged in, literally type yes, a y wont do.

EDIT: syntax for ssh is also wrong, syntax goes:

ssh user@192.168.2.4

replace user with the username of remote box and use proper ip.
Funny, it isn't wrong on my network. I always use ```
ssh <ip_addy>
```
:D

---

### Post by hovzio on 2009-02-03
> **handydan918 said:**
> Funny, it isn't wrong on my network. I always use ```
ssh <ip_addy>
```
:D

apologize if I am mistaken, this doesn't work for me.. but one question, how does the ssh server know who to login as? Does it automaically revert to to the root account?

What is "addy"?

---

### Post by handydan918 on 2009-02-03
> **hovzio said:**
> apologize if I am mistaken, this doesn't work for me.. but one question, how does the ssh server know who to login as? Does it automaically revert to to the root account?

What is "addy"?

Sorry for the poor abbreviation. I intended "address" by "addy". On my network, I have all hosts set to dis-allow root logins at all, so no, it doesn't default to root. However, I also use all the same usernames on all my machines, so it never seems to get confused.

---

### Post by albinootje on 2009-02-04
> **hovzio said:**
> how does the ssh server know who to login as? Does it automaically revert to to the root account?

If you're logged in as user jonathan, then you'll see the difference between :
```

ssh -v ssh-server-ip-address
ssh -v jane@ssh-server-ip-address
ssh -v mary@localhost

```
Only at the first of the three examples jonathan will be trying to log in via ssh with username jonathan.

---

