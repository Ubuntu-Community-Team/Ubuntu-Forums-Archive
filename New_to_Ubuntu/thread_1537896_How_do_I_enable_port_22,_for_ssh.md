---
title: "How do I enable port 22, for ssh?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-07-24
I have installed ssh on my new laptop and cannot ssh files off its drive (I have a local wireless network) I am using Ubuntu 10.4

help would be great.

Mick

---

### Post by mapes12 on 2010-07-24
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

### Post by Mick8882003 on 2010-07-24
So I dont have to explicitly open the port: if i do:

```
mickpc@mickpc-desktop:~$ nmap -p 22 192.168.0.*

Starting Nmap 5.00 ( http://nmap.org ) at 2010-07-24 22:40 EST
Interesting ports on mygateway1.ar7 (192.168.0.1):
PORT   STATE SERVICE
22/tcp open  ssh

Interesting ports on 192.168.0.2:
PORT   STATE SERVICE
22/tcp open  ssh

Interesting ports on 192.168.0.50:
PORT   STATE  SERVICE
22/tcp closed ssh

Nmap done: 256 IP addresses (3 hosts up) scanned in 15.52 seconds
mickpc@mickpc-desktop:~$ 

```

on another machine i see that the port is closed...

Mick

---

### Post by mapes12 on 2010-07-24
Did you install the ssh meta package on the machine reporting the closed port? By default ssh uses/opens port 22.

---

### Post by Mick8882003 on 2010-07-24
I just uninstalled/reinstalled it and it is still closed and I cannot connect.

Mick

---

### Post by mapes12 on 2010-07-24
Try entering it in the ssh configuration GUI:-

Places>Connect to Server>Service type [ssh]>Port [22]

as well as the other entries in my first post.

EDIT - It might be how your network is configured: [http://ubuntuforums.org/showthread.php?t=800475](http://ubuntuforums.org/showthread.php?t=800475)

---

### Post by bodhi.zazen on 2010-07-24
> **Mick8882003 said:**
> I just uninstalled/reinstalled it and it is still closed and I cannot connect.

Mick

My guess would be that you are running a firewall.

If so, what did you use to configure iptables ? ufw ?

---

### Post by YesWeCan on 2010-07-24
Is your laptop 192.168.0.50?
Ubuntu installs with all ports open by default so have you made a firewall yourself? If so, you need to tell the firewall to allow port 22. Would you post the settings here: sudo iptables-save

---

### Post by YesWeCan on 2010-07-24
Sorry bodhi.zazen I didn't realize you had beaten me to it. :p

---

### Post by da burger on 2010-07-24
> **YesWeCan said:**
> Is your laptop 192.168.0.50?
**Ubuntu installs with all ports open by default** so have you made a firewall yourself? If so, you need to tell the firewall to allow port 22. Would you post the settings here: sudo iptables-save

I could be mistaken but I'm pretty sure that's the exact opposite of the truth. Ubuntu installs with every port closed for security reasons.

---

### Post by CharlesA on 2010-07-24
> **da burger said:**
> I could be mistaken but I'm pretty sure that's the exact opposite of the truth. Ubuntu installs with every port closed for security reasons.

No, there is no firewall enabled by default, but there are no services listening by default.

My bet is that a firewall is enabled and port 22 is not open.

---

### Post by bodhi.zazen on 2010-07-24
> **da burger said:**
> I could be mistaken but I'm pretty sure that's the exact opposite of the truth. Ubuntu installs with every port closed for security reasons.

> **CharlesA said:**
> No, there is no firewall enabled by default, but there are no services listening by default.

My bet is that a firewall is enabled and port 22 is not open.

You are both correct.

By default there are no listening services , so all the ports are closed.

By default iptables is permissive and allows all traffic.

So, by default, if you then install ssh , port 22 will then be open and iptables will not block the traffic.

If openssh server is installed, and the port is closed, that implies iptables has been configured to block incoming traffic.

---

