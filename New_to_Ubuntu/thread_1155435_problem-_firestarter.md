---
title: "problem- firestarter"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by mojolobo on 2009-05-10
hello everyone , nice to be here

I have just install Firestarter firewall. some users say it is needed. other say it is not.
From what ive read the firewall is built in the kernel and is activated on startup.
My questions are 
what is the purpose of firestarter? 
how do i know if my Firewall is active , on startup.

also, 
i use deluge bit torrent client , ive enabled the block list , type peerguardian. when i run firestarter during download , my cpu spikes to 100%. Just what is going on ?

some advice would be much appriciated . thanks

---

### Post by Redache on 2009-05-10
> 
I have just install Firestarter firewall. some users say it is needed. other say it is not.
From what ive read the firewall is built in the kernel and is activated on startup.
My questions are 
what is the purpose of firestarter? 
how do i know if my Firewall is active , on startup.


Firestarter is a Graphical Frontend for IPtables, which is the Firewall that is built into the Linux Kernel. Technically it's always running as its integrated into the Kernel. Firestarter enables you to control the Firewall Rules and how high the protection level is.

As for your Deluge Problem, does it spike to 100% throughout the entirety of the download or does it do it when you activate a download and then drops down to normal?.

---

### Post by lovinglinux on 2009-05-11
> **mojolobo said:**
> what is the purpose of firestarter? 

Create firewall rules for iptables.

> **mojolobo said:**
> how do i know if my Firewall is active, on startup.

```
sudo iptables -L
```

If is not activated, then the output of the command above will be short and include only "ALLOW" rules.


> **mojolobo said:**
> i use deluge bit torrent client , ive enabled the block list , type peerguardian. when i run firestarter during download , my cpu spikes to 100%. Just what is going on ?

You don't need and you shouldn't use Firestarter all the time. Since it is just a firewall manager, once you configure the rules you can close Firestarter GUI. Iptables, which is the real firewall, will still work on the background. Running Firestater all the time might be a security risk, since it needs root permissions.

Firestarter is not even recommended anymore. Ubuntu currently comes with UFW (Uncomplicated Firewall), that you can control using GUFW. To install it, go to Addd/Remove manager and search for "gufw" and install the package named "Firewall Configuration".

---

### Post by mojolobo on 2009-05-11
thanks Redache , lovinglinux
cpu usage spike during a download , when the list in "events" builds up.

i have more questions
1.should i configure iptables in firestater, of just leave is as it is since im a beginner. 

2.how does firewall in linux , differ from something i would use in windows like Comado or Zonealarm.

i have disabled my boot screen so i can view loading on bootup. everything is ok , loading firestarter firewall:fail
3. since i dont need firestarter this should not be a problem ? right?

thanks
[B]
[/B]

---

### Post by lovinglinux on 2009-05-11
> **mojolobo said:**
> i have more questions
1.should i configure iptables in firestater, of just leave is as it is since im a beginner. 

Lots of people will argue that you don't even need a firewall, because Ubuntu doesn't have any open ports by default. No services listen to any port. Additionally, if you are behind a router, then it will be your first line of defense, which should be enough. Let's say you don't have a router and don't use the firewall, then anyone will be able to reach you any time they want, but since you don't have listening services, the connection will be refused. Which is the same as saying the port is closed. You are secure.

If you need to open a port for a service (like a torrent client for example), then you need to allow people to connect, so the firewall shouldn't block the port and thus shouldn't be needed. But if I have a service listening to an open port, then someone might hack into my system? It is possible, but only if the program listening to that port has exploitable security flaws. A firewall won't help you with that, since you need to allow people to connect to your service, otherwise you won't be able to use the program.

Most former Windows users (including me) are paranoid about firewalls, because Windows has a lot of services listen to ports you don't even know about and, due to flaws in the system, they are a real threat. For example, Windows comes with remote desktop enabled and loaded automatically on boot. Additionally, third-party Windows program tend to phone home without your knowledge, virus can use the net to download more malicious stuff and so on. Most programs you use on Ubuntu are from a trusted repository, there are no virus for Linux in the wild and security flaws are corrected pretty fast due the open source nature of the programs. It's not totally safe, but much better than Windows out-of-the-box.

That being said, I confess I use a firewall. But I don't use Firestarter or any other firewall manager. I create my on iptables rules and most of the time I block all incoming connections, both on the router and on the iptables. Just open what I need on-demand.


> **mojolobo said:**
> 2.how does firewall in linux , differ from something i would use in windows like Comado or Zonealarm.

The linux firewall is silent and based on port/protocol/ip, not on applications. Which means it won't alert you about a connection attempt and won't let you control which programs can or cannot access the network. I guess ufw allows to use application based rules, but I never tried. This is not a big problem, since you download (at least you should) softwares only from the repositories and even if you don't, they are most likely to be open source. So malicious code is easily spotted by the community and you can also inspect the code. Unlike Windows, where most programs are closed source and you never know what the hell they can do. Nevertheless, you can also block outgoing connections system wide and allow only connections on ports that you need. For example, you would have to allow outgoing connections on port 80 and 443 to surf the web. You also need to allow some ports to let your machine connect to your ISP or allow the ISP ips. Besides that, if you only use the network to surf the web, you won't need any additional ports to be opened for outgoing connections. But I would bother with outgoing connections, unless you have very specific needs. UFW doesn't even has an option to block outgoing connections.

> **mojolobo said:**
> i have disabled my boot screen so i can view loading on bootup. everything is ok , loading firestarter firewall:fail
3. since i dont need firestarter this should not be a problem ? right?

Not necessarily true. It has been a while since I used Firestarter for the last time, but as far as I remember, iptables rules are not persistent, unless you modify some configuration files to make them so. Try booting your system without starting Firestarter. Then run the command *sudo iptables -L* and check if there are only a few rules, all with the ALLOW word. If this is true, then you need to start Firestarter, so it can create the rules again. Firestarter by itself won't forget the rules, but it need to load to create them again on the iptables. Once they are created then you can close Firestarter until the next boot. Firestarter fails to load on boot, probably because it needs root privileges to run. So while you are booting you can't enter the password to allow Firestarter to run. There is a way to make it run as root on boot, but I wouldn't recommend, since this might be a security risk. As I said before, I recommend uinstalling Firestrater and installing GUFW.

I recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

---

### Post by kpkeerthi on 2009-05-11
If you need a GUI for iptable, use [gufw]("http://gufw.tuxfamily.org/index.html"). Here's a [howto]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html").

Firestarter is outdated and is no longer maintained.

---

### Post by mojolobo on 2009-05-12
thank for all the info , really appreciate it

---

### Post by humbug01 on 2009-05-12
Ditto my thanks as I've listened in with same questions. Switching to gufw now....

H

---

