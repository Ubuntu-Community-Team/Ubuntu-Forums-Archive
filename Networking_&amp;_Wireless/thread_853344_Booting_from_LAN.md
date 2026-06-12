---
title: "Booting from LAN"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by fadelvato on 2008-07-08
Hi , i have access to two laptops running Hardy/Gnome (Compaq Presario and Sony Vaio), and my cd drive in the Presario is broken ,so i was wondering if it is possible to boot from LAN (i have a Huawei hg550 router with two ethernet ports) , i want to use the CD Drive in my Vaio to install Kubuntu 4 in the Presario .
and i was wondering how could that be done ? do i need to establish a complicated LAN, or is it a simple operation ?
Ps: both computer support the boot from Lan and the PXE protocol .
i'm available to interact and provide any extra data . Thanks in advance :)

---

### Post by fadelvato on 2008-07-08
Bump :(

---

### Post by bluefrog on 2008-07-08
search the wiki for netboot.

well just read again the wiki. it a bit overcomplicated but it should work.

the easy way is:

install tftp-hpa
sudo cp -R netboot/* /var/lib/tftpboot
chown -R nobody:nogroup /var/lib/tftpboot

need to install and tweak a dhcp server
install dhcp3-server
edit /etc/dhcp3/dhcp.conf
you will need something similar to the following: (adapt to your network, my dhcp server has IP 192.168.1.20)
subnet 192.168.1.0 netmask 255.255.255.0 {
  range dynamic-bootp 		192.168.1.150 192.168.1.200;
  option broadcast-address 	192.168.1.255;
  option routers 		192.168.1.20;
  allow 			unknown-clients;
  use-host-decl-names		on;
  filename "pxelinux.0";
  next-server 192.168.1.20;
}

---

