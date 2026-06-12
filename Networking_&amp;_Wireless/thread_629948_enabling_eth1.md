---
title: "enabling eth1"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2007-12-02
Hi,
I'm trying to configure Firestarter on Ubuntu 7.1.0. The setup wizard sees both my NIC connected to my DSL modem (eth0) and my lan NIC (eth1). It has allowed me to access the Internet (though it's been a problem and I don't have Firestarter running now)  but 

it will sometimes "fail to start" and claim "the device eth1 is not ready".

Running route in terminal returned info on eth0 and ppp0 but not eth1.

Running dhclient eth1 showed me DHCPDISCOVER attempts which ultimately ended with no DHCPOFFERS received; no working leases etc.

Devices/Network Tools currently has eth1 configured with a static ip address of 192.168.1.111 subjet mask of 255.255.255.0 and gateway of 192.168.0.1 - I've also tried running it as on automatic config for dhcp with the same results.

Is it something obvious I'm doing wrong? By the way, should I be rebooting when I change the configuration in network tools.

Thanks a million!

David

---

### Post by kevdog on 2007-12-02
No reboot needed, however I suspect you want to use these interfaces independently and not at the same time. First bring both interfaces down:

sudo ifconfig eth0 down
sudo ifconfig eth1 down

At this point do you need a different routing statement??

Then bring up whatever interface you need

sudo ifconfig <interface> up

Are you keeping your settings in the interfaces file??  If so, rather than the above statement you might want to try
sudo ifup <interface>

The difference in these two statements is that ifup reads the interfaces file and brings the interface up according to what is listed, whereas ifconfig is lower level and simply brings up the interface without any specific configurations.  (ifup calls ifconfig)

Not sure if any of this helped you.

---

### Post by dbclinton on 2007-12-02
Thanks. I'll give that a shot next time I boot Ubuntu. By the way, if this does enable eth1, will these commands change the boot sequence as well so I don't have to do this manually every time?
Thanks,

---

### Post by kevdog on 2007-12-02
Hmm thats a good question -- I doubt it.  We might have to alter some files to switch the interface names eth0 and eth1 as they relate to the specific MAC address of the card.  

Lets just see if everything works first and then we can solve that problem later.

---

### Post by dbclinton on 2007-12-04
Hi,
I successfully brought eth1 down with sudo ifconfig eth1 down, but enabling it with ifconfig eth1 up was unsuccessful (Firestarter and network devices still couldn't make use of it). 
I then tried ifup eth1 and received the message:

SIOCADDRD: No such process
Failed to bring up eth1

Once I disabled eth0 (my DSL connection) and enabled eth1 (my LAN connection) the eth1 appeared to come to life - but I then couldn't start eth0. Is it possible they're somehow conficting with each other?

With thanks,
David

---

### Post by kevdog on 2007-12-04
Are you trying to bring them up on different subnets or the same subnet?

---

### Post by dbclinton on 2007-12-04
I'm not sure. Should they be different?
I'll take a look later.
Thanks so much!
David

---

