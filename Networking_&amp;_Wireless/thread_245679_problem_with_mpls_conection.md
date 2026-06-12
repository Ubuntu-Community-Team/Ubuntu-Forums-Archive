---
title: "problem with mpls conection"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by dids22 on 2006-08-28
hey
my internet use mpls so all i need to configure the internet was to select in the sitting of my lan card and choose DHCP

recently when i getin to ubuntu i cant use the internet(again, i have mpls so i dont need to conect)

i write "ifconfig" in teminal ad i see that the card dont get ip
therefore, i need go to system->adminisration->networking 

and disable the card, able the card and i can use the internet(the card get ip address)

how can i fix it? that i dont nedd to disablr and anable and all this ?

thnks

---

### Post by dids22 on 2006-08-30
no one know?:(

---

### Post by Original Brownster on 2006-08-30
Hi,
Did it work with Ubuntu before and if so when did it stop working, coincide with upgrade?
Check your logs for any clues:$ dmesg | grep eth0
assuming your card is eth0
If the card is being identified at boot and a driver loaded I wonder if it's a time out issue waiting for your router/modem, are they left on, not a usb device is it?
Rather than disabling/enabling the card try running: $ sudo /etc/init.d/networking restart
This will re-run the scripts to bring down and bring up interface only. 

It's a strange problem, I hope the above helps a bit.

> **dids22 said:**
> hey
my internet use mpls so all i need to configure the internet was to select in the sitting of my lan card and choose DHCP

recently when i getin to ubuntu i cant use the internet(again, i have mpls so i dont need to conect)

i write "ifconfig" in teminal ad i see that the card dont get ip
therefore, i need go to system->adminisration->networking 

and disable the card, able the card and i can use the internet(the card get ip address)

how can i fix it? that i dont nedd to disablr and anable and all this ?

thnks

---

