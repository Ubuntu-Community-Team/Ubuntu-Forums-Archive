---
title: "Ubuntu Server 16.04 VirtualBox IP Not Working"
date: 2016-07-22
forum: Networking &amp; Wireless
---

### Post by lucabrazza98 on 2016-07-22
Hi,
So I have Ubuntu 16.04 Server installed on Virtual Box 64bit, and I'm using Apache but have no way to use a web browser that is connected to the same network as the virtual machine to see what is being displayed on that IP.
When I type ```
ifconfig | grep addr
``` this comes up: [http://prntscr.com/bw7eti](http://prntscr.com/bw7eti).
192.168.1.204 - refused to connect.
192.168.1.255 -  might be temporarily down or it may have moved permanently to a new web address

192.168.122.1 - took too long to respond.
192.168.122.225 -  took too long to respond.
127.0.1.1 - blank white page.

My Virtual Box Network settings are: 
Attached to: Bridged Adapter
Name: Intel(R) 82566DM-2 Gigabit Network Connection.
Adapter Type: Intel PRO/1000 MT Desktop (82540EM)
Promiscuous Mode: Allow VMs
MAC Address: 0800274926A
Cable Connected - Ticked.
----------------------
Thanks!
Luca

---

### Post by &amp;KyT$0P# on 2016-07-22
Your link does not work for me.

Give the VM a (additional) host-only network adapter, and try to connect using the IP address the VM has on that adapter.  Does it work?

---

### Post by lucabrazza98 on 2016-07-22
Thanks for your reply so fast!
Now I have 2 network adapters, One Bridged and one Host Only.
I typed in ```
ifconfig | grep addr
``` and all the ip's were still the same and still didnt work.
Thanks
Luca

---

### Post by &amp;KyT$0P# on 2016-07-22
:confused:
There should be one additional IP address listed.  Please post the full output of ifconfig (with both network adapters still there)

---

### Post by lucabrazza98 on 2016-07-22
The Image of ```
ifconfig
``` is attached.
Thanks
Luca[IMG]http://image.prntscr.com/image/e2b1c9de5baf43fea59083c87d2b9f18.png[/IMG]

---

### Post by lucabrazza98 on 2016-07-22
Ok... Suddenly it has started working! Thank you!!!!

---

