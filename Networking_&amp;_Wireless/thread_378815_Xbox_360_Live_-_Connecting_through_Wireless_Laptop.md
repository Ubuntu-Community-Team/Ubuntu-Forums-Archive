---
title: "Xbox 360 Live - Connecting through Wireless Laptop"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by th0r0n on 2007-03-07
Hi,

Basically, when I was running windows, I used to be able to used Xbox Live this way:

Plug my Xbox 360 into the Ethernet port of my Laptop with a CAT5 Cable

Enable ICS on my Wireless connection on the Laptop

This allowed me to use my laptop to connect to Xbox Live

Has anyone done this on Ubuntu? 

I am using Xubuntu if that makes any difference.

Thanks,

T

---

### Post by spd106 on 2007-03-08
Have a read through this wiki page [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

I suggest that you use firestarter as it's probably the the most user friendly way. There are limitations especially as UPnP support is rather tricky and will require more research.

---

### Post by mrsudo on 2008-03-05
this may be a really stupid question but......

this would hypothetically work on a desktop with a seperate wireless card, n'est pas?

---

### Post by Istonian on 2008-03-10
I am having the exact same problem as th0r0n. Firestarter isnt working right. Is there another way?

---

### Post by darkmdbeener on 2008-03-10
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

how do i undo what i did in this tutorial

im trying to use firestarter for this instead sence it didnt work and now its saying that eth0 isnt active and i set it already to dhcp in the network settings

---

### Post by amainejr on 2008-03-22
I've done it a while back.  Here's what I remember.

1) you want to check your network configuration.  You're looking specifically for your ethernet(usually eth0) and wireless(wlan0) settings, but this command will show you everything.
    ifconfig

2) you want to set the ethernet cards network address to something on another section than your wireless.  Ex:  My wireless card is set by DHCP to 192.168.2.1, but i've got the ethernet card set to 192.168.3.1.
    ifdown eth1     /*shut the eth1 network down*/
    ifconfig      /*verify that it is down*/
    ifconfig eth1 192.168.3.1     /*set the eth1 ip address AND RECORD IP*/
    ifup eth1     /*bring it back up*/

3) now set it up to run at boot, edit the rc.local file with the following information.
     sudo gedit /etc/rc.local

     ifconfig eth0 up
     ifconfig eth0 192.168.3.1
     echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth1 -s 192.168.3.1/24 -j MASQUERADE
     exit 0

4) if i remember right, you have to set your wireless card to promiscuous mode, then reboot
     ifconfig wlan0 -promisc
     reboot

Now, you have to manually edit your 360 network and ip settings.  I know the IP has to be within the 192.168.3.x range, just can't have duplicate IP's on the same network.  Can't remember the subnet mask, maybe 255.255.255.0.  The gateway should be what you set the ethernet card to (192.168.3.1).  And I don't remember any other settings within the xbox itself.  Hope this helps a bit.  If I find anything on the internet, I'll be sure to forward the link.

---

