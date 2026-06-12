---
title: "Configure wifi through Bluetooth?"
date: 2020-12-05
forum: Networking &amp; Wireless
---

### Post by Beandip408 on 2020-12-05
Does anyone know of any good tutorials on how to configure a headless Ubuntu machine by connecting to wifi via bluetooth? for the raspberry pi there is berrylan.com but im not finding anything for Ubuntu.

---

### Post by TheFu on 2020-12-05
During the insallation, choose to install the ssh server.  Then you can scan the network for the dhcp IP and login using ssh.
BT isn't part of the "server" install.

Without a head during install, you are stuck. Normally, a serial console would be setup, but that isn't enabled by default for any stock ubuntu installer. 

The setup for ARM is special.

---

### Post by Beandip408 on 2020-12-05
> **TheFu said:**
> During the insallation, choose to install the ssh server.  Then you can scan the network for the dhcp IP and login using ssh.
BT isn't part of the "server" install.

Without a head during install, you are stuck. Normally, a serial console would be setup, but that isn't enabled by default for any stock ubuntu installer. 

The setup for ARM is special.


Thanks, but i need a way to configure the wifi creds if the machine isnt connected to a network. i was doing this with a raspberry pi and [www.berrylan.com](www.berrylan.com) but it doesnt have the same packages for Ubuntu as it did for Raspbian.

---

### Post by TheFu on 2020-12-05
On a rasberry-pi, you can pull the boot media out, connect it to another system and configure the wifi stuff that way, I suppose.

On an x86 machine, I've never heard of any method that wasn't
a) using wired dhcp (no clue how to do this with wifi)
b) using serial console (no GPU); I use a USB-to-serial cable with minicom for this AFTER configuring grub to boot with an 8-n-1-115200 connection. [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
c) pre-installing using a different machine, then moving the HDD/SSD over to the new system, though I have doubts this will work since MACs would change.

[https://askubuntu.com/questions/406166/how-can-i-configure-my-headless-server-to-connect-to-a-wireless-network-automati](https://askubuntu.com/questions/406166/how-can-i-configure-my-headless-server-to-connect-to-a-wireless-network-automati) might be helpful, though much of the way that networking is configured has drastically changed in the last 5 yrs. Perhaps there are nm-* commands that can be accessed over the serial console?  Netplan has replaced /etc/network/interfaces about 3 yrs ago.

Searching for BT solutions only found really old stuff from 8+ yrs ago: [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup). I doubt that works.

You might find better help if you clearly said which OS, which release, you are attempting this with.  When you say headless, I've assumed Ubuntu Server. You didn't say which release - is it 20.04 or something else?  

I really don't think what you seek is possible, but I could be wrong.

---

