---
title: "HOWTO: Scan for and Connect to a Wireless Network from the Command Line"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by mbsullivan on 2008-02-16
There are a multitude of fine, graphical wireless network configuration programs available to the Ubuntu community. However, there may come a day when you need to acquire a wireless connection from an unknown network on a strange network card from the recovery console. Or perhaps you just want to know how to connect to your home network from the command line. Either way, this HOWTO is for you.

This guide assumes that the drivers for your network card are properly set up. Otherwise, it would be too complicated to cover all vendors and chipsets.

So, without further ado...

[SIZE="4"]**(1) Figure out the name of the interface for your wireless card**[/SIZE]

The interface name of cards for different vendors may be different, which is why this step is needed:

```
ls /sys/class/net
```

This will list the interface names for all NICs on your computer. It will probably include eth0 (hardwired NIC), lo (loopback interface for the localhost), and something for your wireless card (like wifi0, or wlan0). 

For these steps let's call whatever name you find for your wireless NIC ***[wifi interface]***.

If you have multiple wireless cards, all of them will be listed. To be sure that the interface that you select is a wireless interface, you can check that its directory contains a "wireless" folder:

```
cd /sys/class/net/*[wifi interface]*/wireless/
```

[SIZE="4"]**(2) Just to be sure it's not being used, bring your interface down, release your DHCP connection and then put it back up:**[/SIZE]

```
sudo ifconfig *[wifi interface]* down
sudo dhclient -r *[wifi interface]*
sudo ifconfig *[wifi interface]* up
```

Many of these commands require superuser priviledges (i.e. root access), so the sudo command precedes them. Of course, you could always use "sudo -s" or some other method to login to a shell as the root account, but why complicate matters?

[SIZE="4"]**(3) Scan for open networks**[/SIZE]

```
sudo iwlist *[wifi interface]* scan
```

This should return results that look something like this:

> wlan0     Scan completed :
          Cell 01 - Address: 00:04:E2:D0:D1:96
                    ESSID:"SMC"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Quality=78/100  Signal level=-56 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000039cdb32ac3


The **ESSID**, **Frequency** and **Address** are the most important labels here (quality may also factor into your decision, too... higher is better).

**[SIZE="4"](4) Set the wireless NIC so that it will connect to the found wireless network:[/SIZE]**

```
sudo iwconfig *[wifi interface]* ap *[whatever you found for the MAC address]*
sudo iwconfig *[wifi interface]* essid *[whatever you found for essid]*
sudo iwconfig *[wifi interface]* freq *[whatever you found for frequency]*G
```

Note the "G" after the frequency, to denote "GHz".

[SIZE="4"]**(5) Acquire a DHCP address from your wireless router:**[/SIZE]

```
sudo dhclient *[wifi interface]*
```

Okay... assuming that your DHCP address was acquired properly, you should have a internet connection all set up.  Now, this is probably too complicated of a process to do by hand, but there are a number of ways to automate it. That's outside the scope of this tutorial!

Now go out and be somebody!
Mike

---

### Post by K.Mandla on 2008-02-19
Moved to Networking and Wireless.

---

