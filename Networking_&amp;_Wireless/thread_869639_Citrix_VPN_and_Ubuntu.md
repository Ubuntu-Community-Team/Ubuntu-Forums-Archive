---
title: "Citrix VPN and Ubuntu"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Jimbro727 on 2008-07-25
Hopefully this is the correct forum for this question..

I'm trying to connect to a Citrix Access Gateway on Ubuntu 7.10.  Upon logging in to the web front-end and clicking "Secure Access Client", the Citrix box redirected me to a page to download "citrixvpn-linux-2.4-i386.sh".  The beginning portion of this file is a shell script, and the rest is a tarball.  The script separates the two, extracts the files from the tarball, compiles a copy of the ip_queue module, and then copies some init scripts.  None of this worked under Ubuntu, but I was able to manually separate the tarball and extract what I believe is all of the files that I should need.  They are:

ip_queue.c
net6vpn
net6vpnd
net6vpnd.fedora.init
net6vpnd.mandrake.init
net6vpnd.redhat.init

Looking at the init scripts, it appears that before starting the daemon (net6vpnd), they do some iptables stuff.  They append the QUEUE target to each chain listed when "iptables -L" is executed.  When the init script is told to stop, it removes the QUEUE targets and then stops the daemon.  

I was new to the ip_queue module, but it appears that it's a fairly simple module that queues up packets for processing by applications in the userspace.

I already had the ip_queue module compiled, and it seems to work fine, and I can add the QUEUE targets without a problem.  I thought that maybe the problem was the included ip_queue source file was some patched version of the ip_queue module, but I think it may just be an older version - it's definitely somewhat different - and I can't get it to compile, gcc complains about just about every included header (number of function parameters, etc.).  Maybe this version was written a long time ago?

The daemon appears to start fine, and I can even connect to the Citrix gateway (and it authenticates me!).  However, none of my traffic appears to be forwarded through the VPN.  I can't see any of the machines that I should be able to.  Looking at the network traffic with wireshark, it appears as though there's alot of TLSv1 communication happening between the citrix box and my machine, but I'm not sure what.  Sometimes my connection to the Internet is uninterrupted, and I can continue hitting websites, etc.  Sometimes it isn't, and I have to stop the daemon and clear those iptables QUEUE rules.  I haven't been able to get consistent results, but it seems that my connection is uninterrupted at LEAST for the first time I attempt to establish a VPN connection using a freshly started daemon.

