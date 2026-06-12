---
title: "How to change mac adress with network manager"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by shunklord on 2007-08-16
Hello

How i can change my mac adress when i use the network manager ?

thanks

---

### Post by praet on 2007-08-16
Note that while you cannot change the physical unique mac address embedded into the network hardware, you can change the software layer mac address.
There is no way to do it in a gui form (network manager), but in a terminal open:
```
$ sudo gedit /etc/network/interfaces
```
which will open the interfaces file
```
auto lo
``` is the loopback interface
```
auto eth0
iface eth0 inet dhcp
```
It could also be eth1 etc..

Just add the line below with the desired mac address as shown:
```
auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06

```

After saving the file, restart your networking.
```
sudo /etc/init.d/networking restart
```

---

### Post by atonaldenim on 2007-09-18
I'm not sure if the above method works when using NetworkManager.

A method I have verified on my wireless card using NetworkManager on Feisty Fawn is the simple program [GNU Mac Changer]("http://www.alobbs.com/macchanger/"). It was already installed on my system, but if not...
```
sudo apt-get install macchanger
```
To change the MAC address for an interface, you must leave Networking Enabled in NetworkManager, while disabling only the particular interface you wish to change. For my wireless card, I right-clicked the NM Applet, and unchecked Enable Wireless, while leaving Enable Networking checked.

Then the command is simply:
```
sudo macchanger eth1
```
which iterates the last bit of your real MAC. (of course you must change "eth1" in the above example to refer to your network interface.) The command accepts many other options as well, see **man macchanger**.

Finally, re-enable the interface in Network Manager, and your new MAC address should be listed in Connection Information.

(thanks to James Crocker's article [Anonymizing Network MAC Addresses]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses"))

---

### Post by netztier on 2007-09-19
> **praet said:**
> Note that while you cannot change the physical unique mac address embedded into the network hardware, you can change the software layer mac address.
There is no way to do it in a gui form (network manager), but in a terminal open:


The method you describe can't work with network-manager, because of the requirement that any interface you want to manage with network-manager*must not* be configured via **/etc/network/interfaces**.

As suggested by atonaldenim, **macchanger** might work.

best regards

Marc

---

