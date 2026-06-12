---
title: "Basic samba knowledge..."
date: 2009-09-19
forum: New to Ubuntu
---

### Post by OllieGab on 2009-09-19
Help! Some basic samba knowledge, please.
I've configured samba in Ubuntu 9.04 the way I **think** it should work.
I've got two other distros on a laptop (wireless), which, when I try to access the folder I've given share access to, give me an error message like:

"Could access all contents on server..."

I also get:
"'net usershare' returned error 255: net usershare add: failed to add share test. Error was Operation not permitted"

when I try to give a folder on the server machine sharing properties. Though, I have had that folder in sharing mode earlier (the hand under the folder!)

So I think the problem is with Ubuntu rather than the 'clients'.
Do the client machines need to have any additional software installed? I mean, apart from the "normal" standard applications?

---

### Post by mapes12 on 2009-09-19
Are there any windoze machines in your network or do you just have Ubu/Linux machines that you are trying to connect and share files/resources with?

---

### Post by OllieGab on 2009-09-19
There's one Linux machine and one Mac - which also can't "see" anything!

---

### Post by mapes12 on 2009-09-19
You don't need to go through all the Samba configuration hassle to connect Ubu and Mac boxes. Install SSH and it's a breeze. For the Mac go here for the guides on HowTo SSH with a MAC:

[http://www.google.co.uk/#hl=en&source=hp&q=osx+ssh&btnG=Google+Search&meta=&aq=f&oq=osx+ssh&fp=1&cad=b](http://www.google.co.uk/#hl=en&source=hp&q=osx+ssh&btnG=Google+Search&meta=&aq=f&oq=osx+ssh&fp=1&cad=b)

For the UBU machines it goes like this for me:

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

### Post by OllieGab on 2009-09-19
Yes, thanks! That worked fine. I already had the required applications on both machines. Also, turning off the firewall on the main machine (I'll configure later to allow SSH) seems to have made a difference...

I've haven't checked out the Mac link yet but as that machine belongs to my son I'll let him struggle with that;-)

Thanks a lot!

---

