---
title: "auto configuring usb0 on hotplug"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by nascent16 on 2007-06-28
Whenever I plug my usb pda into my computer (running ubuntu 7.04), it's supposed to auto detect the hotplug event and statically configure usb0. It will work once, but never again. After the first time, it detects that there is a new network interface and it shows up in ifconfig as usb0, but it does not apply the static settings. Does anybody know why this is? I saw something about network manager perhaps interfering, but uninstalling network manager did not help the problem. Any ideas?

/etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

auto usb0
iface usb0 inet static
address 192.168.2.100
netmask 255.255.255.0
broadcast 192.168.2.255

---

### Post by cgirda on 2007-07-20
Try this..

 1>  Edit  the file "/etc/udev/rules.d/85-ifupdown.rules"
     
      Comment out the to ACTION  lines and add the following 2 lines below the commented lines

     ACTION=="add", RUN+="/root/myifup $env{INTERFACE}"
   ACTION=="remove", RUN+="/sbin/ifdown $env{INTERFACE}"

 2>  Create  a fie  " /root/myifup ",  with the following entries. 

       #!/bin/sh
         iface=$1
          ifdown $1
         ifup $1
         exit $?

   Re-boot the machine and you should be in business.

---

### Post by bwakkie on 2008-04-18
I tried this and it wasn't a very good idea to use on Hardy. 10th of thousands udev error messages it will give. YOu are warned

---

