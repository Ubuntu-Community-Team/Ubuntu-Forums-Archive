---
title: "Unable to change MAC address with ifconfig commands..."
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-06-05
I've read that you can temporarily change the MAC address of your wireless NIC with something like:
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 00:28:C7:0A:42:A2
sudo ifconfig wlan0 up

```
Unfortunately this doesn't seem to work for me. After doing the "sudo ifconfig wlan0 hw ether 00:28:C7:0A:42:A2", if I then do "ifconfig", it doesn't show my MAC has changed to the new value. And then when I do the "sudo ifconfig wlan0 up", it doesn't bring up my wireless connection fully; I have to do a "sudo /etc/init.d/networking restart" or "sudo ifup wlan0" to actually bring up my wireless connection.

Can someone please give me some insight what is happening? Why doesn't the ifconfig command change the MAC address, and why do I need more than the simple "sudo ifconfig wlan0 up" to bring up the interface?

Thanks for any help.

---

