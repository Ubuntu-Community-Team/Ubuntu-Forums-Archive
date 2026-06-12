---
title: "VNC problems"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by ZootHornRollo on 2008-08-06
Hi,

i have a machine set up as a headless audio player connected to my hifi.

I normally use VNC to connect to it and control it but i am getting an error.

```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

Any ideas what i can do resolve this without connecting up a monitor?

I have no way to reboot without holding the power button in for 5 secs.

---

### Post by ZootHornRollo on 2008-08-06
The IP address is right as it shows up on my router as an attached device and i can ping it.

---

### Post by ZootHornRollo on 2008-08-06
i cannot ping the vnc port (5900).  i get this message.

```
ping: unknown host 192.168.0.3:5900
```

---

### Post by superprash2003 on 2008-08-06
try accessing via hostname instead of ip, could be that the ip 192.168.0.3 of the machine has changed..

---

### Post by scorp123 on 2008-08-06
> **ZootHornRollo said:**
> i cannot ping the vnc port (5900) Of course not. "Ping" always uses the same port: 7 (icmp). You cannot "ping" ports, only hosts. If you want to check what ports are open on a remote machine you should use port-scanning tools such as "nmap" ... you will find this tool in the repositories (e.g. via Synaptic) and plenty of tutorials via Google. And don't you ever "nmap" foreign IP addresses!! Some people might interpret that network scan as an attack ("nmap" is one of those tools which is used by "both sides", good and bad!) so you please make sure you only use "nmap" against your own computers, OK?

If "vncviewer" says it cannot connect then it's most likely that either the IP address of the host has changed or that the VNC server running there has crashed for some reason (this can happen) and isn't there any longer.

So you should check:

- can you ping that PC and are you 100% sure that the IP address is correct?
- what does "nmap" say which ports are remotely open or not open?

If 5900 is closed then the VNC server has died for some reason and you should "ssh" into your remote PC and start it again.

---

### Post by ZootHornRollo on 2008-08-06
many thanks for a very informative reply.

i will give it a go tomorrow morning.

cheers.

---

### Post by xc3ll on 2008-08-06
Try ssh'ing into the box and make sure vncserver is running.

Do a 
$ps aux | grep vncserver

If vncserver is running, it'll show up.

---

### Post by ZootHornRollo on 2008-08-06
after a bit of googling i have discovered that i must have SSH client on this machine (installed on default installation) but do not have ssh-server on my audio machine as i have never knowingly added it.

I have never used it.

I only got the machine set up properly a few days ago and was planning just to use vnc to control it.  i have been testing the vnc/wifi connection for over a month with no problems so i took the monitor away this morning after backing up all the audio files on the HD to DVD. Just typical that it was today i encountered the first issue regarding remote controlling it only hours after taking away the monitor!! 

I'll need to get the monitor out again (big 19" CRT monster!!!) and install ssh and then learn all about that!!!

should i install the blacklist too?

---

### Post by xc3ll on 2008-08-06
Installing ssh server is super easy, although there's a few steps you should take to keep it secure.  Here's a guide on getting ssh up and running:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

Along with a guide on ssh keys:

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

If you set up ssh correctly and have a good strong password (big like Pepsi can), you shouldn't have to worry about using a blacklist.

In case you have no idea what SSH is, its pretty much an application that will give you a secure remote terminal.  As long as you can ssh into a box, you can pretty much solve any problems that you might be experiencing.  It will also allow you to secure VNC (which I also highly suggest. You can either port forward or use the -via option in vncviewer)

---

### Post by ZootHornRollo on 2008-08-08
> **xc3ll said:**
> Try ssh'ing into the box and make sure vncserver is running.

Do a 
$ps aux | grep vncserver

If vncserver is running, it'll show up.

i have installed SSH server but still can't really make much use of it.

how do i run the above command?  do i run it on the server or on the client?

---

### Post by ZootHornRollo on 2008-08-08
> **ZootHornRollo said:**
> i have installed SSH server but still can't really make much use of it.

how do i run the above command?  do i run it on the server or on the client?

got it!  :o

---

### Post by ZootHornRollo on 2008-08-10
when trying to do anything over vnc or ssh i have to use the IP address (which changes if i reset my router) as the hostname is not recognised from either system.

is there a setting somewhere to make it work?

> graham@graham-desktop:~$ vncviewer MusicBox:0
Couldn't convert 'MusicBox' to host address

---

### Post by gigaferz on 2008-08-11
log in to your router set up web page, and figure out a way to make your Internal ip address static,

---

### Post by ZootHornRollo on 2008-08-11
I managed to work out how to do that after posting that so one problem solved.

but it does not solve the hostname issue.  any idea's how to get the hostnames to work?

---

### Post by xc3ll on 2008-08-11
There's a few ways to kinda do what you want.  First requires you ssh tunnel your VNC connection, and is really easy to set up. The second way will do what you want, but not quite.  

1st Way:  

Do the thing with the router that giga said. (What you really wanna do is reserve a ip for the mac address of the NIC on your server. You can figure out it's NIC by typing 'ifconfig'. Its the number in the form of xx:xx:xx:xx:xx:xx next to HWAddr. Most routers allow this, and it sounds like you have this set up).

Next, go to your ~/.ssh folder, and use your text editor to change/create a file named config (full path should be ~/.ssh/config ).  Make/add an entry in this form:

host MusicBox
        Hostname *<ip address>*
        User *<your username>*

After that, create an ssh tunnel to your musicbox,by using this command:

ssh - N -L 5900:localhost:5900 MusicBox

and then in a seperate terminal:

vncviewer localhost:0

This is the best way, since it'll also encrypt your VNC traffic, but if you're not concerned with anyone sniffing your packets over WiFi, then its not necessary.


You can also accomplish the same thing using DynDNS. They'll give you a free DNS name (something like musicbox.ath.cd I think). And then, you can tell your router to route traffic from that address to your musicbox(most routers have this capability), or you can install a app on your musicbox that will update dyndns's servers, and then port forward on your router.

that will allow you to do this:

vncviewer musicbox.ath.cd:0

This will allow you to run vnc from anywhere in the world, but I wouldn't suggest it, since your VNC traffic will be unencrypted.

If you do want this capability tho, you can use both of the methods I suggested in conjuction, ssh'ing to your new domain, and then pointing vncviewer to the localhost.

Hope this helps.  I might have gotten the ssh command wrong. If it doesn't work, lemme know.

---

