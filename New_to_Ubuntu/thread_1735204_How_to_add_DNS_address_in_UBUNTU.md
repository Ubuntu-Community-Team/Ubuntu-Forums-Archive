---
title: "How to add DNS address in UBUNTU"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by honey_bee on 2011-04-21
Hi,
       I am using UBUNTU 10.10 I have manually assign IP address in
/etc/network/interface

Now I want to add DNS ip addresses. Please guide me the file in which I may add the IP address of my name server or the GUI interface to add it quick

honey

---

### Post by mikewhatever on 2011-04-21
I think DNS addresses should go into /etc/resolve.conf.

---

### Post by spikoley on 2011-04-21
Below are directions to set you DNS from OpenDNS.  Just change the IP addresses to whatever you want.

[From]("https://store.opendns.com/setup/device/ubuntu/")
> 8. NOTE:
To avoid having your settings get revoked after reboots, or after periods of inactivity, you may need to make the following changes via the command line:
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# add the following line to the document before the 'return subnet-mask' command
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0
You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

