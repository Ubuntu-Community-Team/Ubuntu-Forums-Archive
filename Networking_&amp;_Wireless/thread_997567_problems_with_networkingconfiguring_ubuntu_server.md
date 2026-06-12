---
title: "problems with networking/configuring ubuntu server"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by L14UX_1NS1D3 on 2008-11-29
Hello. I've have run into some annoying problems while setting up ubuntu server. 
First off I have installed webmin and torrentflux on the server. I have scoured the filesystem for configuration file to see what ports these programs run on and how to conjure them on a web browser, but alas I have found no way to change settings via conf files.

I have given the server the static ip 192.168.1.5 and a client computer, for testing the connection with, 192.168.1.9 .

I briefly was able to ping the server from the connected client, and from the server ping the client comp. I don't know what I changed that made it work after having tried many times having to edit the /etc/network/interfaces file and working with ifconfig to change the ip

I'm really, really stuck! I even tried asking around for some answers on the ubuntu ircs but people either don't know what I'm talking about or are idle on the channel.

FYI I'm runing the ethernet cable into a 4-port wired router and from there connecting the computer to test the connection. 
I wish I knew a way to connect the client directly to the server and have it work. On the server I have five 10/100kbps ethernet cards on the comp. My plan is eth0 to be the access port for connecting to the server via ssh or whatever and eth1 be connected to a router for access on the local network. I have no experience with setting up a server other than freenas. Please help, any info is greatly appreciated! :confused:

---

### Post by bab1 on 2008-11-30
> FYI I'm runing the ethernet cable into a 4-port wired router and from there connecting the computer to test the connection.
I wish I knew a way to connect the client directly to the server and have it work. 

In a sense they are directly connected (DC).  No hops through a router is DC.  The 4 ports are a layer 2 switch.  All connections keep track of the MAC addresses of the attached devices.

> On the server I have five 10/100kbps ethernet cards on the comp. My plan is eth0 to be the access port for connecting to the server via ssh or whatever and eth1 be connected to a router for access on the local network.

Unless you are going to use the server as a router or are going to bond the NIC's together there is no need to have a multi-homed host.

---

### Post by CodeAlias on 2008-11-30
Hi, 

This could be routing problem.
Check your default route by typing 

```
sudo route
```


---
[Network Security, Wireless and Performance]("http://www.codealias.info")

---

