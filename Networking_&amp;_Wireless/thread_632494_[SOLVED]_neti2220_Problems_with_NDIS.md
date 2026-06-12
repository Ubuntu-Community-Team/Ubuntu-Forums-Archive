---
title: "[SOLVED] neti2220 Problems with NDIS"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by Nirevus on 2007-12-05
I have recently installed Ubuntu 7.10 on my mums Acer Aspire 1360 for her. Everything works, including all her periphrals, except for the inbuilt wireless.

[COLOR="Red"]EDIT:[/COLOR] Solved! I can't believe I didn't think of this. Once the driver has been installed you simply need to type "ifconfig wlan0 up" at terminal. I didn't need to manually configure the network either.

On the advice of a user on #ubuntu I installed the neti2220 driver with NDIS, and everything went perfectly,  both "ndiswrapper -l" in the terminal, and ndisgtk display that the driver is working and the device is recognised, but it won't pick up any networks.

ndiswrapper -l displays:
```
neti2220 : driver installed
device (17FE:2220) present
```

When I click on the Network Manager panel icon, it originally displayed Wireless, Wired and Modem, with the first two set the roaming mode. However I just noticed after a restart that the Wireless connection isn't displayed anymore, although ndisgtk and "ndiswrapper -l" still both report it as being present and "ndiswrapper -m" outputs "module configuration already contains alias directive"

---

### Post by Nirevus on 2007-12-05
Can anyone help with the problem? I'm not sure of where to turn next, as it doesn't make much sense to me.

---

### Post by xristos on 2007-12-05
Same problem here with aspire 1520 which have the same wireless network card.
"iwlist wlan0 scan" shows nothing
"iwconfig wlan0" shows the usual stuff like it is working normally but when I try to change values e.g. "iwconfig wlan0 essid home channel 6" it doesn't work .

---

### Post by Nirevus on 2007-12-05
For "iwlist wlan0 scan" I get "wlan 0 Interface does not support scanning."

And "iwconfig wlan0" says No such device.

The Wireless Network Drivers application and "ndiswrapper -l" still show it as installed and the device present.

---

### Post by Nirevus on 2007-12-06
I've seen several peolpe on the forum experiencing this problem but nobody has got any answers. The only one I've seen that might of got an answer is in Catalan.

Can anyone even give any ideas to try?

---

### Post by xristos on 2007-12-06
I managed to connect. I tried a lot of stuff so I don't really know which one worked .
I will write about the one I thing made the difference .
Click on the nm-applet icon and select "Connect to Other Wireless Network"
Enter essid and other information manually and hit OK .
Hope it works .
This means that the only problem is that you cannot search for networks , so you must know the essid of the network you want to connect.
Have to remind you that iwconfig works on my laptop.

---

### Post by Nirevus on 2007-12-06
I tried to set up the manual connection before, but to no avail. I'll try again tomorrow, if anyone has any ideas in the mean time I'll also give those a go tomorrow.

---

### Post by Nirevus on 2007-12-08
I now get the same results as you, to iwconfig, but even with it manual configured it doesn't connect to the network.

---

### Post by xristos on 2007-12-09
Try this , edit the /etc/network/interfaces file and comment out all lines but the ones about lo interface . Something like this : ```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0
```

That is because we use the nm-applet . Check this page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

