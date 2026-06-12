---
title: "connect two computers"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by andres-bracho on 2009-08-18
In Windows I just use the same network name and it's done, now in Ubuntu...

I have an Acer Aspire 9300 (Ubuntu 9.04) and an Acer Aspire One (EEEbuntu updated to Ubuntu 9.04), I also have a crossover cable... now tell me how can I share a folder between both computers to exchange some files without loosing the normal ability of both computers to connect independently to Internet...

Very basic instructions, please...

Thanks in advance.

---

### Post by LowSky on 2009-08-18
how about a better idea

[http://www.getdropbox.com/](http://www.getdropbox.com/)

or [https://ubuntuone.com/](https://ubuntuone.com/) ( not sure if it is still in private beta, worth a look) I like it

---

### Post by SuperSonic4 on 2009-08-18
You can use ssh to connect, it's even easier if one has a static IP address

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

### Post by bear24rw on 2009-08-18
on both computers

```
sudo aptitude install openssh-server filezilla
```

now you can use filezilla to connect to each other, or go to places > connect to server select ssh and then enter in the ip of the other one. it will then show up as a folder

---

### Post by andres-bracho on 2009-08-18
LowSky what if your need to connect both computers and don't have Internet...?

SuperSonic4 if I configure a static IP does that affect my hability to connect to internet later?

And thanks you a lot... but don't you have something more simple and basic? those instructions are quite confusing for me... :confused::confused::confused:

bear24rw that sounds easier but, same question with IP's...

---

### Post by JK3mp on 2009-08-18
> **supersonic4 said:**
> you can use ssh to connect, it's even easier if one has a static ip address

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

+1

---

### Post by bear24rw on 2009-08-18
you need to get a router or a switch, if you use a cross over cable there goes your ethernet ports..

BUT!

if you click on network manager and go to creat new connection, give it a name and click okay or next or whatever let it finish then on the other computer search for wireless networks and connect to the network name you just name

then in the console on each computer

ifconfig

and look for the ip address use that ip in filezilla or the connect to server dialog

---

### Post by bear24rw on 2009-08-18
> **SuperSonic4 said:**
> You can use ssh to connect, it's even easier if one has a static IP address

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

those instructions are WAYYYY over complicated..

---

### Post by mapes12 on 2009-08-18
It goes like this for me: 

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way I know.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through.

```
sudo apt-get install openssh-server
```

2.) Find out the IP addresses of your computer. Use the following command to obtain your computers IP address

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
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter.

So, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click ok
You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

### Post by SuperSonic4 on 2009-08-18
> **bear24rw said:**
> those instructions are WAYYYY over complicated..

I'd use external storage or dropbox in that case but it is worth learning - ubuntugeek has very user-friendly advice

---

### Post by andres-bracho on 2009-08-18
Thank you mapes12... now I understood... sounds simple enough... I'll try it...   : )

---

### Post by mapes12 on 2009-08-18
> **andres-bracho said:**
> Thank you mapes12... now I understood... sounds simple enough... I'll try it...   : )You are most welcome :guitar:

---

