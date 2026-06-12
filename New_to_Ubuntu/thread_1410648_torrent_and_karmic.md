---
title: "torrent and karmic"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by archangel_micheal on 2010-02-19
to anyone help.

i have installed karmic and have a dd-wrt firmware on a linksys router. and i know that all firewall ports are closed out of the box. i have tried to open the ports and use port forwarding, also dmz, upnp and a number of other methods to get my vuze to see past the firewall on the router and on the computer and acknowledge that a port is open and listening so i can upload some different material for others to share of my creation.

i admit i am new, and i need to be pointed to a complete howto on doing this. any help would be appreciated. thanks in advance.

---

### Post by nhasian on 2010-02-19
you dont need to mess with any firewall settings in ubuntu.  you only need to forward the correct port from your router to your computer's IP address.  then tell your torrent software which port number to use.  For example in your router you can forward port 51234 to ip address 192.168.0.100.  That is assuming your computer is on 192.168.0.100 and that it never changes.  (You should be able to set the dhcp server in the dd-wrt to assign the same number to a particular computer each time) anyway, then in the bittorrent client on said computer you will also telll it to use port 51234 and then you are done.

---

### Post by 3rdalbum on 2010-02-19
By default, on Ubuntu, the firewall ports are OPEN. But there is nothing listening on those ports.

---

### Post by lijcam on 2010-02-19
To make sure the firewall in ubuntu is not on:

```
sudo ufw status
``` It should return "inactive" if disabled.
If it is on you can disable it by:
```
sudo ufw disable
```

Another problem is your ISP might be blocking the port so make sure your pick a very high port.

---

### Post by archangel_micheal on 2010-02-19
thanks everyone. i will try all of this and thanks for the prompt response.

---

