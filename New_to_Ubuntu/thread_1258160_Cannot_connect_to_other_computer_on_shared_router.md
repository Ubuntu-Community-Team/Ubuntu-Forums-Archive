---
title: "Cannot connect to other computer on shared router"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by thomas forbes on 2009-09-04
I have 2 computers running jaunty. The are connected to a linksys wrt54g router with LAN cables. I can't file share through them, but I can use the network printer. I have giver installed on both, but they only show the computer they are on. What am I doing wrong?

---

### Post by k33bz on 2009-09-04
> **thomas forbes said:**
> I have 2 computers running jaunty. The are connected to a linksys wrt54g router with LAN cables. I can't file share through them, but I can use the network printer. I have giver installed on both, but they only show the computer they are on. What am I doing wrong?

Install openssh-server so you can talk to each other then install an ftp program, I personally use filezilla. Both are in the synaptic manager

Also need to make sure you have that option enabled in your router.

---

### Post by thomas forbes on 2009-09-04
Ive taken the steps suggested with adding openssh-server and filezilla. Don't know if my router is set right as linksys support doesnt handle linux. Trying to use filezilla router & firewall config wizard. Its been sitting on response:150 opening data connection for some time

---

### Post by mapes12 on 2009-09-05
You have to configure openssh so that the 2 machines can access each other:

1.) Make sure that ssh is installed on both machines. 

```
sudo apt-get install ssh
``` This installs both openssh-server and openssh-client on your machine. Do this on both machines

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
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) To access the other computer
Now, when you want to access a computer from the other, go to Places> connect to server.
- Choose SSH as the service type from the top drop down box

- the server is the IP of the other computer (the one you want to access) so enter the IP address from ifconfig

- the port can be left blank (this means it assumes port 22)

- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username

- the username *must* be specified. This would be the user you use to log into the other computer.

- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your file browser

Click OK
You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

N.B. The first time you connect a warning box may pop up to remind you that keys are going to be exchanged (or something like that). Just OK it.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Personally, I don't use Filezilla. The above configuration is easy enough to access files.

Your router will be OS independent.

Hope this helps.

---

### Post by thomas forbes on 2009-09-05
Thank you, this solved the problem.

---

