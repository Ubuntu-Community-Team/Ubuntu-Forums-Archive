---
title: "CANNOT get either NFS or Samba running"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by ah pook on 2010-05-28
OK, I'll admit I'm a newbie, but I have a regular desktop, AMD 64bit, running Lucid.Been using Ubuntu for three years now. No problems at all. ( Thanks to everyone). My wife has a Dell mini 10 which I installed Lucid onto, and it works perfectly, for what she wants. Surfing, email, etc. I am totally unable to get them to work together. I'm running a wired connection to the router, she's running wireless. I've followed every instruction for both Samba and NFS, and nothing works. I've spent two weeks on this to no avail. Which should I choose, NFS or Samba, as all I want to do is browse my music directory on her mini, and maybe copy the occasional movie to her hard drive. 

I'm very frustrated. Thanks for letting me vent. I Still love Ubuntu.

---

### Post by chrisod on 2010-05-28
Is file sharing enabled on the both computers? Right click on the folder(s) you want to share and select 'sharing.' You should not need either Samba or NFS for sharing files between 2 Ubuntu boxes.

---

### Post by ah pook on 2010-05-29
Ghod you guys are good! Thanks so much!

---

### Post by mapes12 on 2010-05-29
Hi

From reading the thread on this post I'm not sure if you have a solution to your problem so I thought I would post this just to try and help. For two Ubu boxes you do not need NFS/Samba. To connect Ubu boxes you just need the built in SSH functionality.

It goes like this for me:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

