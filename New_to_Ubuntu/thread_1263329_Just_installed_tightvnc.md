---
title: "Just installed tightvnc"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Bensky5012 on 2009-09-10
Now how do I launch the application?

---

### Post by Excedio on 2009-09-10
> **Bensky5012 said:**
> Now how do I launch the application?

Open a terminal and type:
```
vncviewer *ipaddress:portnumber*
```

---

### Post by Bensky5012 on 2009-09-10
so this doesnt work like secure shell at all?

I need to login to my teachers server and I don't know the ip address or what port I am supposed to use.  I only know the url of the server.

scratch that I have host name and port, can I access it with these two?

---

### Post by Excedio on 2009-09-10
Try
```
vncviewer url
```

---

### Post by Bensky5012 on 2009-09-10
```

ben@ben-laptop:~$ vncviewer sl-lamp.sl.psu.edu
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server

```

---

### Post by Excedio on 2009-09-10
Sorry...i'm out of ideas. :???:

---

### Post by Excedio on 2009-09-10
Is this the kind of server the has a desktop or is this purely CLI?

---

### Post by Bensky5012 on 2009-09-10
Its purely CLI I believe

---

### Post by drinkpepsi on 2009-09-10
Command Line Interface

---

### Post by mapes12 on 2009-09-11
If the 2 machines you are trying to connect are on a local LAN you may have better success with SSH. Post back if you want a HowTo.

If you're trying to connect outside your LAN i.e. over the internet then post back for some more ideas.

Mark

---

### Post by Bensky5012 on 2009-09-11
Do they offer SSH for ubuntu?

---

### Post by Excedio on 2009-09-11
> **Bensky5012 said:**
> Do they offer SSH for ubuntu?
 
Yes
```
sudo apt-get install openssh
```
If the computr you are trying to get into is CLI, then VNC is not what you need. VNC is to see the Desktop and control windows and programs. SSH is definately what you need.
 
Feel free to keep tightvnc installed though, I use VNC on a daily basis and it extremely helpful.

---

### Post by mapes12 on 2009-09-11
It goes like this for me:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```is a meta package and will install both applications

2.) Find out the IP addresses of the computer you want to connect to.

```
ifconfig
```

this should give you an output just like this one

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
- Choose SSH as the service type from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

### Post by dearingj on 2009-09-11
Can you login using secure shell? If so, and if you installed tightvnc using the xtightvncviewer package, then you could try this:

```
vncviewer -via username@url localhost:0
```

Replace username with whatever name you use to log in using secure shell, and url with the url of the server you're trying to connect to.

Edit: Just saw your post saying that this server is "purely CLI I believe". VNC won't work in that case. If you're looking for a utility that will let you and somebody else access a terminal and see what the other is typing, I suggest you look into the program Screen. It's in Ubuntu's repositories.

---

### Post by Excedio on 2009-09-11
> **mapes12 said:**
> It goes like this for me:
 
I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.
 
1.) Make sure the openssh-server and openssh-client are installed on both machines.
 
```
sudo apt-get install ssh
```is a meta package and will install both applications
 
2.) Find out the IP addresses of the computer you want to connect to.
 
```
ifconfig
```
 
this should give you an output just like this one
 
 
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).
 
So, in my case the address would be 192.168.1.68
 
3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser
 
Click OK
You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.
 
Now a folder should open with the folder on the other machine.
 
From this folder you will be able to browse the other machine and transfer files back and forth.
 
Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.
 
Hope this helps.
 
w o w....that's just dwarfed my post......
 
do what he said :D

---

