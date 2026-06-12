---
title: "changing mac address no connection"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by highcliff on 2007-08-02
I use ubuntu 7.04 with D-Link wireless and i connect to open & WEP network normally but when i change the mac address with any method i can't connect again althought i do every thing like restarting the network or dhclient unless i reboot and the mac go back to the original one,any friend  here can help.thank to the sweet ubuntu and who use it.

---

### Post by kevdog on 2007-08-02
How are you changing the MAC address??? Is this with a wired or wireless card?? Why do you need to do this anyway?

---

### Post by highcliff on 2007-08-03
Thank you,i change mac for wireless card, some networks  use mac filtering  so i must change it to specified one.
I use macchanger or : ifconfig ath0 hw ether 00000000000
and befor doing this i stop ath0: ifconfig ath0 down then do all the procedures to get the interface and network up but i cant make any connection with that network.

---

### Post by noob12 on 2007-08-03
Too spooky sorry.

---

### Post by kevdog on 2007-08-03
Are you running this command at the command line like the following:

```
sudo ifconfig ath0 hw ether xx:xx:xx:xx:xx:xx
```

or in the format like you are stating

> ifconfig ath0 hw ether 00000000000

Just want to know that your trying the MAC address spoofing on the command line rather than in the /etc/interfaces/file.

Similar to
```
sudo ifconfig ath0 down
sudo ifconfig ath0 hw ether xx:xx:xx:xx:xx:xx up
sudo dhclient ath0
```

---

### Post by highcliff on 2007-08-03
Thank you kivdog for your patience ,i use the accurate commands:
```
sudo ifconfig ath0 hw ether xx:xx:xx:xx:xx:xx
```
and also change /etc/interfaces exactly as you write(i get them from ubuntu forum while searching for my problem)
by the way if change /etc/interface with new mac and reboot then use ifconfig ath0 , i found the old mac!

---

### Post by kevdog on 2007-08-03
Can you post your /etc/iftab file -- wondering if that is screwing it up.

---

### Post by highcliff on 2007-08-04
this is out of /etc/iftab:

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:f2:9e:ba:c0 arp 1
ath0 mac 00:17:9a:bd:ed:31 arp 1
```

these are original mac addresses with out changing (when reboot)
and i think you approach the solution

---

### Post by kevdog on 2007-08-04
Remove or comment out the ath0 entry and then repeat the steps.  Maybe this will work

---

