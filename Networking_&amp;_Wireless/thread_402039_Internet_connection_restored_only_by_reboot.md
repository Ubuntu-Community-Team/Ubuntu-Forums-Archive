---
title: "Internet connection restored only by reboot?"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by sica07 on 2007-04-05
Hello everybody,
I have a little network with a Ubuntu Edgy server. I have two problems wich I can solve. The first problem when it happens that  the connection to internet drops down (poor services form the ISP) the only way I can restablishe it, is rebooting the server. Another problem is that, if I restart the network service (/etc/init.d/networking restart) the computers in the network loose the contact with the server (no more internet and file share).  Before Ubuntu I had installed Fedora and there was no such problems. I made the same configurations in Ubuntu, but the resultes are not the same. Pls help (and excuse my bad english). Thanks

---

### Post by dannyboy79 on 2007-04-05
when internet drops, is this due to your connection to the isp goes down, or is this just the server internet doesn't work? what is the router's ip address? what is the output from the following commands:

sudo cat /etc/resolv.conf

sudo cat /etc/network/interfaces

sudo cat /etc/dhcp3/dhclient.conf

dmesg | grep eth

lscpi | grep Ethernet

also, when you lose internet access, can you still ping [www.gogle.com?](www.gogle.com?) you should never have to restart the server just to get internet access back up. the 2 commands that will do are 

sudo /etc/init.d/networking restart

and

sudo ifdown eth0

then

sudo ifup eth0

(NOTE: you would replace eth0 whatever your interface name is, maybe it's eth1 or wlan0 or ath0.)

---

### Post by sica07 on 2007-04-06
Thanks a lot for your reply dannyboy79  but I found out that I can restart the connection with the /etc/init.d/dial restart command. The only problem that I have now, is with the /etc/init.d/networking restart as I mentioned in my first post. Any ideas about that?

---

### Post by dannyboy79 on 2007-04-06
ok, you're using dial up? i didn't know that. the networking has to be run after the dial command and it's probably not set that way. so what is the output from this command

ls -la /etc/init.d/

the number for dial should be LOWER than the number for networking otherwise your networking can't configure itself because there's not a connection made. I don't have any experience with dial up and linux but I am just using logic here so hopefully I am right. 

UPDATE: after I wrote all that, I found a great guide for ya but I didn't want to just erase the above in case it was useful as well. here you go: [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by sica07 on 2007-04-06
Well, i am not having a dial-up connection, but a pppoe via ADSL connection, so the link is not helping me very much, BUT, the idea about starting the dial service before networking may work, I will try and I will let you know. Thanks for your help!
P.S If it helps, I used this link to setuip my conection: [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

---

