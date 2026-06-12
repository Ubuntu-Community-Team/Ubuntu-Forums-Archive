---
title: "isc-dhcp-server not starting on reboot"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by Doug_Kelley on 2013-11-06
Hi everybody--
I've set up my machine (Ubuntu 12.04 LTS) as a gateway with isc-dhcp-server, which happily assigns IP address to other machines on the local network. This is great. And of course I want it to continue automatically when the gateway restarts. So I've run
sudo update-rc.d isc-dhcp-server defaults
That produces a warning about missing LSB information but seems to run successfully. Sadly, after a reboot the service doesn't start. To be precise, "ps -e | grep dhcp" returns nothing and other machines on the network get no addresses until I manually run 
sudo service isc-dhcp-server restart
Are more steps required? Thanks in advance!

---

### Post by SeijiSensei on 2013-11-06
Ubuntu has moved pretty much all daemons to the Upstart system.  The commands like "service" are pretty similar to those used to manage daemons on RedHat systems.  For details, see [http://askubuntu.com/questions/19320/recommended-way-to-enable-disable-services](http://askubuntu.com/questions/19320/recommended-way-to-enable-disable-services)

---

### Post by Doug_Kelley on 2013-11-07
Thanks SeijiSensei! I read up on Upstart and eventually came to [this thread]("http://askubuntu.com/questions/62812/why-isnt-my-upstart-service-starting-on-system-boot") about a similar issue. Following along, I edited /etc/init/isc-dhcp-server.conf by changing "start on runlevel [2345]" to "start on filesystem and net-device-up IFACE!=lo". That fixed my problem.

---

