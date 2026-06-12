---
title: "virtual appliance: how to set dhcp or static ip"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by aktxyz on 2007-01-25
We currently package our software solution as an appliance.  When a customer buys our solution...

- they get a rack mount machine
- running ubuntu server (no X)
- there is panel on the front of the machine to setup dhcp or static IP

The customer never logs into the box, everything is done thru a web based management UI.


SOOOOO ... we want to do the same thing with a Virtual Appliance, basically Ubuntu Server running inside of VMWare.  The BIG PROBLEM is that there is no physical panel on the front of  the device, so how to set the network up (DHCP or Static IP).

Our customers are not that savvy, and we really don't want to have them need to use ssh, login, and run a script or whatever.  We could always set it up for them initially, but if they change subnets or switch from DHCP to Static, we don't want to be the getting factor for them to make that change.

Ideally, the experience would be something like this...
- install vmware
- install our vmware image
- start vmware
- automatically tries to get a DHCP address
- IN PLACE OF THE LOGIN prompt, there is a little menu
  1 - use static ip
  2 - use dhcp
  3 - shutdown
  4 - reboot

Any ideas ???

Thanks

---

### Post by cyan.ogilvie on 2008-01-26
I had exactly the same requirement and found your post looking for something to do just that.  Well, after some more searching I found nothing so I rolled my own.

You're welcome to use it if you like (I'd appreciate feedback and bug reports, as it's brand new):

```
wget -c http://packages.codeforge.co.za/ubuntu/dists/gutsy/main/binary-i386/applianceconfig_1.0-1_i386.deb

sudo dpkg -i applianceconfig_1.0-1_i386.deb
sudo reboot

```

It assumes the network interface to manage is eth0.  I've tried it on some of my virtual machines (Ubuntu server 7.10, running in VMware Workstation 6.0.2) and they seem to work fine

---

