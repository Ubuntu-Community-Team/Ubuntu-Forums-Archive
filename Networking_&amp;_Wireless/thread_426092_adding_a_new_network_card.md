---
title: "adding a new network card"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by blackmesaU on 2007-04-28
my onboard lan is doing funny things, such as it will obtain a dhcp address and will work for 5 minutes then will not respond to pings or connection attempts. i tried a staic address but that gives no connectivity.

i have now disabled the on-board nic in the bios and added a 3com 3c905c pci card. now eth0 will not come up, the new card is there listed if i do an lspci command. any pointers as to what i need to do..

---

### Post by chili555 on 2007-04-28
The file */etc/iftab* associates interfaces, such as eth0 with MAC addresses. Yours probably lists eth0 as bound to your old, now disabled, ethernet adapter.

After backing up the current file:```
sudo cp /etc/iftab /etc/iftab.bak
```I suggest```
sudo gedit /etc/iftab
```Remove the entire eth0 line. Save and close gedit. Reboot and see if eth0 has reappeared.

---

### Post by blackmesaU on 2007-04-28
thanks for the reply. tried that but it eth0 does not reappear, is there an easy way of finding out the mac address from ubuntu? i guess i could edit this file manually?

---

### Post by chili555 on 2007-04-28
I think this card works with the module 3c59x, so let's try:```
sudo modprobe 3c59x
```Then see if eth0 has reappeared. It may stick through a reboot, but if not, *sudo gedit /etc/modules* to add:```
alias eth0 3c59x
```Please let us know.

---

### Post by blackmesaU on 2007-04-28
that did not work. does not appear after those steps. :(

---

### Post by chili555 on 2007-04-28
May we please see```
sudo lshw -C network
```Thanks.

---

### Post by blackmesaU on 2007-04-28
buffer i/o error on device hda, logical block 0
*-network disabled
desc ethernet interface
product 3c905c-tx/tx-m
vendor 3com
physical id 7
bus info pci'03:07.0
logical name eth0
version 74
serial 0050da371c21
size
capacity
width
clock
capabilities
configuration: autonegociation=on bcast=yes driver=3c59x duplex=half link=yes mutlicast=yes port mII speed 100mb/s
resources


If you need the blanks let me know as i had to type it out.

HTH

---

### Post by chili555 on 2007-04-28
> *-network disabled
desc ethernet interface
product 3c905c-tx/tx-mDisabled? I wonder how or where or why. You might have another peek in the BIOS to see if there is any setting that may give preference to PCI cards for network, rather than built-in. You might also see if you can move the card to another slot.

Also, take a look at:```
dmesg | grep eth0
```See if it holds any clues as to why this simple card doesn't just leap to life.

Also, look at:```
sudo ethtool eth0
```See if it tells us anything valuable. I might be very interested in whether it detects a link, suggesting integrity, or lack thereof, of the cable and router.

---

