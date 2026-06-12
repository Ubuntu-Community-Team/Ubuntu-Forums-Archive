---
title: "Installing ndiswrapper problems on feisty"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by atvar on 2008-03-08
Okay, I've been trying to get an internet connection on my linux box for some time. I don't have the ability to get a wired connection to it, so I have to do everything manually via a jumpdrive for the packages needed.

Right now, I am attempting to install ndiswrapper 1.38, but I get a whole bunch of errors when I attempt to do the make commands.

I go:

```
sudo make uninstall
```

and it seems to complete successfully.

Next I go 

```
sudo make
```

and it gives me a ton of errors, the last three lines of which are:

```
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory '/usr/src/ndiswrapper-1.38/utils'
make: *** [all] Error 2
```

Theres obviously a problem here.. and, being a newbie I can't seem to identify the cause and remedy it. So, being a newbie, I attempted

```
sudo make install
```

and I got the same errors as I got with sudo make.

At this point, I'm completely confused. The only thing I can think of that would be causing it would be my kernel is not at least 2.6.6 or 2.4.26, as
```
ls /lib/modules/'uname -r'/build
```

returns

```
ls: /lib/modules/uname -r/build: No such file or directory
```

Help a poor newbie to make this card work? :) lol

Oh, the card I am attempting to install is a Netgear WG121 Wireless adapter.

---

### Post by 1010011010 on 2008-03-08
If it's a .tgz file, you need to...

```
tar xvf *filename*.tgz
```

next...

```
cd *filename*
```

next...

```
sudo make
```

and finally...

```
sudo make install
```

---

### Post by kevdog on 2008-03-08
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by atvar on 2008-03-08
I have already unpacked the file. I was actually inside the directory that it was unpacked into.

the path for the file is

/usr/src/ndiswrapper-1.38

The ndiswrapper-1.38.tar.gz is still in the /usr/src folder.

---

### Post by kevdog on 2008-03-08
1.38 is an old version.  Please use a newer version.

---

### Post by atvar on 2008-03-08
> **kevdog said:**
> Check out this thread:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Sadly I do not have an ubuntu 7.04 install cd. I had borrowed a livecd from a friend, and installed it from there. They kept their CD.

---

### Post by kevdog on 2008-03-08
You need the linux headers in order to compile -- hence that probably is the source of your original errors in the first place!!

---

### Post by atvar on 2008-03-08
Probably. I'll go download the install cd and burn it. Maybe that will work. Thanks :)

---

### Post by kevdog on 2008-03-08
Post back if you have problems, your venturing down a road with a lot of landmines but to a destination that thousands have arrived!

---

### Post by atvar on 2008-03-08
Will do. lol. I had it working once upon a time. I think I might just install gutsy considering I can't seem to find a place to download the iso for Feisty so I can use the CD.

---

### Post by atvar on 2008-03-08
I got lucky. My room mate had a good 7.04 cd.. Now the problem I'm running into is this:

I put the cd in, and typed as per your guide:

```
sudo apt-cdrom add
```

So far, so good. Next I enter:
```
sudo aptitude update
```
Here comes the issue.. my computer begins trying to update off of the internet, which it does not have access to...

How do I make it install from the disc?

---

### Post by atvar on 2008-03-08
Ok. apparently the headers are there... 

in /usr/src/ there are four folders:

/usr/src/linux-headers-2.6.20-15

/usr/src/linux-headers-2.6.20-15-generic

/usr/src/linux-headers-2.6.20-16

and

/usr/src/linux-headers-2.6.20-16-generic

Is that normal?

---

### Post by kevdog on 2008-03-09
Yes, but you really only need the header versions for your specific kernel you are using.  Dont worry about it -- keep going!

---

### Post by atvar on 2008-03-10
Update:

I formatted my HD and installed Ubuntu 7.10 Gutsy Gibbon from a live cd I made. I then proceeded to install ndiswrapper 1.51 successfully, and I installed the driver for my Netgear WG121 Wireless USB adapter. Now the problem is it will not connect to any networks. I only get a single green USB connected light, but no Wireless connection light. The computer is registering there is a wireless adapter/driver, however it will not connect. I'm lost again. lol. Made plenty of progress, now for another of those mines. lol

---

### Post by kevdog on 2008-03-10
Can you post the following:

iwlist scan
lshw -C network

---

### Post by atvar on 2008-03-10
Result of:
```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

```

Result of 
```
lshw -C network

For wlan0:
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:a1:7d:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg121 driverversion=1.51+NETGEAR, Inc.,11/13/2003, 1 multicast=yes wireless=IEEE 802.11g

```

I KNOW theres at least two wireless routers out there, as I am sitting on one with my laptop. I also know that this adapter does in fact work. It was my main connection for my windows box for quite a while.

Perhaps I got the wrong driver, or I did something wrong when I installed Ndiswrapper. I don't think there could be any real system conflicts as this is a clean install of gutsy.

---

### Post by kevdog on 2008-03-10
can you do a dmesg (please dont post the whole file), and look for any lines referring to ndiswrapper.  There seems like there would be an error possibly.  Can you also list lspci -nn?

---

