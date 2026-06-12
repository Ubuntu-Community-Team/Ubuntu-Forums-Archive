---
title: "Port Forwarding For Absolute Beginner"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by noodlemctwoodle on 2010-06-17
Good Day to All ):P
 
Well i have just installed Ubuntu 10.04, come over to Linux from windows and i must say it kicks *** compared to windows.. 
 
However im really struggling with the IP tables and port forwarding to setup VNC remote desktop and HTTPS sabnzb
 
Can anyone give me or point me in the right direction to setup port forwding in terminal or is there a GUI that i can install to do this??
 
Many Thanks

---

### Post by Breambutt on 2010-06-17
```
sudo apt-get install gufw
```
It's a simple GUI for a simplified command line firewall that uses iptables rules. Main menu entry installs in System > Admin > Firewall.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by noodlemctwoodle on 2010-06-17
> **Breambutt said:**
> ```
sudo apt-get install gufw
```
It's a simple GUI for a simplified command line firewall that uses iptables rules. Main menu entry installs in System > Admin > Firewall.
 
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
 
 
Thats awesome, i'll give that a go when i get home from work :wink:
 
Many Thanks

---

### Post by 3rdalbum on 2010-06-17
> **Breambutt said:**
> ```
sudo apt-get install gufw
```
It's a simple GUI for a simplified command line firewall that uses iptables rules. Main menu entry installs in System > Admin > Firewall.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Disregard that. Breambutt, the OP wants to forward ports from their router to their computer, not close ports on their computer.

Noodle, the first step is to set your computer to use a static IP. Let's see if I can describe this fully to you. Right-click on your Network Manager applet and choose Connection Information. It will tell you the address of your "default route", which is your router. You need to choose an IP address for your computer that is on the same subnet as the router; this means that only the LAST NUMBER differs (for instance, if your default route is 192.168.0.1, you can choose 192.168.0.2 up to 192.168.0.255 as your computer's IP address).

Also take note of your Primary and Secondary DNS.

Right-click on Network Manager again and choose Edit Connections. Go to Wired or Wireless (depending on what you use) and edit the existing connection there. Go to Ipv4 Settings and choose Manual as the method, then input your chosen IP address, gateway (the "default route" address) and the primary and secondary DNS with a comma in between them. The Subnet Mask should be 255.255.255.0.

Save this, then disconnect and reconnect. As far as your router is concerned, you now have a static IP address, so it will always know which computer is yours.

Now visit your router's configuration panel; this is basically "http://" plus your default route address. The username and password are usually "admin" and "admin" unless you have changed it. Go to the Port Forwarding section of your router and use it to forward TCP or UDP port numbers to your chosen IP address. Every router is different.

While you're in your router's configuration panel, make sure UPnP is turned on. Some programs will then be able to automatically port forward, although this is usually restricted to Bittorrent clients and VNC servers and I doubt your web server will be UPnP aware.

Okay, that should be it. Make sure you have used the "Apply" or "Save Changes" button in your router! Your router might need to be rebooted too, or it might do this automatically.

---

### Post by mapes12 on 2010-06-17
Not sure if this is what you're looking for but I used the free domain and tools from dyndns.com:- [http://www.dyndns.com/support/kb/dyndns.html](http://www.dyndns.com/support/kb/dyndns.html)

This helped me configure my Dad's machine (in another town) so that I could access it remotely to help him out from time to time.

Mark

---

### Post by Breambutt on 2010-06-17
Oh boy, not again.

I already dumped this thread before posting anything, something just seemed out of place with "absolute beginner to Linux" and not using the router's browser-based interface. That's how it's done in Windows too, right? What am _I_ missing here? I've never had to configure any of those things to make it budge, don't all routers have the ability to reserve IPs in a static manner based on MAC address and whatnot? ;o

---

