---
title: "Is there a way to share files...?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-10-24
Is there a way to share files on a network like Windows does? I really don't want to have to ask someone what their ip address is every time I want to share a file, or vice versa. I would like to just click on, may be network or something, and have it automatically find the other computers that have shared folders on the network.

Edit - I should have said we were also on the same LAN

---

### Post by CharlesA on 2009-10-24
You can setup a samba server on that machine. That'll let you share between windows boxes.

---

### Post by clive littlewood on 2009-10-24
Hi

If all machines are Linux try "Giver" in the repos.

Install on all boxes and share away !!

see my blog for more details.

Clive

---

### Post by saki-roll on 2009-10-24
easy way to do this on Ubuntu is to go to terminal and type _sudo apt-get samba_ this will give you samba support to share folders to windows, otherwise from linux to linux its easy, one problem you might have though is if you've installed any firewall programs it might not let it go through unless you specify that the port windows uses is open, port... 445 and 135-139, thats IF you have a firewall like firestarter active, hope this helps

---

### Post by philinux on 2009-10-24
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Only needed if some of the boxes on the net are windows.

---

### Post by slughappy1 on 2009-10-25
I guess it was my fault that I made my question a little vague. I wanted to share files between two Linux computers on the same LAN. It sounds like Giver is exactly what I wanted to know. I knew about it but was hoping that there was something newer. I wasn't sure how well Giver would work since it hasn't been updated since August 2007.

---

### Post by cclee on 2009-10-25
Nfs?

---

### Post by mapes12 on 2009-10-25
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

### Post by mike555 on 2009-10-25
OR you could just use "DropBox " and put the files you want to share on it ......... the added advantage is also being able to get those files from any computer by going to their site .........

---

### Post by vinutux on 2009-10-25
> **mike555 said:**
> OR you could just use "DropBox " and put the files you want to share on it ......... the added advantage is also being able to get those files from any computer by going to their site .........

Y dropbox What about ubuntu one ?

---

