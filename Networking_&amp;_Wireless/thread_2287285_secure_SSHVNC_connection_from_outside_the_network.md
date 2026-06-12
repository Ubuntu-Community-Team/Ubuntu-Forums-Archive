---
title: "secure SSH/VNC connection from outside the network"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by qubix2 on 2015-07-18
Hi everyone, 

I have installed Ubuntu Mate 15.04 on my raspberry pi 2 and I was playing around with ssh, vnc, got it to work from my laptop, but only through local ip (192...). However, my router assigns the same public ip to every computer/tablet/etc. connected to it. How can I make just my pi visible on the internet, and not the rest of the devices? 
Also how can I make this connection secure? 

Sorry if my question is a bit naive, but I am new to all this networking stuff and I want to learn as much as possible from it. :)

---

### Post by Lars Noodén on 2015-07-18
As it stands, the secure way to deal with VNC is over SSH.  So you'll have to set up tunneling over SSH first and the first part of that is working with SSH.  Since you're going to be making SSH available over the Internet, you'll probably want to enable [key-based authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) and disable regular passwords.  

Once that is working, you'll need to have your router forward an external port to port 22 on your target machine.  The details vary from brand to brand and model to model, but there should be a menu that allows you to set up forwarding.  Also, if you haven't done it already, set your router so that it always gives your target machine the same IP address.  Again, that should be one of the options hidden away in your router's menus.  You'll know that is all working when you can, from outside your LAN, connect with SSH to the designated port on your router and it goes through to SSH on your target machine.  e.g. for port 2222

```

ssh -p 2222 *xx.yy.zz.aa*

```

Then you can look at tunneling.  

```

ssh -p 2222 -L 5901:localhost:5901 *xx.yy.zz.aa*

```

That would be for VNC display :1 and you would connect to it at "localhost" or "127.0.0.1" from the machine on which you typed in "ssh ..." to make the tunnel.

---

### Post by qubix2 on 2015-07-18
Hi Lars, thanks for your reply. 

Thing is I try to do the Port Forwarding part. I enter my router's settings menu, it actually has a submenu "Forwarding". There I can add a list with :

** Public Port Range ------ Target IP Address -------- Target Port Range ----------- Protocol ----------- **

For protocol I only have 3 options ( TCP, UDP, both). There is no SSH. 

I tried something like

```
 22 ----- 19X.XXX.XX.XX --------- 22 ------------ both 
```

where the local IP is the IP of my Pi. 

Then I do the 

```
 ssh -p 22 8x.xxx.xxx.xx 
```

where 8x... is my public ip (it's a dynamic ip, but I think it should work for short periods of time).

I left port 22 for both Pi and router just for testing purposes. The result I get is connection timed out.

---

### Post by weatherman2 on 2015-07-18
You also must install the ssh server in Ubuntu.

```

sudo apt-get update
sudo apt-get install ssh

```

First try ssh on your local network with your local IP to make sure you can ssh into the Ubuntu box.  Then try it from outside.  Please note that ssh login by password is enabled by default, DANGEROUS if you allow that from outside.  It's important to have a really strong password on your Ubuntu box - but disabling password login and using certificate login instead is highly recommended.

Note that you will also need to install a VNC server in Ubuntu and then start it after you have initiated the ssh fro outside.  Do a web search for "VNC over ssh" for more info, though the recipes you will find will vary from distro to distro and may not work the same everywhere.  I've never spent much time with this approach but never gotten it to work with some brief experiments.

What I did instead is install OpenVPN on home router.  Then I make a VPN connection into my home router from wherever, then I can VNC to anything on my network with its local IP (or local name).  But not every router can do OpenVPN.  If you have a router that supports TomatoUSB or DD-WRT firmware, this might be an option for you.

You may also need to worry about your external IP changing, if it is not a static IP.  In that case, look into dynamic DNS.

---