### Post by noodlemctwoodle on 2010-06-17
[[SIZE=5][COLOR=#000000]3rdalbum[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=61044") 
 
Thanks for your post but i have already set all that up, that was the easy part. i have setup all the port forwards on my router & UPnP is enabled. DDWRT makes that very easy ;)
 
The thing is when i connect to my Linux box through VNC the connection is very slow as if the Ubuntu firewall is blocking my every move and i read that you can configure ports & port forwarding in the IP tables. However I was unaware of an easy way of doing this, I will definately give BreamButts method a try. 
 
Also i need to open port 9000 for SabNZB so i can use HTTPS connection over the LAN as it seems Ubuntu is blocking it as i cannot access SabNZB server from my windows XP Virtual on the same LAN.
 
Many Thanks

---

### Post by noodlemctwoodle on 2010-06-17
> **mapes12 said:**
> Not sure if this is what you're looking for but I used the free domain and tools from dyndns.com:- [http://www.dyndns.com/support/kb/dyndns.html](http://www.dyndns.com/support/kb/dyndns.html)
 
This helped me configure my Dad's machine (in another town) so that I could access it remotely to help him out from time to time.
 
Mark
 
 
Thanks for your advice, i already have a dyn-dns account for RDP to my windows virtual, but will be using it for Ubuntu once i work out how to configure the ports in Ubuntu...

---

### Post by Irony on 2010-06-17
> **noodlemctwoodle said:**
> once i work out how to configure the ports in Ubuntu...
By default all the ports in ubuntu are open. Port forwarding is done at your router (see [http://portforward.com/](http://portforward.com/) ).

---

### Post by noodlemctwoodle on 2010-06-17
> **Irony said:**
> By default all the ports in ubuntu are open. Port forwarding is done at your router (see [http://portforward.com/](http://portforward.com/) ).
 
I havent changed any of the port forwards on my router after moving over from windows, where both RDP and VNC worked flawlessly using either static external IP or Dyn-DNS address.
 
However now moved over to Ubuntu manually set my internal IP to 192.168.1.20, which is the same as my previous windows install and where all my ports are forwarded to but now nothing works... So by power of deduction i figured Ubuntu must be blocking it somehow..???
 
I have installed VNC in Ubuntu and it works internally via my iphone, and from my virtual XP box. but as soon as you try and connect via external connection it falls over. You can view the Ubuntu desktop but you cannot do anything else, once the screen is being viewed.
 
SabNZB over LAN just doesn't work at all i have opened the correct port on my router and forwarded to the IP of my Ubuntu box but still no go as if some thing else is blocking it. However worked fine under Windows XP.
 
 
So any ideas??

---

### Post by beckols on 2010-06-17
I think you can safely assume that you aren't looking for a solution in the firewall area.  Since it works fine internally but not externally, I would check out some DDWRT settings (although I'm not sure what could be causing it, big help, I know =) ).

---

### Post by Irony on 2010-06-17
> **noodlemctwoodle said:**
> I have installed VNC in Ubuntu and it works internally via my iphone, and from my virtual XP box. but as soon as you try and connect via external connection it falls over. You can view the Ubuntu desktop but you cannot do anything else, once the screen is being viewed.
In Karmic I found Vinagre to be buggy and a lot of the time it didn't bother connecting I ended up using xtighvncviewer which is installable from synaptic and used from the command line like this;

```
vncviewer -encodings 'tight' localhost:5900
```

Replace localhost:5900 with whatever you are using, e.g. an ip address.

I find that in Lucid that Vinagre works but I prefer using xtighvncviewer because it is faster and clearer. However xtighvncviewer won't resize the screen to fit your screen so moving it back and forth is necessary.

---

### Post by yeremiya on 2010-06-24
> **noodlemctwoodle said:**
> I havent changed any of the port forwards on my router after moving over from windows, where both RDP and VNC worked flawlessly using either static external IP or Dyn-DNS address.
 
However now moved over to Ubuntu manually set my internal IP to 192.168.1.20, which is the same as my previous windows install and where all my ports are forwarded to but now nothing works... So by power of deduction i figured Ubuntu must be blocking it somehow..???

I have the same situation as you. The internal IP is the same as in Windows, the router is set to forward certain ports at that IP, but I can't seem to be "visible" from the internet.

I tried to forward incoming connections (I do this because of torrents, I want incoming connections in Transmission, I've set the incoming connections port in preferences) and then checking via various online services such as [http://www.canyouseeme.org/](http://www.canyouseeme.org/), but I can't seem to "see" myself from there.

Any ideas on how I might resolve this?

EDIT: Solved! Looks like I made a mess myself: the port I chose was already in use by something else. I tend to use low (300-10000) ports, and, with my luck, I hit the one that I couldn't use. Now, after chosing my port from 30k - 35k range - it's all a-ok!

---

