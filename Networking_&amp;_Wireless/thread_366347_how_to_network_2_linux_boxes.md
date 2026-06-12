---
title: "how to network 2 linux boxes"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by computerjunkie on 2007-02-20
Im posting to ask for the easiest way to network two linux computers together to share the internet connection and files and then (hopefully) eventually my ps3 once I put YDL on it.

here is my basic idea of how to do it but I really dont know:

Using firestarter:
eth0 is my lan connection to the internet
eth1 is the device that is enabled for internet connection sharing

save this config and start the firewall and get it to start at boot (whats the command to do that by the way)

next I would use the wifi radar utility (which right now isnt opening, but I dont have any wireless devices installed, so I'm assuming when I install the PCI wireless card with the appropriate driver wifi radar will work...i hope) to select Ad Hoc mode and as the SSID I would enter "blackdragon" as that is the host name of my laptop.

then I would set the IP to static and set it off by one of my laptop's IP. (if my laptops wireless cards IP was 192.168.1.1 I should set the static of my wireless PCI card in my desktop to 192.168.1.2, right?)

This is (I think) how I can get my desktop to access the internet through my laptop....correct? Or am I missing something and way off? (never networked linux computers before)

if someone could tell me if this is what I should do I'd be most appreciative, or if Im wrong point me in the right direction.

thanx.


P.S. I'm having issues with firestarter. When i select "restrictive by defualt" and then specify the services that I want to allow, after I reboot the computer and then manually execute firestarter those applications are not allowed to access the internet unless I shut down the firewall, but the rules are still there. what gives?

---

### Post by chggr on 2007-02-21
I will tell you what I did to set up my home network.

I have two PCs, a desktop PC and a Laptop. The desktop PC is permanently connected through ADSL line to the Internet and I wanted the laptop to share this internet connection, too. What I did was to install squid ([www.squid-cache.org](www.squid-cache.org)) on the Desktop PC, so that it could act as a proxy server. I set up squid to listen to port 8080 and allow internet access only to the IP 192.168.0.1 (Laptop's IP). Then on the laptop I did the following: System -> Preferences -> Network Proxy -> Manual Proxy configuration and I filled in the Desktop's IP and port 8080. This is all you need to do in order to share the internet connection. Squid is almost plug and play - it took me only 5 minutes to get it to work.

I also wanted to share files between the two PCs. I installed sshd (the ssh daemon) into Desktop and I use ssh to connect from the laptop to the desktop machine. sshd is also almost plug and play and it doesn't need much configuration. Now if I want to connect to the desktop machine using my laptop, I do the following: Places -> Connect to Server -> Service Type: SSH, Server: <the Desktop's IP>, Username <The username I use on the Desktop machine> -> Connect. It then asks for password and immediately performs the connection. Maybe you should install sshd on both machines so that you can connect from the one to the other and vice versa.

Finally I installed firestarted on the Desktop PC and closed all incoming connections except those coming from the Laptop's IP. This way I was able to secure perfectly the computer which is always connected to the internet.

PS: The difference between me and you is that I use cable to connect the two PCs and you prefer using wireless. But I don't expect there will be any differences on the configuration needed.

---

### Post by computerjunkie on 2007-02-21
thank you that was helpful, but I want to be able to use both computers to access the internet and eventually share that connection with my ps3 that will be running Yellow Dog Linux (once they develop the appropriate driver for the wireless card in the ps3)

Basically I want to set up my laptop as a server so that it can access everything on the desktop and the ps3 and so that the ps3 can access anything on either of those computers and so that my desktop can access everything on my ps3 and laptop and use all of those to go online for whatever purpose I'll need the internet for (games and updates for the ps3 and desktop and web browsing and IM and the like for the laptop.)

---

### Post by chggr on 2007-02-21
> **computerjunkie said:**
> thank you that was helpful, but I want to be able to use both computers to access the internet and eventually share that connection with my ps3 that will be running Yellow Dog Linux (once they develop the appropriate driver for the wireless card in the ps3)

With my settings, both computers access the Internet.
I think you can use the same procedure as the one I described in order to achieve what you want.

---

### Post by bryo21 on 2007-03-08
Hi Guys,

Sorry to post here. I know this is on how to network 2 linux boxes but I just need some answers to help me. My problem is on how to network 1 Windows box and 1 Linux box. I tried to create a new thread but no one answers me. Please see this [link]("http://ubuntuforums.org/showthread.php?t=378298&highlight=internet+sharing").

Please help me guys so that I can continue studying Ubuntu. 


Thanks in advance guys. :)

---

