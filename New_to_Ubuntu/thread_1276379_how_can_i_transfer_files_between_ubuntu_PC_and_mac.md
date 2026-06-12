---
title: "how can i transfer files between ubuntu PC and mac using ethernet cable?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by kaston on 2009-09-27
i'm trying to transfer a large amount of data (~100GB) from a PC running hardy heron to a macbook pro running snow leopard.  both computers are connected to the internet through my wireless modem but i know that it should be possible to do this using only an ethernet cable connecting the two, which i have, and i'd like to know how to do this.  

i am quite a noob so very detailed instructions would be appreciated.  thanks a lot.

---

### Post by mapes12 on 2009-09-27
> **kaston said:**
> i'm trying to transfer a large amount of data (~100GB) from a PC running hardy heron to a macbook pro running snow leopard.  both computers are connected to the internet through my wireless modem but i know that it should be possible to do this using only an ethernet cable connecting the two, which i have, and i'd like to know how to do this.  

i am quite a noob so very detailed instructions would be appreciated.  thanks a lot.I haven'tgot a Mac but you should be able to do this using SSH on both machines. You can setup SSH on the Mac: [http://www.google.co.uk/#hl=en&q=mac+ssh&meta=&fp=5314e9eaa343dff4](http://www.google.co.uk/#hl=en&q=mac+ssh&meta=&fp=5314e9eaa343dff4)

and this is how I use SSH between two Ubu boxes. Adapt accordingly:


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

### Post by KIAaze on 2009-09-27
> **kaston said:**
> it should be possible to do this using only an ethernet cable connecting the two

As far as I know, it must be a [crossover cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")!!!

P.S.: Once the networking is set up correctly, I think you should be able to use any file transferring system, not just ssh.
ex: scp, ftp, sftp, etc

---

### Post by kaston on 2009-09-27
thanks for the reply.  i ended up specifying a random static ip address for my wired connection in system>admin>network.  then i shared the folder i wanted via the right click menu and it immediately popped up on my mac desktop.  come to think of it i probably didn't need to specify any address and it would have detected it as soon as i shared the folder.  

i guess i'm not using ssh but i figure it's pretty secure since it's just my 2 laptops wired together

---

