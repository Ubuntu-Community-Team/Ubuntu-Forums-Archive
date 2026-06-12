---
title: "Ubuntu 14.04 to Ubuntu 14.10 Network-Manager fails to start on boot"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by sean84 on 2015-03-01
I recently upgraded from 14.04 LTS to 14.10. Since the upgrade, the Network-Manager service fails to start on boot. I have checked the syslog and noticed the following errors.

nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
NetworkManager[3258]: <warn> Dispatcher script failed: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
ntpd_intres[1617]: parent died before we finished, exiting

I am able to start the network if I enter the following commands:

sudo service network-manager start
sudo initctl emit static-network up

Based on other forum posts and what I've found myself, the Network-Manager service fails to start because static-network-up fails to start. Based on the file /etc/init/network-manager.conf, there is a condition in the "start on" section that is contingent on static-network-up starting. However, I'm unable to figure out why this service is not starting.

Any help is greatly appreciated.

---

### Post by sean84 on 2015-03-05
This seems to be a common issue with Ubuntu 14.10. Has anyone been able to resolve the problem?

---

### Post by atluxity2 on 2015-04-21
I recently upgraded as well, and is experiencing the same issues you describe, and find the same in my logs. Currently debugging. Did you find anything?

---

### Post by atluxity2 on 2015-04-21
I have tried reinstalling network-manager, I had "no-auto-default" on my eth0-mac in /etc/NetworkManager/NetworkManager.conf, but commented that out, no change...

---

