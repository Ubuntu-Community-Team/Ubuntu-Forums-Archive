---
title: "How to disconnect from a wireless network ?"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by sistoviejo on 2007-11-15
This will probably sound silly...
I clicked on the network manager and then accidentally clicked on an open network and connected to the network.
How do I disconnect now? :confused:
Thanks!

---

### Post by unerau on 2007-11-15
i think you should kill it.

search in  google how to kill it. yes kill

i will tell you some more about it later, once i get home =)

---

### Post by sistoviejo on 2007-11-15
I tried google for it but couldn't find anything. I tried using my hardware button to disable it but the wireless manager still told me it was connected.

Finally I killed this process:

/usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid

And then I started it again and this seems to have actually disconnected from the network.

Thanks! 

PS: Doing this seems to be a little awkward when I am actually using a GUI. A "Disconnect" button would be nice.

---

### Post by V-600 on 2007-11-15
The quickest way I found to disconnect is to click on the network manager and reselect the network you are connected to. When the network key window appears, click cancel and it disconnects you.

Not tried with an unsecured network though as I haven't got one in range. It may be similar though.

---

### Post by kevdog on 2007-11-15
Its easy to do from the command line if you are using dhcp 

sudo dhclient -r <interface name>

For example:
sudo dhclient -r wlan0

This releases the dynamically assigned IP address assigned by the wireless server.  

Another approach would be to disable or turn the wireless card or wired card off (Think of it as a software switch).

This would be 
sudo ifconfig <interface name> down

So something like this

sudo ifconfig wlan0 down

---

### Post by sistoviejo on 2007-11-15
I guess it would be good if nm-applet would allow you to disconnect besides connecting to a wireless network. A disconnect button would be usefull. Don't you think?

EDIT: I've noticed that you can disable wireless lan simply by right clicking on the network manager icon and unchecking "enable wireless".
The bad thing is that it will automatically reconnect to the same network when I enable wireless lan again.

---

