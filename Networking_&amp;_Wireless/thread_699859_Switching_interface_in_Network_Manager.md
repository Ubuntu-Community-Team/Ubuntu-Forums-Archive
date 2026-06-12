---
title: "Switching interface in Network Manager?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by petzworld999 on 2008-02-17
Hello. I recently purchased a Linksys WUSB54GC USB wireless adapter for my computer after my Broadcom card died. The interface for the Linksys card is wlan0. The interface for the now dead Broadcom card is eth1. When connecting in the nm-applet, the network manager uses the dead Broadcom card as the default interface. Is it possible to change the interface on the nm-applet from eth1 to wlan0?

---

### Post by julian67 on 2008-02-17
Haven't been in that situation myself but several ideas come to mind. 1st blacklist the broadcom driver so your OS doesn't try to use it, then reboot. Or better physically remove the defunct hardware (if you can) and reboot. You could also edit  the /etc/network/interfaces file (back it up first) to remove mention of the broadcom card and then restart networking ```
sudo /etc/init.d/networking restart
``` or reboot.

---

### Post by petzworld999 on 2008-02-17
Ok, now it is not recognizing the blacklisted driver or my eth1 interface. I click on the applet and it just asks me for 'Manual Configuration.' How do I add my wlan0 interface to the applet?

---

### Post by julian67 on 2008-02-17
> **petzworld999 said:**
> Ok, now it is not recognizing the blacklisted driver or my eth1 interface. I click on the applet and it just asks me for 'Manual Configuration.' How do I add my wlan0 interface to the applet?

please say what you actually did of the several suggestions I made and also if you did anything else too. It would be helpful if you can post your /etc/network/interfaces file

---

### Post by petzworld999 on 2008-02-17
I blacklisted the Broadcom drivers and removed it from my /etc/network/interfaces file, which looks like this:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0



iface eth0 inet dhcp



iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Home Network

auto wlan0





```

where eth0 is my wired Internet.

---

### Post by julian67 on 2008-02-17
Your interfaces file should look like this (assuming tou're using dhcp to get connected)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
#iface wlan0 inet dhcp
```

edit: or for your static ip ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.101
netmask 255.255.255.0


auto wlan0

```

I'm not sure you need the gateway specified, nm should deal with that so try without first. reboot and nm-applet should use your new wireless adapter and see your wireless network.

edit: sorry i made a mistake....2 AM here. Have edited the above, should be good now.  Your wired interface is using dhcp so nm should deal with it without it being mentioned in the interfaces file.

---

### Post by petzworld999 on 2008-02-17
When the last line is commented out, I can attempt to connect with the applet, but I do not succeed. When the last line is not commented out, I can connect, but not with the applet. When the line is commented out, I get the following error when restarting networking:
```
Ignoring unknown interface wlan0=wlan0.

```

---

### Post by julian67 on 2008-02-17
> **petzworld999 said:**
> When the last line is commented out, I can attempt to connect with the applet, but I do not succeed. When the last line is not commented out, I can connect, but not with the applet. When the line is commented out, I get the following error when restarting networking:
```
Ignoring unknown interface wlan0=wlan0.

```

sorry i made a mistake, just edited as you posted, see above.

---

### Post by petzworld999 on 2008-02-17
That didn't work, but now it also has a greyed out 'Wired Network' option.

---

### Post by kevdog on 2008-02-17
Is your wired network eth0?  A reference to eth0 should be in the interfaces file if you want to automatically bring and configure this interface.

---

### Post by petzworld999 on 2008-02-17
eth0 is my wired network.
eth1 was my wireless network.
wlan0 is my new wireless network.
lo is the loopback interface.

---

### Post by kevdog on 2008-02-17
So what do you want to do?  Bring up eth0 automatically at boot?

---

### Post by petzworld999 on 2008-02-17
I want to be able to use the nm-applet to connect to wireless networks for wlan0.

---

### Post by kevdog on 2008-02-17
So if you go to the command line and do the following and then try to use nm to connect -- does it work?

sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

---

### Post by petzworld999 on 2008-02-17
No, nm still gives me the option to enter a manual configuration or switch to a wired network if I have a cable plugged in.

---

### Post by kevdog on 2008-02-17
Ok, with the cable plugged in, can you list ifconfig prior and after running the above commands?

---

### Post by petzworld999 on 2008-02-17
My cable is being borrowed by a family member at the moment. The wired network is something that I don't care about, I just want to be able to see all the wireless networks that I can connect to from the applet.

---

### Post by kevdog on 2008-02-17
What does

iwlist scan show?

This command should show you all the networks on the command line (NM uses the same command internally to produce the results in the GUI)

---

### Post by julian67 on 2008-02-18
petzworld999 how's it going? I had to sleep but finally woke up so will try to help if possible.

---

### Post by petzworld999 on 2008-02-18
iwlist shows this: 
```

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

```

---

### Post by julian67 on 2008-02-19
```
iwlist scan
```

---

