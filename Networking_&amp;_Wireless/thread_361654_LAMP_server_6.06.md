---
title: "LAMP server 6.06"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by blx_286 on 2007-02-14
I need some assistance with my LAMP server 6.06. I have two problems that appear to be related. After installing the server, I installed the Gnome desktop with ```
sudo aptitude install ubuntu-desktop
```

If I issue any of the following commands, it wants to uninstall the Gnome desktop.

```
sudo aptitude install gcc
sudo aptitude install build-essential
sudo aptitude install linux-headers-2.6.15-26-386
```

I wasn't paying attention the first time it asked and I uninstalled Gnome. So now that I have Gnome reinstalled, I want to install VMware Tools and Webmin. Can someone point me in the right direction?

Thanks,
Tim

---

### Post by blx_286 on 2007-02-14
Update:

Not sure why I couldn't install those in terminal, but I was able to with Synaptic.

---

### Post by ciscosurfer on 2007-02-14
> **blx_286 said:**
> I need some assistance with my LAMP server 6.06. I have two problems that appear to be related. After installing the server, I installed the Gnome desktop with ```
sudo aptitude install ubuntu-desktop
```If I issue any of the following commands, it wants to uninstall the Gnome desktop.

```
sudo aptitude install gcc
sudo aptitude install build-essential
sudo aptitude install linux-headers-2.6.15-26-386
```I wasn't paying attention the first time it asked and I uninstalled Gnome. So now that I have Gnome reinstalled, I want to install VMware Tools and Webmin. Can someone point me in the right direction?

Thanks,
TimThe ubuntu-desktop package is a meta package and can be removed safely; remember to reinstall it when you make any major upgrades, etc.

This link should help with VMWare tools >> [http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/](http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/)

This link should help with installing Webmin (it is actually a Howto on installing a server environment, but will discuss installing Webmin as well) >> [http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)

Good Luck!

EDIT: Unless you've specifically added a Webmin repo to your /etc/apt/sources.list and then updated the list, Webmin shouldn't appear in Synaptic.

---

