---
title: "netgear wireless usb wg111v2. edgy trouble. help required."
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Staff on 2007-08-29
i had dapper drake and internet working on that using negear wg111v2 but when i upgraded to edgy it wont connect. i was using ndiswrapper on dapper. during ( or possibly just after... im not sure ) my edgy upgrade this message appeared

 'some third party entrties in sources.list were disabled. After upgrade, you can re-enable them with 'software properties' tool or with synaptic'.

 im not sure if this has anything to do with it. when i go onto system, administration, networking, there is no wireless device. there was one in dapper. when i enter the command 'ndiswrapper -l' ( lower case 'L'), it shows:

installed ndis drivers
net111v2                                               divers present, hardware present

according to every other thread i have looked in, i should be able to connect. i have blacklisted the following:

blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
blacklist r8187
blacklist bc3m43xx

i really dont know what to do. Im rather new to ubuntu, so i'll need detailed instructions.
thank you.

---

### Post by super61 on 2007-08-30
well what i have is ndiswrapper as well. do this
install that and install the inf file from the cd included with the usb adapter. use the win2k one ( its more reliable ) and get closer to your router. ( that was my main problem right there to far from router ) 

if non of that doesn't work i cant help

---

### Post by RageOfOrder on 2007-08-30
I use 
dhcpcd wlan0
to connect my wireless. 

Could also be that your ndiswrapper module isn't loaded.
Try
sudo rmmod ndiswrapper && sudo modprobe ndiswrapper

if this doesn't work, uninstall and re-install ndiswrapper and your drivers for it. Should fix it.

---

### Post by Staff on 2007-08-30
thanks, reinstalling ndiswrapperdid the trick! :D i used the 98 drivers and it worked ok.

---

