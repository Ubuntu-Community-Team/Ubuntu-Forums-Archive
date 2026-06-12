---
title: "connecting my home computers together"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by fi29 on 2010-06-15
I will apologise in advance since this is no doubt something very basic, or in case the information can be readily found somewhere else (I really can't find it).
 
I'm new to linux, and computers in general, and simply want to network together the computers in my house. I have 2 laptops and 1 PC, all of which are running linux/ubuntu, and a switch. I have no internet connection at home, and probably won't for some time. All I want to do is connect them together so that the computers can see each other, can share files, etc.
I've looked everywhere on the internet for how to set this up, but everything I find either assumes you have an internet router, or when I read up on connecting to an ethernet network it merely says something about contacting the network administrator... and I don't have one of those.
When I think about it, it seems like it must be a really easy thing to do, like I should just be able to plug it all in and it works, but I am totally stumped. So, I would be extremely grateful if anyone could offer me some help. 
I guess, firstly, is it possible to connect the computers in this way? And secondly, how would I go about it?
 
Sorry for taking up anyone's time, and thanks in advance.
 
fi

---

### Post by mapes12 on 2010-06-15
I use SSH. If you have no internet then try using aptoncd to install SSH: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

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

### Post by 3rdalbum on 2010-06-15
In Network Manager (right-click the Network Manager applet on your panel, choose Edit Connections...) set up a new wired connection (or edit an existing one) with an IP address on the same subnet. That is, under the IPv4 Settings tab, choose "Manual" and set the IP address on the first computer to "192.168.0.2" and on the second computer to "192.168.0.3" and so on. This way they'll be able to send packets to eachother, because they all have different addresses.

The next step is to install the 'samba' package on the computers that will be hosting files. Fortunately Ubuntu already seems to have the dependencies for the Samba package preinstalled, so just download the package from Synaptic or from [http://packages.ubuntu.com](http://packages.ubuntu.com). Double-click the package to install it.

Now go to System > Help And Support and click on Internet And Networking. Click on "Share files and folders". Follow the instructions there for all computers that will be hosting files, and let us know how it goes.

---

### Post by mapes12 on 2010-06-15
> The next step is to install the 'samba' package on the computers that will be hosting files.You only need Samba for networking MS Windows machines and it's a pain in the butt to configure. If you only have Linux boxes all you need is SSH. You might not even need SSH if right clicking the folder you want to share and the Share Options works for you, but I've never tried that before.

---

### Post by Morbius1 on 2010-06-15
> **mapes12 said:**
> You only need Samba for networking MS Windows machines and it's a pain in the butt to configure. If you only have Linux boxes all you need is SSH. You might not even need SSH if right clicking the folder you want to share and the Share Options works for you, but I've never tried that before.
Excuse the interruption, but just to clarify something. The "right clicking the folder you want to share and the Share Options" is called Nautilus-share. Samba calls it "usershare" and has been part of Samba for years.

You can create a share using Nautilus-share in about 4 seconds. There are some ( many actually ) that have problems with the Samba back-end. Getting the Samba back-end to work ( regardless if they are using Nautilus-share or Classic-share ) can be an ordeal.

If your needs are very simple and you have an all linux network give the utility: **Giver** a shot.

---

### Post by HermanAB on 2010-06-15
Hmm,running windows networking on Linux is a pain in the derrier, however you do it.  Samba requires hundreds of lines of configuration and there are a bazillion things that can go wrong.  In contrast, NFS needs only two lines - one on the server and another on the client computer.

Here is a guide for NFS:
[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

---

### Post by mapes12 on 2010-06-15
Hi Guys

For windoze shares I use PyNeighourhood. I have a HowTo if anyone is remotely interested.

The OP is connecting the machines via a switch so it isn't clear how the private network is assigning private IP addresses to the machines connected to it. "Switch" can mean different things to different people but to assign IP's it must have some kind of DHCP capability otherwise the machines would not be able to see each other?

---

### Post by anewguy on 2010-06-15
To the OP:


You may want to see this link - it pretty well explains it all:

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/")

Dave ;)

---

### Post by mbuotidem on 2010-06-17
so how far? have you been able to create the network? Let us know so that we can help. You are right about thinking that it shouldn't be to difficult to create it.

---

