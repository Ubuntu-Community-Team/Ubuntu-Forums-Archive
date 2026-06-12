---
title: "Problems connecting to network on boot with NDISwrapper"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Hyperkill on 2007-10-31
I recently encountered that problem where your network card fails to connect to the network through network manager.  It seemed to be a problem with my recent upgrade to Gutsy and I needed a new network card anyway so I just got a new D-Link.  I set everything up following the tutorial on the NDISwrapper website and can't get the final step to work...connecting to the network on boot.  I first added 'ndiswrapper' to /etc/modules and it doesn't connect on boot.  I then wrote a little script that goes like this...

```

#/bin/bash
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key restricted 910d349a0db11bb0067bdc3a04
sudo iwconfig wlan0 essid TonyDebbie
sudo dhclient wlan0

```

It's called runnetwork.sh and I just manually run that when my computer boots up. The only problem with the script part is that I can't add it to my sessions because a password is required to run root commands so it fails to issue the commands.   If anyone has any information on getting the network to connect on boot please reply with some advice.  Thanks.

---

### Post by ddrichardson on 2007-11-01
Can it not just be added to the init scripts to be executed at boot?

---

### Post by Hyperkill on 2007-11-03
Good question.  I don't know since I'm pretty new to Linux still.

---

### Post by charles woodward on 2007-11-03
There is a problem relating to wireless networks - and there are a number of threads on this very subject.   

There are two possible solutions you should try before anything else.

1.  edit your /etc/sysctl.conf and add the following lines :

net.ipv4.tcp_sack=0
net.ipv4.tcp_window_scaling=0

save the file, then try rebooting (you will probably have to edit the file as `sudo`.

If that fails you can try modifying your /etc/dhcp3/dhclient.conf file and add the following line (there is a similar line that is commented out in that file).

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

then save the file and reboot (or restart the network).

One of those two commands worked for me after a weeks of no internet (and I've been using Unix/AIX/Linux for twenty years).

This may not be the cause of your problem, but so many people are having difficulty connecting to the networks, and these are the two most promising solutions offered by others in various threads.

Hope you get it working soon

---

