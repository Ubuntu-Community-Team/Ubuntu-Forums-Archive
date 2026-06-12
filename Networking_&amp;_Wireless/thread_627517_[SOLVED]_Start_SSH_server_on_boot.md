---
title: "[SOLVED] Start SSH server on boot"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by IamAcoconut on 2007-11-30
This question concerns Gutsy Server edition. 
I want to make SSH server start on system boot, so I can login from my local network.

Important: I need working SSH daemon to start upon boot **prior to**  configuring Internet connection, which can only be done from remote (physical obstacles).

The issue might seem trivial, but carrying a server box back and forth is not much fun, that's why I'm asking in advance about such a  simple thing.

I will appreciate any input, thanks :)
[B]
ANSWERS[/B]:
[LIST=1]
[*]sshd ('openssh-server') starts on boot by default, when installed.
[*]You can choose to install it during server installation [of Gutsy]. You better do - my apt couldn't detect the system CD after the installation was complete.  
[/LIST]

---

### Post by mellowd on 2007-11-30
SSH should start automatically on boot. At least that is the way it is with my server. I didn't configure anything. All I did was install it and it alwyas runs. Did you do anything to change this default behaviour?

---

### Post by IamAcoconut on 2007-11-30
> **mellowd said:**
> SSH should start automatically on boot. At least that is the way it is with my server. I didn't configure anything. All I did was install it and it alwyas runs. Did you do anything to change this default behaviour?

Do you mean ssh **server** (called sshd)], not the actual 'ssh' process? Are you able to log in from remote without physically accessing the computer? With or without autologging on?
Does that mean, that an Ubuntu Server box allows all incoming ssh connections just after it's installation (as the firewall is - by default - off/permissive, isn't it)?

---

### Post by mellowd on 2007-11-30
It's the daemon.

I chose to install it when I installed ubuntu server but you can add it at any time.

And yes, I use it to administer my server box from anywhere. It's a headless box and I never touch it. From home I'll use putty to log onto the box and from work I'll do the same except I'll vpn in first.

---

### Post by daengbo on 2007-11-30
Sorry that I'm really confused. What do you mean by remotely administrating a server before the Internet connection is configured? You'll need the connection to administer.

---

### Post by IamAcoconut on 2007-11-30
> **daengbo said:**
> Sorry that I'm really confused. What do you mean by remotely administrating a server before the Internet connection is configured? You'll need the connection to administer.
Maybe via LAN. But when using ssh you have to refer to a particular IP address. Or did you set it manually during the install process, mellowd?

---

### Post by psusi on 2007-11-30
You aren't making any sense... if the network is not yet configured, then there isn't anything for sshd to listen for connections on, which is why it doesn't start up until after the network interfaces are started.

---

### Post by IamAcoconut on 2007-11-30
> **psusi said:**
> You aren't making any sense... if the network is not yet configured, then there isn't anything for sshd to listen for connections on, which is why it doesn't start up until after the network interfaces are started.
You talkin' to me? ;) Or Mellowd?
I can assign IP addresses to interfaces that will connect to PCs in my LAN. Than SSH via one of those interfaces. THEN mess with the 'external' interface for internet connection. The trick is, I'll have to turn off the computer and boot it again without physical access before conducting the last operation.

---

### Post by googlah on 2007-11-30
sshd should be started at boot. Atleast what mine does too.. I just needed to apt-get the package "openssh-server" and it's always on as fast as I turn on the computer.

---

### Post by IamAcoconut on 2007-11-30
> **googlah said:**
>  I just needed to apt-get the package "openssh-server"(...)In order to do what? I won't be able to do that, unless the package is on the CD.

---

### Post by mellowd on 2007-11-30
It's on the CD.

My server has only 1 network interface. That being the lan interface. That goes to a firewall then goes out on the net. I'll ssh in either via the lan or via the net and it'll come in on the same interface

---

### Post by IamAcoconut on 2007-11-30
**Mellowd**, how does your server obtain it's very first IP. Do you have a DHCP on your firewall. I've got none. The box concerned IS my firewall/router.

---

### Post by mellowd on 2007-11-30
I'm a bit confused as to what your setup is and also what exactly it is you are trying to do. Could you go a little more in depth?

My firewall has dhcp but my servers ip is static

---

### Post by IamAcoconut on 2007-12-01
> **mellowd said:**
> I'm a bit confused as to what your setup is and also what exactly it is you are trying to do. Could you go a little more in depth?Nonexistent yet. I'm going to install Gutsy Server tonight [CET]. Just wanna avoid dragging the server box back and forth, hence all this fuss.

> **mellowd said:**
> My firewall has dhcp but my servers ip is static Did you set the static IP during the installation, or when/how? As it's only possible to login remotely after the IP is set.

---

### Post by mellowd on 2007-12-01
> **IamAcoconut said:**
> Nonexistent yet. I'm going to install Gutsy Server tonight [CET]. Just wanna avoid dragging the server box back and forth, hence all this fuss.

 Did you set the static IP during the installation, or when/how? As it's only possible to login remotely after the IP is set.

I didn't configure it on the server, I configured it on the firewall to give a static address based on the MAC address.

---

### Post by mellowd on 2007-12-01
> **IamAcoconut said:**
> Nonexistent yet. I'm going to install Gutsy Server tonight [CET]. Just wanna avoid dragging the server box back and forth, hence all this fuss.

 Did you set the static IP during the installation, or when/how? As it's only possible to login remotely after the IP is set.

Come to think of it, it looks like you want to SSH in while you are installing it? That's not possible. While installing I had to move my keyboard and screen to the server. It's a mission but once it's done it's done. You only ever need that while installing it.

The only way to get around this is if you have something like iLo which comes on HP servers. I don't think you'll have that setup at home though.

---

### Post by IamAcoconut on 2007-12-01
Negative, **mellowd**.
I already said: I wanna SSH after performing the normal installation. But if something goes wrong, I'll have to install and configure the previous OS again just to be able to [connect to the Net and] ask for help, then drag the box to it's place, than drag it back here and try again, hence sooo maaany dumb questions. 'Cos it serves me as a router.

Ok, I'm getting to work now.

---

