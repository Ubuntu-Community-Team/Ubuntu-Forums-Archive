---
title: "Installing a home server (beginner...)"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by ianjames711 on 2010-04-26
I just installed the newest addition of ubuntu server on an old computer so I could try and learn what it is like to be an administrator of a (home) ubuntu server and I have already run into trouble... I install everything alright but now that everything is up and running I can't seem to establish any kind of connection. I can't ping out to anything and apt-get update failed to fetch anything. When I ping out it says "network unreachable". Can anyone help me? Any help would be appreciated.

---

### Post by 3rdalbum on 2010-04-26
Ubuntu Server doesn't have a GUI, and so it doesn't have Network Manager to automatically manage your connection.

I think all that's required is for you to run:

```
sudo dhclient
```

and then you should have a connection. But don't quote me on that.

Note that Ubuntu Desktop is just as capable as Ubuntu Server at being a server; I use the Desktop edition on my home server. But in the Real World(tm) servers are run without GUIs, so if your object is to learn Real World(tm) skills then best to stick with the command-line.

This may help: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by utnubuuser on 2010-04-26
Slightly off-topic...

You might want to have a look at Turnkey-Appliances  -  Preconfigured ubuntu servers.

---

### Post by HDave on 2010-04-27
Welcome to the world of system administration.  Getting your box on the network and diagnosing issues related to it happens all the time.  Here's a few things:

1) Out of the box, Ubuntu server uses DHCP to get an IP address and the IP address of your gateway (to the internet), and the IP addresses of your DNS servers.  If you do not have a DHCP server running on your network to supply this information then you are out of luck.  Most decent Internet routers have a built-in DHCP server.  If yours does, check it to see if it gave out a "lease" of an IP address to your new server.

2) Make friends with the "ifconfig" command.  Run it as sudo and verify that the network adapter you expect to be up and running is really working and has an assigned IP address.

3) If you don't have a DHCP server, you can assign a static IP address.  You'll need to edit /etc/network/interfaces to supply your IP addr, gateway, and subnet mask.  You'll also need to edit /etc/resolv.conf.

4) If your network adapters themselves aren't working then say hello to the "ethtool" command.

5) The best way to test to see if everything works it to ping the IP address of your router.  If that works then ping [www.google.com](www.google.com).  If that doesn't work then you have a DNS problem.

6) An awesome little text based web browser is "lynx". You can install it from the repos once you get networking going.

7) Don't get a VM appliance.  Get it working yourself...its not that hard and the learning is fun.

8) While you can install the desktop version of Ubuntu and then install the server kernel, doing it the way you are doing is better, faster, and more stable.

---

