---
title: "Unable to start network in VM"
date: 2015-07-05
forum: Networking &amp; Wireless
---

### Post by zpb0103 on 2015-07-05
I use both Ubuntu and Xubuntu in a VM (virtualbox), primarily for gnucash. 

I started with Ubuntu and when it was no longer able to start the network connection (bridged) I decided I'd try Xubuntu next since Ubuntu seemed sluggish in this environment. Now Xubuntu is having the same exact problem as Ubuntu. Its about a week in and it cant start the network connection. I can startup any other vm I have (ubu server, freebsd, and win2008; I code) on the same machine using virtual box and it has no problem. I can leave any other vm running for weeks, and I do, and its no problem. It is only with Ubuntu and Xubuntu that this happens. 

[http://imgur.com/19Z4v9Z](http://imgur.com/19Z4v9Z)

It doesnt happen after I install things (which is rare) or when I'm making changes. I rarely use Ubu/Xub for anything other than gnucash. I often dont notice that I dont have a connection because I literally dont use the machine for anything else. Sometimes I dont know until I happen to restart and it hangs during its startup process with a waiting for network notification. 

Every time this happens I dont know how to fix it so I end up just reinstalling and starting over. I'd like some help figuring out why this is happening or a fix for it. Again, this doesnt happen with any other vms other than ubuntu and xubuntu. I almost think it has something to do with network manager because it doesnt happen in ubuntu server. 

Please help before I tear any more hair out.

---

### Post by ajgreeny on 2015-07-05
Why use a bridged connection?

I have many VMs on a Xubuntu 14.04 host; all use the standard NAT connection type and run faultlessly.
I have never used bridged connections so can help with any information on that, but a default NAT may solve your problem assuming it is an option for you.

---

### Post by zpb0103 on 2015-07-05
Hi ajgreeny, 

Thanks for responding. I use bridged primarily because thats what the servers I test with also run. They need to be able to communicate with other devices on the network without additional configuration. I have a naming and addressing scheme so I can easily identify the purpose of the vm without having to looking at a spreadsheet. I used the same concepts when I setup the vm for gnucash for ease of use. 

I have tried NAT with the same result. I've also tried stopping the VM and adding another network card, but it too fails during startup. They both get the same error message, [http://imgur.com/19Z4v9Z](http://imgur.com/19Z4v9Z)

Since I didnt clarify before, I'm on windows 8.1 and running a xubuntu and ubuntu client in vritualbox. 

I can do the basics in linux eg manually configure settings and install things... but dont know the troubleshooting for an issue like this. Any ideas on where to start?

---

### Post by zpb0103 on 2015-07-05
Update

While looking into it tonight, I noticed my /etc/network/interfaces file had been changed on 6-25, not sure what would have changed it since I dont install anything, just updates, but when I looked at it... it was missing inet for eth0. Such a silly thing to miss. Still wondering what changed it, I'll keep an eye out going forward.

---

### Post by ajgreeny on 2015-07-06
If this problem is now solved please mark is such from the Thread Tools menu up top of the thread.

---

