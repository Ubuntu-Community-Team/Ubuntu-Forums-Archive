---
title: "how to log network connection activity?"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by jamesey on 2007-12-11
I want to log the "thought process" of my machine's network connection. 

When I boot up in Gutsy, I do not automatically connect to my home wireless network. Despite this, a Screenlet tells me that the connection strength is always above 95%. I know that's not an issue because in Feisty my connection worked flawlessly. 

If I'm impatient, I can go to the network manager, uncheck the box for my wireless connection, check it again, and be connected right away. If I'm patient, I can wait 15 minutes, and Gutsy will suddenly decide to connect itself to the network. 

Within the first hour of getting connected, my connection will drop and reconnect multiple times before eventually being stable for the rest of the day. It's really annoying. 

I have no idea what setting or trigger would cause this type of behavior. I want to see a log of what my computer is thinking as these things happen so I (or someone on these forums can help me) can troubleshoot. Anyone know how I can do this?

---

### Post by imog on 2007-12-11
While I dont know how to do this exactly, I know it is possible to view a log of what your machine is currently processing.

Alternatively, what you may try doing is installing/running wireshark and capturing packets on your wireless network interface.  It is straightforward to do, and if you save the capture, we could look at it to see what is being transmitted over the air when your getting disconnected or trying to initially authenticate to the AP.  I suggest this because it may help us figure it out, and I actually know how to do it.

Once wireshark is installed, you click on interfaces at the top, then select options for your wireless interface, name a log file, then start capturing.  Share the log file with us and we can look to see whats being transmitted.

---

### Post by jamesey on 2007-12-11
bueller?

---

### Post by imog on 2007-12-12
Alright, I was having a problem where it appeared as though ubuntu was locking up today so I needed to figure out the real answer to your question to fix my own problem.

What I did was from a terminal I issued:
gedit /var/log/messages

It opened and it told me wtf my system was doing when it was becoming intermittently nonresponsive for several seconds at a time.  It was clear my touchpad was going haywire, so I installed a synaptic config utility and turned off the touchpad altogether since I dont use it.  Everything is fine now.

If you did the same, you may see some messages about what is failing and causing your own problem.  Alternatively, all you really need is to read about the "dmesg" command which will get you to the same information.

---

### Post by jamesey on 2007-12-18
can anyone make anything of this?
jamesey is my machine name. I've been having funky connectivity problems during this time

Dec 18 19:01:23 jamesey kernel: [47416.812000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 18 19:01:24 jamesey kernel: [47417.924000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:25 jamesey dhcdbd: Unrequested down ?:3
Dec 18 19:02:25 jamesey kernel: [47478.964000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:28 jamesey kernel: [47481.388000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 18 19:02:33 jamesey kernel: [47487.044000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!

---

