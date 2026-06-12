---
title: "[SOLVED] Static IP Address Problems"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by bren21 on 2008-07-22
Whenever I try to configure a static ip address I can not connect to the internet. I am connecting with wireless to a wpa network, and put in the following information:

Configuration: Static ip address
ip address: 192.168.1.136
subnet mask: it does this for me
gateway address: 192.168.1.1

The ip address and gateway address both worked fine under windows on the same computer, and the roaming option works fine. Any reason why a static ip wont work?

---

### Post by rbc on 2008-07-22
Are you trying to set the static IP while connected wirelessly to the router? If so, try wiring to the router, then change the wireless NIC to static, then unplug the wired connection. No promises, but it worked for me

---

### Post by prshah on 2008-07-22
> **bren21 said:**
> 
and put in the following information:
Configuration: Static ip address
ip address: 192.168.1.136
subnet mask: it does this for me
gateway address: 192.168.1.1


You probably need to restart networking after making the config changes; open a terminal (Applications-Accessories-Terminal) then give the command```
sudo /etc/init.d/networking restart
```

---

### Post by bren21 on 2008-08-09
Neither of these worked for me, and yes I am connecting through wireless.

---

### Post by caljohnsmith on 2008-08-10
I think I remember there being issues using WPA with a static IP address and Ubuntu's Network Manager. Try turning off WPA in your router and see if you can connect with a static IP and no encryption. If you can, maybe give the [WICD network manager]("http://wicd.sourceforge.net/") a try since I think it has less issues with static IP + WPA.

---

### Post by bren21 on 2008-08-13
Excellent! Wicd worked perfectly for me, I wish I had found out about it earlier. Thanks a lot caljohnsmith

---

### Post by Sct_Plt on 2008-08-18
Hope you folks don't mind me jumping in,, but I've got the same problem stated in the original post.  I worked on it for 2 hours yesterday, but could not get the NIC to accept a static address using the Ubuntu networking applet. The WRT54G is doing the DHCP, but I like to run the wired resources with static IP. The printer and NAS work fine, but using a default router config with no static addressing - I couldn't get it to accept the static address on the workstation NIC. Roaming mode and the "automatic mode DHCP" work great. I'll suck up DHCP address from withing the DHCP block no problem - but NO luck with just sticking in a static address on the NIC. There's no wireless connection for the workstation. I tried the networking restart with no luck.  Is this a documented problem in the kernel?

---

