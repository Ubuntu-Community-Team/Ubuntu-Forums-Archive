---
title: "Computers not showing in Network &quot;folder&quot;"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by ajdrew06 on 2009-09-13
This question is complicated as I am not familiar enough with the various terminologies to ask it properly, so I appreciate your patience in responding.

I have two computers on a network through a router - both are running Ubuntu 9.04.  I have a file share set up between the two computers using SSH.  I usually connect through a bookmark that opens a SSH server connection through port 22.  However, sometimes I get error messages and can't mount the connection unless I log out & log in one or both computers.

I added the Network icon to the desktops on both computers.  I thought that I could connect more easily to the other computer by double clicking on that computer's icon in the network window.  However, I still run in to trouble.

I noticed that when I double click on the Network icon, I often cannot see one or both computers in the window that pops up.  The following is a scenario that I go though:  When computer A is up & running, I will turn on Computer B.  When I open the network icon on computer B, I see neither computer.  If I log out & log back in again, I can see computer B (the one that I am running) but not computer A, and if I log out & log in again, then I will be able to see both computer A and computer B and the file share will work.  Again, this doesn't happen all the time.  Sometimes both computers will show and I don't have to do the log out & in thing, and sometimes, I only need to log out & log in once. 

I don't understand why my network seems to be so "buggy".  If anyone could shed some light as to anything I may be doing wrong, I would appreciate it.

Thank you!

---

### Post by mapes12 on 2009-09-13
Looks to me as if your router has a delay in configuring machine IP addresses. Are you using static or DHCP IP address assignment?

And are you addressing the the machines in SSH with localhost name or IP address?

---

### Post by isparkes on 2009-09-13
> **ajdrew06 said:**
> I usually connect through a bookmark that opens a SSH server connection through port 22.

I'm not entirely sure what this means - you can do a load of things through SSH, but setting up a file share is certainly not an easy one, and you'd have to have some file sharing layer on top of it, either SAMBA or NFS or some other file sharing protocol.

If you are using Samba (which also allows Windows machines), the "discovery" (finding network elements to show in the list) can take a long time. So make sure that if you are using things this way, that you bring some patience with you.

If I'm barking up the wrong tree, I'd agree with the previous comment, that there's some underlying delay in the transport, and you can discover this most easily with "ping" commands.

So, could you give a little more info about what the SSH configuration is?

---

### Post by mapes12 on 2009-09-13
> but setting up a file share is certainly not an easy one, and you'd have to have some file sharing layer on top of it, either SAMBA or NFS or some other file sharing protocol.

To share files between two Ubu machines is very easy. You do not need Samba or NFS. That's for accessing MS stuff. And you don't even need that if you have the windoze box set up correctly.

All you need to access files across two Ubu machines is SSH configured correctly. IMHO the problem appears to be the router and how SSH is being asked to access the other machine. Once that is resolved then you should be good to go.

BTW, I'm assuming both machines use an ethernet cable to connect to the router i.e. no wifi? Because wifi can cause (occassionally) problems across SSH.

Here's my SSH HowTo I posted for someone else:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```is a meta package and will install both applications

2.) Find out the IP addresses of the computer you want to connect to.

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
- Choose SSH as the at the service type from the drop down list
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

### Post by isparkes on 2009-09-13
OK, with you, wasn't aware of these elements of the GUI. Neat.

Thanks for the info - learn something new every day.

---

### Post by ajdrew06 on 2009-09-13
> **mapes12 said:**
> Looks to me as if your router has a delay in configuring machine IP addresses. Are you using static or DHCP IP address assignment?

And are you addressing the the machines in SSH with localhost name or IP address?

I am using DHCP.  I am connecting through "Connect to server..."

Connection Type: SSH
Server: enter ip address
Port: 22
Folder: ...
Username: ...

Just now, I tried to make this connection, and it said "No route to host" but when I reset my router, I was able to connect.  However, neither computer showed up in my network "folder" before & after the reset.

---

### Post by mapes12 on 2009-09-13
> Just now, I tried to make this connection, and it said "No route to host" but when I reset my router, I was able to connect. However, neither computer showed up in my network "folder" before & after the reset.If you obtained a connection what did you see and how did you know the connection had been made?

---

