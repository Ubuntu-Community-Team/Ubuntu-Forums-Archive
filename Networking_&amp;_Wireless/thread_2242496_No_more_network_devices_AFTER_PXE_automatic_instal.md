---
title: "No more network devices AFTER PXE automatic installation"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by yzord2 on 2014-09-02
I have a problem with an automatic installation of Ubuntu server on a  VM. The problem is that after installation and reboot the VM gets the IP  which it gets from the DHCP instead of using the static IP which has  been set in the preseed. I tried several methods and configs, but it  keeps holding it's DHCP IP. Apparently it does not config the network in  the preseed phase. It looks like it is ignored during installation. Of  course i could edit the network afterwards, but that's not the purpose  of an automatic installation.

The VM gets his IP from the DHCP  and loads the ipxe.php. It checks which image it should get but it fails  right away with the following

[[IMG]http://s27.postimg.org/s4chme5of/Schermafbeelding_2014_08_27_om_13_00_02.jpg[/IMG]]("http://postimg.org/image/s4chme5of/")

Please notice that this didn't happen when it was a clean VM during installation. This all happens after the installation was a succes and reboots the server. I guess something is not right in the ipxe.php, but my Linux skills are very limited and still learning all this. I have attached the ipxe.php (which is a txt file here) and was hoping someone could point me to the right direction.

---

