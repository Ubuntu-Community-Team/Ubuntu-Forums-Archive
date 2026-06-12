---
title: "Networking connections don't connect to the internet, are slow, and drop connection"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by l6griffin on 2015-12-20
This maybe a case of a little knowledge is dangerous. I have an HP2000 laptop running 15.04 the network work till I added a hotspot. There are 3 connections eth0, wifi, and hotspot. I tried to correct the problem but think I only messed things up worse. If there is away to delete everything and start over I would. I followed the sticky but on the dist-upgrade it failed on a unrelated (bug filed) problem. I can be reading messages and click on the next only to get server not found, then click refresh to have it load. The wireless info tar file should be attached.

---

### Post by Hadaka on 2015-12-20
Hi,first uncheck anything you have checked for "hotspot"
proxy server,shared...whatever. then please copy and paste one command at a time...
```
sudo cp /etc/network/interfaces /etc/network/interfaces.old
```
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
the do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
*next remove the usb stick
you can only have one...not both...choose...
##### network managers ##################
Installed:
    NetworkManager
    Wicd
Boot and test.

---

### Post by praseodym on 2015-12-20
Hi,

put the /etc/network/interfaces back to normal:

```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Obviously, your time zone is LA?! If so, correct the country code settings:
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot. Both network-manager and Wicd are installed. Choose one of them.

Edit: Hadaka was faster

---

### Post by l6griffin on 2015-12-20
Hadaka, I'm not sure what you mean "uncheck anything you have checked for "hotspot"
proxy server,shared...whatever", delete all the hotspot connections?

Working on the rest.

Thanks for the effort [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") :)

I executed all the commands, then deleted all the hotspot connection, and rebooted. After booting up I was connected to the eth0 (DLINK) with no Internet access. A new connection was created for the hotspot, auto ethernet. When I connect to auto Ethernet I have internet access. I'm not sure how well it is working yet, hopefully I can work with it till I get upgraded to 15.10. When I get 15.10 installed then I'll mark this post solved and  open another 15.10 problems. Thanks till then folks.

---

### Post by l6griffin on 2015-12-23
Just finished upgrading to 15.10, My network connections were good enough THANKS. It took 21-22 hours. I'll mark this thread solved.

---

### Post by Hadaka on 2015-12-23
Glad to hear !

---

