---
title: "Home network"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by bluefightingcat on 2007-08-18
Hi,

I have got a laptop and a desktop. I want to setup a simple home network to share files. I've read around and Is that the best way seems to be NFS. Both machines run Kubuntu Feisty. 

I followed the wiki to try and setup the NFS server on my laptop and the client on my desktop. The idea would be to get files from my laptop and move them to my desktop. 

However I think there seems to be some problems with my network card configurations. Both computers have one wireless adapter (which work fine) and one ethernet card. 

Since I only want to use the ethernet cards to connect to the home network, I assume that it would be useful to give them a fixed static ip. Is this a correct assumption?

If I am not mistaken this can be achieved by editing /etc/network/interface. Is this correct?

And would the entry for the ethernet be something like this:

auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx (anything I want)
netmask 255.255.255.0
gateway 0.0.0.0

Would an entry like this be correct?


BFC

---

### Post by bluefightingcat on 2007-08-18
Hi,

I think I am really really close to getting NFS network working. The problem is I just can't figure what my server and domain names are. The instructions say to put this:


sudo mount server.mydomain.com:/files /files

but what exactly do I have to replace in server.mydomain.com 

Where do I find this information from. 

What I have tried so far is to put "timo-desktop"  which is the name of my computer. But all I get with this is an error that says:

mount: can't get address for timo-desktop


So I am little confused here. 

BCF

---

### Post by TheWizzard on 2007-08-18
> **bluefightingcat said:**
> Hi,

I think I am really really close to getting NFS network working. The problem is I just can't figure what my server and domain names are. The instructions say to put this:


sudo mount server.mydomain.com:/files /files

but what exactly do I have to replace in server.mydomain.com 

Where do I find this information from. 

What I have tried so far is to put "timo-desktop"  which is the name of my computer. But all I get with this is an error that says:

mount: can't get address for timo-desktop


So I am little confused here. 

BCF


```
cat /etc/hosts
```
should give you the IP or alias of your server

---

### Post by TheWizzard on 2007-08-18
oops.:oops:

only if you made aliases...
make sure the server has a static IP. use the **server's** ip or make an alias.

---

### Post by bluefightingcat on 2007-08-19
Hi,

Sorry I am bit of a newbie. What exactly do you mean? and how do I find my servers ip?

BFC

---

### Post by TheWizzard on 2007-08-19
> **bluefightingcat said:**
> Hi,

Sorry I am bit of a newbie. What exactly do you mean? and how do I find my servers ip?

BFC

ok, your client computer has to find your server. so it needs the address. this can be a local IP address or a more friendly format like server.mydomain.com

to get the address, go to the server and open a terminal.
type:
```
ifconfig
```

now you see your network devices listed. the active one should have something like this: 
```
inet addr:192.168.1.100
```

192.168.1.100 is the IP address of the server.

now go back to the client computer and use the ip of the server to connect.

good luck.

---

### Post by bluefightingcat on 2007-08-20
Hi,

Ok I took your advice. However now when I try and mount on the client: 

sudo mount 192.168.1.2:/home/timo /media/desktop

This command gives this output:

mount to NFS server '192.168.1.2' failed. 


I did some searching around but I have no idea why this happens. Any suggestions?

BFC

---

### Post by TheWizzard on 2007-08-20
did you try to ping the server?

---

### Post by bluefightingcat on 2007-08-20
Hi,

I just pinged it and it works fine. Perfect communication with the server. 

BFC

---

### Post by TheWizzard on 2007-08-20
cool.
i don't use NFS myself, so i'm affraid i cant help you further. 

good luck

---

### Post by bluefightingcat on 2007-08-22
Hi,

I found the problem. I had both the Server and Client setup with the same static IP. :oops:

Now it works fine. 

BFC

---

