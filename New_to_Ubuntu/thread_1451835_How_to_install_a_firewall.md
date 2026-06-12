---
title: "How to install a firewall"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by anirban00 on 2010-04-11
hi all, i am new to ubuntu

 i want to install a firewall on my system, so how do i go about it.:)

 Thanks in advance for all your replies.

---

### Post by Sin@Sin-Sacrifice on 2010-04-11
[iptables]("https://help.ubuntu.com/community/IptablesHowTo") is already on your system. A good gui for it is gufw. ```
sudo apt-get install gufw
``` A good resource for it is ```
man ufw
``` And I'm sure there's tons of guides all over the interweb for gufw.

---

### Post by spiky001 on 2010-04-11
hi is there a reason you need a firewalll linux is preety safe by default it,s ot like windows?
if you do need 1 there is gufw in the repos

---

### Post by mbzn on 2010-04-11
Hi linux's 'iptables' is already installed and stronger than a firewall on most home computers. for server needs, iptables can be confugured with apps such as firestarter.

hope this may be of help [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2010-04-11
Hmm, first you need to figure out whether you really need it and what you want it to do.

The 'firewall' is actually already present.  All you need to do is configure the netfilter rules.  By default, the Ubuntu system doesn't need any special firewall rules.

Soooo, if you don't really know what your are doing yet and don't know whether you need it, or what it is all about, install Gufw.  

Otherwise, doing nothing is also a safe bet.

If you want to learn about all the gory details, Google for "Rusty Russell's Notoriously Unreliable Web Site".

---

### Post by lisati on 2010-04-11
If you're behind a router, you're probably fairly safe - many routers these days come with firewall capabilities.

---

### Post by 3rdalbum on 2010-04-11
By default, Ubuntu doesn't listen to any incoming ports anyway; it'll ignore all incoming connections, which is what a firewall does.

On Windows, you need a firewall because there are parts of Windows that listen to incoming connections without actually needing to. They are a security problem. On Ubuntu nothing listens unless you tell it to, or install some software that always listens (a "server"), and the programs that listen to incoming ports are usually locked down pretty well.

So unless you've installed some server software or turned on Remote Desktop, your system will already be acting as though it has a firewall.

---

### Post by Volcom3 on 2010-04-11
If your not running a server look into APPARMOR or UFW "Ubuntu Fire Wall"

---

