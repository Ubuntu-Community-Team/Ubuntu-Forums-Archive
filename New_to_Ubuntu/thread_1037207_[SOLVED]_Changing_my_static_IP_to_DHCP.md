---
title: "[SOLVED] Changing my static IP to DHCP"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by JDnomad on 2009-01-11
I installed Ubuntu on my dual boot w/vista system.  All is going well except for my network connectivity.  I am using a wired lan connection to my ISP.  I have to visit a static page then log on to my account before being granted a connection.  My IP address, netmask, gateway and DNS server info stays static.  I changed this info using the gui, yet when I re-boot it resets itself to DHCP. 

thanks for any ideas!

---

### Post by JDnomad on 2009-01-11
Disregard, I think I found the answer in another thread..

---

### Post by jgoguen on 2009-01-11
Did you create another Ethernet definition in NetworkManager?  If this computer is to be used in more than one place, that may be the best option.  You'll probably have to choose your Ethernet definition every time though.

If this computer is only used with this connection, you could try using the interfaces file.  This will stop NetworkManager from managing the interface and force a static IP address.  To start, open /etc/network/interfaces to add the new definition.  Press Alt+F2 and enter this command:
```
gksudo gedit /etc/network/interfaces
```Enter your password when prompted, and your interfaces file will open.  You probably only have two lines in there:
```
auto lo
iface lo inet loopback
```Leave those as they are, and put this right below it, with one blank line between the sections:
```
auto eth0
iface eth0 inet static[INDENT]address <your static IP address>
netmask <your subnet mask>
gateway <your gateway>
broadcast <your broadcast address>
[/INDENT]
```Watch for blank lines, there should be none.  This section and the first two lines that were there before should have a blank line between them.  Save this file and exit gedit.  Now, press Alt+F2 again and use this command to start editing DNS definitions:
```
gksudo gedit /etc/resolv.conf
```The lines beginning with **nameserver** are the ones that point to DNS servers.  Change the first ones to your DNS server IP addresses, and remove any that are left over.  Save this file and exit gedit.  Now, you can either reboot (preferred, since this will verify that it works after a reboot) or open a Terminal (Applications -> Accessories -> Terminal) and enter this command to reset networking:
```
sudo /etc/init.d/networking restart
```You should now have a static IP set on eth0, and this should persist across reboots.

---

