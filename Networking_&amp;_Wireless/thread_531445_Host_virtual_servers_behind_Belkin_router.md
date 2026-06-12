---
title: "Host virtual servers behind Belkin router?"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by ububuL on 2007-08-21
I have a Belkin F5D7230-4 router and forward inbound ports 80 (apache httpd) and 22 (secure shell server) to one of my local machine with private IP--192.168.2.100 and private ports 80 and 22. 

Now the problem I am facing is that only port 80 forwarding is working but not port 22. When I port scan my router's public IP--71.141.xxx.xxx, I only see port 80 is open. 

```
$ssh 71.141.xxx.x
ssh: connect to host 71.141.xxx.x port 22: Connection refused
```

Contacted Belkin and they didn't know a thing about what went wrong. Then, I talked to my ISP (sbc dsl), they said the ports shouldn't be open if they were not blocked by my firewall. 

It is kind of frustrating now because I port forwarding two ports the same way and one is working and the other one is not but both the web server and ssh sever can be accessed from local network. 

Any comments or helps will be appreciated. Thanks.

---

### Post by nodows on 2007-08-21
So you're trying let yourself ssh into your home machine from the outside world right?

It might be something as simple as you don't have sshd running or configured properly
and your port isn't open on the local machine.  It may be making it through the router
but being blocked on the machine side.  If your router lets you see traffic in and out
or at least some basic logging abilities you might be able to check it to see if its
getting your connection from the outside world.  If it is, then you need to check
that your machine is in fact running the ssh service on port 22 (and its open).  

Since this is ubuntu you're running unless you went out of your way to install
a firewall or configure iptables I doubt the port is closed if you have sshd running 
properly.  

Hope that helps....

---

### Post by ububuL on 2007-08-21
Yes, I am trying ssh into my home machine from outside.

I had made sure the sshd was running on port 22 by ssh into that machine from another machine with the private IP 192.168.2.4. Also, I checked the sshd_config and the port was set to 22. I don't have any sort of firewall installed besides the one built in with my router.

I checked the firewall log in my router configuration and didn't see any packets coming from my host being blocked. I even turned off the firewall temporarily to see if it would work but no luck.

---

### Post by Austin_KW on 2007-08-21
Can you definitely get in using port 22 on the local network.

Also try forwarding some random port X (external) to internal port 22 and then use ssh -p X, 
Any chance that your router is trapping port 22. If you "telnet routerIPaddress 22" do you get a connected message? EDIT; I mean the internal 192.168 etc router address without forwarding and with forwarding

---

### Post by ububuL on 2007-08-22
Forward random port, say port 92 to private port 22, still can't ssh in
```
$ssh -p 92 71.141.xxx.x
ssh: connect to host 71.141.xxx.x port 92: Connection refused
```

```
$telnet 71.141.xxx.x 22
Trying 71.141.xxx.x...
telnet: Unable to connect to remote host: Connection refused
```

```
$telnet 71.141.xxx.x 80
Trying 71.141.xxx.x...
Connected to 71.141.xxx.x.
Escape character is '^]'.
```
Port forwarding to my httpd web server works okay but it is the only port I had success port forwarding. 

```
$ telnet 192.168.2.100 22
Trying 192.168.2.100...
Connected to 192.168.2.100.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.3p2 Debian-9
```

I have no problem ssh into the 192.168.2.100 (Debian box) from my 192.168.2.3 (Ubuntu box). Don't know why port forwarding didn't work.:confused:

---

### Post by Austin_KW on 2007-08-22
```
ssh: connect to host 71.141.xxx.x port 92: Connection refused
et al.

```

Not sure about your router, but usually the "connection refused" means that something responded and said NO, you are not allowed.

Usually routers are set to stealth ports i.e. Not respond at all. 
Try some random port and see if it is different.
Also try with the ssh box disconnected from the Net and see if the ssh box or the router is making this "refused" response.

/Hope this helps

---

### Post by ububuL on 2007-08-22
I had to call Belkin again to get a replacement unit because there is not much configuration I can do here anymore. Hopefully, the new unit will work as it is supposed to work. Thanks for all the kind help.

---

### Post by jwynharris on 2007-11-04
Hi guys,

Not a unix user really, but having similar troubles with my new Belkin router with a winxp server (192.168.2.100) running apache. 

I need to access HTTPS (443) from the outside world, but need to do this on port 22 say. So thats 22 incoming translated to 443 to my server using the virtual server.

Now interestingly enough, I had until 2 days ago a ADSL belkin router with 802.11g capability. It all worked very well including the virtual servers. Now the range on the wireless didn't reach as far as I needed the the shop very nicely allowed me to upgrade to the MIMO version with bigger range. Setup is slightly different, but now I can't get the virtual servers to work!! It used to on the model down!!!

Also I did some experiments. Old router, I could access the WAN IP from internally and it would use the virtual servers to translate (as if I was on the outside - nice). With the new one, it doesn't work or do this anyhow.

I use SVN over HTTPS. If I set up port 443 incoming to go to port 443 internal, and use a web browser it works. HOWEVER if I use Tortoise SVN (using the same URL and ports) instead of a browser then it does not work and tells me I can't access the server! Remember, it used to work...

I wondering if it problems with the SPI.

Very confussed and somewhat frustrated. Talked to Belkin tech support - didn't have a clue and phone line to India was poor! So not only do you have to deal with a long distance call (I was calling from New Zealand) but also, poor line, accents and insufficient tech knowledge.

If anyone else has similar issues, would be good to know. If you want to know model numbers I can dig them out..

jeremy

---

