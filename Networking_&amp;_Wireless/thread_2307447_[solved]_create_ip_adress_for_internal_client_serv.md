---
title: "[solved] create ip adress for internal client server connection"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by DrScum on 2015-12-25
On my Laptop I am running a win database client on virtual box and want to connect to a MySQL server running on the linux host. Everything is set  up and working perfectly with one basic problem I have to solve now:

The connection to MySQL wasn't possible through localhost. Thus I used the wired IP address of my home office (the ip assigned to my laptop by my home office DHCP server). However, when the laptop  is not connected to the home office network this ip doesn't exist of course and the connection doesn't work. 

I want to create an IP on the Win host which is always available even if there is no active network. Is something like that possible and if yes, how do I set it up?

---

### Post by steeldriver on 2015-12-25
By "address of my home office" do you mean the external (public) IP address of your home router?

It sounds like you should be using a [host-only networking]("https://www.virtualbox.org/manual/ch06.html#network_hostonly") configuration?

---

### Post by DrScum on 2015-12-25
by address of my home office I mean the IP thats assigned to my laptop by the home office server. The wired IP adapter is set to "automatic" thus it gets an ip assigned.

What I need is something like a loopback which already exists in form of "localhost" (127.0.0.1) but since the windows guest in the virtual box setup also uses the "localhost" loopback I can't connect to "localhost" of the linux host.

It looks like the host-only networking you pointed me to is exactly what I am looking for.

---

### Post by DrScum on 2015-12-25
thanks a lot steeldriver, I followed the link you pointed me to and have a working system now.

For people who hit this post trying to solve similar problems some more information:

I am running an Oracle Virtual Box system on a Linux Mint 17 host. As guest system I have a Win7 OS which runs an MS-Access Database application connecting to a MySQL database set up on the Linux host.

---

