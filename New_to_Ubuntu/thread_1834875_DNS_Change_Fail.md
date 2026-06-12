---
title: "DNS Change Fail"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by bilkenter on 2011-08-28
Hi,

Although I edit /etc/resolv.conf in order to change DNS servers, when I restart my computer, resolve.conf backs to default setting.

What should I do to edit it permanently?

Ubuntu 11.04, Gnome 2.3, Kernel 3.0.2

Thanks

---

### Post by Actonix on 2011-08-28
You can make use of a DNS other the default provided by your DHCP router by having different connections.

For instance, if you already have  connection called "Auto eth0" create another called "Auto eth02" or use any other naming convention that best assists you in identifying your various connections.

To do so Open up connections Manager (Edit Connections) and Add another connection - under the IPV4 tab, instead of "Automatic (DHCP)" set it to use "Automatic (DHCP) Address only", that enables you to input the DNS server(s) you wish to use against the  DNS Servers field, if more than one use a comma to separate it from the other  - save and reconnect with the new connection setting.

if that does not work for you it might be that there are other entries your router requires you to provide - like your mac address which you can simply copy from the original connection that is known to work.

You could set a connection up to use Norton DNS as your server for a sort of test connection as returning to their site will let you know if it is in working for you.

---

### Post by HereInOz on 2011-08-28
If you are running Network Manager, it will overwrite anything you put in resolv.conf.  You need to make the change in Network Manager:

System > Preferences > Network Connections. 

Then edit the relevant connection, changing the IPv4 settings to Automatic (DHCP) Addresses only, or Manual if you want full manual address configuration, then entering the DNS server(s) of your choice.

If you want to use resolv.conf for DNS, and /etc/networking/interfaces to configure a static IP setup, you need to uninstall Network Manager.

---

### Post by bilkenter on 2011-08-28
Than you very much both. 
Solved.

---

