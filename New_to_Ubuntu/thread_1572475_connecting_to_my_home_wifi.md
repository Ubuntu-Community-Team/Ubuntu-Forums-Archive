---
title: "connecting to my home wifi"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by kwisj on 2010-09-11
Hi Guys
I'm have a question about connecting to my home wifi network. I'm using ubuntu 10.04
Its running on windows virtual pc which is runnning on a vista home premium 32 laptop.
It wont connect to my home wifi. (It does connect via an ethernet cable, no probs).
I have a similar set up running on a netbook XP machine and it connects fine with no configuration required apart from the wep key.
Can anyone tell me how to configure the wi fi? I have followed the help file but fall at the first hurdle as it does not detect any wifi networks!
I have gone to network connections and i get the ''auto eth0'' wired connection, but in wireless i get nothing. I have a Broadcom 802.11b/g card.
thanks for you time
Kwisj

---

### Post by rory526 on 2010-09-11
Oh... I have had similar problems. I don't think all Broadcom wifi cards are well supported. Could you give us the full model number please?

also, try
```
ifconfig -a
```

which will list all interfaces including those that are down.

---

### Post by kwisj on 2010-09-11
Hi thanks for the reply. 
I think I may have sorted out the problem: it was to do with not having the network adapters section in VPC properly configured. It only had the the LAN card included in the networking section by default. I set the number of network adapters to 2 and selected the broadcom wlan in the dropdown menu. Now it seems to be OK. However in networking icon in the top left area of ubuntu, next to the clock it still says that it is a wired connection auto eth1. (auto eth0 was the original wired connection that i was using) In the network connections display it is not registering that it is using a wireless network. which could prove tricky in the future.
BTW this is what  got for the di of the broadcom card? PCI\VEN_14E4&DEV_4315&SUBSYS_1508103C&REV_01
PCI\VEN_14E4&DEV_4315&SUBSYS_1508103C
PCI\VEN_14E4&DEV_4315&CC_028000
PCI\VEN_14E4&DEV_4315&CC_0280

Do you think its kind of fixed or does it need to to be configured further?
PS i've attached some screen shots so you can see what's going on
cheers
Kwisj

---

### Post by rory526 on 2010-09-11
I'm sorry, I missed that you were running Ubuntu on a virtual machine. I haven't any experience with VPC unfortunately. Maybe this might help:

[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004#Network%20Card](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004#Network%20Card)

Also, you could try connecting to your wireless network through the command line.

This should list nearby wifi networks.
```

sudo iwlist eth1 scan

```

The following commands are for use with WPA or WPA2 networks. Please replace the items in angle brackets with the appropriate content.
```

sudo wpa_passphrase <network_name> <password> > /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i eth1

```

And this command will connect you to the network if it uses dhcp.
```

sudo dhclient eth1

```

---