The only information that I'm getting that point to a problem are ip_rt_bug outputs in dmesg.  I have no idea what that is, and google hasn't been much help, unfortunately.  (I've included some at the bottom)

If anyone has any information regarding this, it would be a huge help.  I really need to get this VPN working.  Even if you don't know anything about Citrix, if anyone could clear up what's supposed to be happening here, maybe I can further troubleshoot.  Thanks!

iptables when I want to establish the VPN:
```
jimbo@jimbo-desktop:~/citrix-playground$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
QUEUE      0    --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
QUEUE      0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
QUEUE      0    --  anywhere             anywhere            

```

Daemon (net6vpnd) started:
```
jimbo@jimbo-desktop:~/citrix-playground$ sudo ./net6vpnd
net6vpnd: net: socket: initializing.
net6vpnd: net: socket: failed to initialize SSL CA certificates.
net6vpnd: ip: initializing.
net6vpnd: ip: tcp: starting.
net6vpnd: ip: starting.
net6vpnd: ip: filter: starting.
net6vpnd: event listener: starting.
net6vpnd: client listener: starting.

```

Client (net6vpn):
```
jimbo@jimbo-desktop:~/citrix-playground$ ./net6vpn --login
The server's certificate is not fully trusted.
Do you wish to continue? [yes|no]: yes
Username: ------
Password: 

```

Daemon (after establishing connection with client):
```

net6vpnd: net: vpn_socket: the server's certificate is not trusted
net6vpnd: vpn: failed to get host check configuration from gateway.
net6vpnd: vpn: failed.
net6vpnd: client handler: the server's certificate is not fully trusted.
net6vpnd: vpn: route [10.0.0.0/255.0.0.0]
net6vpnd: vpn: dns [10.10.1.115]
net6vpnd: vpn: dns [10.10.1.120]
net6vpnd: vpn: dns [10.10.1.13]
net6vpnd: vpn: dns suffix [xxxx.xxx]
net6vpnd: vpn: split dns [off]
net6vpnd: ip: udp: attempting to establish DNS tunnel.
net6vpnd: ip: udp: DNS tunnel established.

```


Here are some of those ip_rt_bug lines.  I'm 192.168.1.127, 192.168.1.1 is my router, and 208.67.222.222 is my secondary DNS (openDNS).  My router is my primary DNS server, which leads me to believe that this output is DNS related:
```
[1053616.702148] ip_rt_bug: 192.168.1.1 -> 192.168.1.127, ?
[1053621.697861] ip_rt_bug: 208.67.222.222 -> 192.168.1.127, ?
[1053626.694138] ip_rt_bug: 192.168.1.1 -> 192.168.1.127, ?
[1053631.689945] ip_rt_bug: 208.67.222.222 -> 192.168.1.127, ?
[1053636.686201] ip_rt_bug: 192.168.1.1 -> 192.168.1.127, ?
[1053641.682505] ip_rt_bug: 208.67.222.222 -> 192.168.1.127, ?
[1053646.678718] ip_rt_bug: 192.168.1.1 -> 192.168.1.127, ?
[1053651.675071] ip_rt_bug: 208.67.222.222 -> 192.168.1.127, ?

```

---

### Post by ahbart on 2009-03-06
Jimbro727,
Did you ever find any answers for this problem? I do not fully understand what you were saying, but it looks like I'm suffering from the same problem.
I can connect to the server and login. But when I click the desktop icon, I just see a Citrix popup connected to ... But nothing comes up after that.
I tried different versions of citrix ica. But no difference.

---

### Post by Conor Gallagher on 2009-03-24
Similar problems here.....brick wall

I have spent the last few hours attempting to get citrix applications setup through an "Application Secure Gateway" without success. In firefox, after I login to the secure gateway (using vpn key, password etc) it hangs on loading the secure application manager stage. The session manager popup window freezes at the loading stage.

I have installed the citrix ICA client and have successfully used it to run Microsoft Outlook over another work network so I don't think this is the problem.

I had thought that this was maybe a Java plugin error (I'm running the AMD64 plugin) but I re-installed java and have tested with Sun's applet.

Any help would be greatly appreciated.

---

### Post by ahbart on 2009-03-24
I've tried 64bit and now a 32bit Ubuntu 8.10 system. Now again with the latest citrix xenapp web client (version 11). I login with password and token code. But when I press the desktop icon which loads the launch.ica file, I get an image of Citrix receiver - connecting to ;40;STA97...
But then nothing happens, till an time out. In the past on Ubuntu Warty ... it worked. But for me it stopped working with Gutsy. It seems to be a specific Ubuntu problem. But why?

Strange thing is that if I open windows xp in Virtualbox, on the same machine, I can login and use Citrix. So it has nothing to do with the broadband modem.

If someone could help us here, that would be great.

---

### Post by alex2399 on 2009-03-24
abhart, do you want to have a remote windows desktop from your organization via the ICA, or is it something else you are trying to do? If the former, it didn't work for me after installing the Linux Citrix client at first. But I do not know the error message anymore, but I still know the solution to my and maybe your problem ;)

There was something wrong with the certificates, I had to download a Thawte certificate and put it in the right place in the ICA folder, after that it functions flawlessly. If I remember correctly, there are logs in the ICA clients directory where you can find out a bit more.

---

### Post by ahbart on 2009-03-24
Thanks for you reply. Yes I need a remote desktop. 
I already installed the certificate from the firm. I do not get an error message. The clients just hangs/waits for something. And it gives up after some time.

---

### Post by Mars73 on 2009-03-27
At our company we use a CAG to allow remote user access to the company network as well and everything works fine in a Windows enviroment but not in my Ubuntu 64bit Ibex (maybe with 32bit as well).
I've installed the Citrix Ica client as seen on the various pages, as well as the certificates but when logging in with password and token I get to the page where you can download a plugin (for Windows) so I choose skip download and then the page with starting session starts. I can see in the URL that the client is Java (and not activex).
And that is where it ends...nothing happens.
I would love to get Ubuntu to connect to my work from home as I then can throw away Windows. It is an essential piece of software/connection I need as I have to work from home sometimes and give support to other users and networks.
Would be awesome if someone could help and/or figure this one out.

---

### Post by ahbart on 2009-03-27
Mars73, There is no launch.ica involved here? When I login and click the desktop I get a launch.ica file. .ica is connecten to the ica client, which is a plugin in firefox. 

If you are offered a java version, then you should have installed sun java plugin. Did you install the 64 bit version with plugin from the sun site? The one in the repository does not have the plugin. Wel last time I looked.

---

### Post by Mars73 on 2009-03-28
When using Windows and clicking on the Desktop then the launch.ica is launched. On Ubuntu I don't get that far. I get to the page when you can download or skip download (the Citrix XenWeb.exe I believe) so when choosing skip it continues. I see in the URL that it uses the Java.
But it stays in the Starting Session screen.
I've compiled the 64bit Java and java -version gives:

marcel@marcel-desktop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) 64-Bit Server VM (build 11.0-b15, mixed mode)

It's weird that it says 1.6.0_10 though as I've compiled the 1.6.0_14 version.
Also opening the Cag site and the following sites are very slow.
I'll do some more checking.

---

### Post by ahbart on 2009-03-28
You don't have to compile a java version on 64 bit ubuntu. Sun has a deb file for this system. that is the 1.6.0-12 version.

It is also possible to install the citrix Xenapp client for linux (the tar.gz version). Even on a 64bit version of ubuntu. But you have to use pluginwrapper and move/link some libs between lib32 and lib.

---

### Post by Patrick Janssen on 2011-04-04
Hello everyone,

I'm new here. Just started with ubuntu this weekend. I stumbled upon this thread because I was looking for a solution to the problem that started this thread. Citrix Secure Acces and how to set it up in Ubuntu. I first started of with a separate boot section for xp and Ubuntu. But that wasn't working for me. If you want to work with Ubuntu, you shouldn't have to set op a dual boot just for one piece of software. So after trying all the options I found on any Ubunti and Citrix search, the following is the solution that works for me: Since Citrix Secure Access doesn't comprehend anything but Windows, we'll have to emulate windows

First I installed ubunti again, got rid of xp (boot) and went on with Ubuntu Softwarecentre, where I got a copy of Virtualbox OSE and installed it. Than I ran it to set up XP. After that I was able to instaal Citrix from cd.

So now I've got myself a computer that starts with Ubuntu, that can run citrix secure acces by using virtualbox ose which in turn runs win xp

Good luck

---

### Post by ahbart on 2011-04-05
Why don't you just install the debian package?
[Link](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1#top)
It's working for me. But one note: I had to disable desktop effects in Gnome on Ubuntu. (A tab at the appearance settings).
Bart

---

### Post by Mars73 on 2011-05-03
What I had to do to make it working, at least opening the Citrix Access site (as that was the first thing that didn't worked) is to add the following line to /etc/sysctl.conf and restart you PC.

net.ipv4.tcp_window_scaling=0

We had the same problem with some Vista and W7 PC's and we had to issue the command netsh tcp autotuning = disabled (something like that) and the window_scaling command is somewhat the same.
I had it working with the Citrix Linux receiver but after a reinstall of my laptop is was too much of a hassle to get it working again so I tried Wine and the Windows version of the Citrix Client and it all installed and works without any problem.

---

