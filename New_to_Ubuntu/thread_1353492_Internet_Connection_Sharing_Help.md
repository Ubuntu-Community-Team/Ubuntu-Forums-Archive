---
title: "Internet Connection Sharing Help"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-12
Hello everyone!

I am having a problem sharing my network connection with another computer on my network.

I have an old laptop set up with firestarter on it, allowing it to share my internet connection. (the internet-connected interface is wlan0, and the network connected interface is eth0). 

Now I have an ethernet cable running from that laptop into a Hub/Switchy type thing, and then into a Debian server (No GUI) hooked into its ethernet port.

Now The problem is that the internet connection is not transmitting across the cable.

The Hub itself says that both of the computers are connected properly, (green light flashing), but I have no internet on the server.

When I first started the firestarter program(on the laptop), it said that eth0 was not ready. I solved this problem by typing into the terminal:
```

sudo ifconfig eth0 192.168.0.2

```

When I go to my debian server and type:
```

su
ifconfig

```

All that is outputted is the lo interface. What am I doing wrong? Can someone help me?

---

### Post by Iowan on 2009-12-12
I've never used Debian (proper), but I presume it's similar to Ubuntu. 
Check (post) */etc/network/interfaces*.

---

### Post by leprkhn on 2009-12-12
Take a loot at  [THIS]("http://ubuntuforums.org/showthread.php?t=91370") thread. Replace it's internet facing ethX with your wifi.
You may have to set up a static ip on the Debian box. Do so by editing /etc/network/interfaces

---

### Post by darkeye123 on 2009-12-12
Thanks to both of you:

I was following the posted thread when I ran into an issue.

```

brad@brad-laptop:~$ sudo apt-get install ipmasq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ipmasq is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ipmasq has no installation candidate

```

in addition,, I could not perform the echo1 line, even with sudo.
Permission is denied.

The Debian server is recognizing the eth0 port now, after I use ifconfig to manually set the ip.

Still no packets being sent back and forth though.

Will post back with my interfaces file. 

Thank you very much!

---

### Post by darkeye123 on 2009-12-12
That file does not exist in Debian... Or at least not where I looked :P

---

### Post by Iowan on 2009-12-13
That thread is dated 2005 (which doesn't make it wrong). 
 [Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is another help page - dunno if it'll help, or just add confusion.

---

### Post by darkeye123 on 2009-12-13
Thanks again, 
But I just decided to hook the computer into my router. I have some more problems, which are in [this thread]("http://ubuntuforums.org/showthread.php?t=1353968").

---

