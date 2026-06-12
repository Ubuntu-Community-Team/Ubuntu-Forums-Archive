---
title: "Broadcom BCM4312 / HP DV6"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by bencouve on 2013-11-26
Hello experts!!!

I am having trouble getting my wifi working on a HP DV6. The signal indicator at the top of the laptop stays red and will not change to blue. Have just upgraded to 13.04 today (after a recovery) but am sure this is not the cause. I have a DV7 running fine on the same router so it is not the router. I will paste in some output.

lspci -nnk | grep -i net -A2
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1508]
    Kernel driver in use: b43-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3627]
    Kernel driver in use: r8169

 sudo ifconfig wlan0 up;iwconfig
wlan0: ERROR while getting interface flags: No such device
eth0      no wireless extensions.

lo        no wireless extensions.

Also ran these but got errors

sudo apt-get remove bcmwl-kernel-source
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl*
sudo apt-get install b43-fwcutter firmware-b43-installer bcmwl*

The above instructions I found at this url

[http://askubuntu.com/questions/101104/no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312](http://askubuntu.com/questions/101104/no-wireless-connection-detected-hp-pavilion-dv6-1220-with-a-broadcom-bcm-4312)

Please advise. Thanks in advance...

---

### Post by mörgæs on 2013-11-27
Though you are sure it does not help you should still consider a clean install of 13.10. 13.04 is out of support in a couple of months so you need to get to .10 anyway.

---

### Post by bencouve on 2013-12-03
Ok, I will try that. Thanks for the comment

---

