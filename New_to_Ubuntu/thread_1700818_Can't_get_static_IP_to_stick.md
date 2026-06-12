---
title: "Can't get static IP to stick"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by rp7183 on 2011-03-05
Hello all, I am indeed a Linux noob. Reading through on the internet I've learned how I can set a static ip by editing the /etc/network/interfaces file. Let me start by saying I am connecting via a wireless connection. So I appended the following changes to the file:

> auto wlan0
iface wlan0 inet static
              address 192.168.0.157
              netmask 255.255.255.0
              network 192.168.0.0
              broadcast 192.168.0.255
              gateway 192.168.0.1

This actually works fine and does exactly what I want it to do. The problem comes when I restart my computer. When I restart, not only do I not have a static IP, but I am not connected at all, and the networking panel icon disappears. To get it back I have to do the following:

> sudo service network-manager stop
sudo service network-manager start

When I do this, I'm still not connecting. The only way I can connect after that is to remove the settings for wlan0 in the interfaces file and restart networking.

Any advise is greatly appreciated. 

Thanks

---

### Post by Pougnet on 2011-03-05
I say create a start-up script to restart the network manager for the time being.
Here one is from [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) full credit to [U]wieman01
[/U]
```
sudo gedit /etc/init.d/wireless-network
```add this line and save
```
/etc/init.d/networking restart
```Change permission
```
sudo chmod +x /etc/init.d/wireless-network
```Create symbolic link
```
sudo ln -s /etc/init.d/wireless-network /etc/rcS.d/**[COLOR=Red]S40[/COLOR]**wireless-network
```Restart

---

### Post by dwasifar on 2011-03-05
I've seen this kind of conflict between the conventional way of setting static IPs and the Network Manager way before.

To solve your problem, use Network Manager to set your static IPs instead of setting them in the config file, thus:

1) Remove your changes to /etc/network/interfaces.
2) Go to System>Preferences>Network Connections.
3) Select the Wireless tab, highlight the wireless connection you wish to set a static IP for, and choose Edit.
4) Go to the IPv4 tab and change the Method drop-down to "Manual."
5) Click Add to add a line to the addresses list, and enter the same information you tried to use in /etc/network/interfaces.  
6) Also fill in the DNS servers field; typically you will use your gateway address there.  If that doesn't work try 8.8.4.4, 8.8.8.8.
7) Click Apply.

This will usually cause your connection to drop and reconnect right away, if you are already using that connection.  If not, you should get your static IP next time you connect to that connection.

If you're still having trouble after this, make sure the static IP you're trying to use is within the range that the router is configured to provide.

---

### Post by perspectoff on 2011-03-12
I have never been able to get Network Manager to reliably manage static IPs for some reason. On my Ethernet-wired computers, I don't use Network Manager at all and uninstall it completely. Then I use the method of the original post (i.e. editing the /etc/network/interfaces config file).

It is Network Manager that screws up the static IP connections on my systems.

For wireless static IP, I use WICD instead of Network Manager.

The bottom line is that I don't use Network Manager on any of my Ubuntu/Kubuntu systems that use a static IP and remove it on all of them.

---

