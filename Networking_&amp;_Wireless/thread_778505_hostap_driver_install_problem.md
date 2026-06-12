---
title: "hostap driver install problem"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by 052d on 2008-05-02
i have a pcmia prism 2.5 wireless card, and wish to use hostap driver.
after installing xubuntu 8.0.4, i followed some people's guide, blacklisted orinoco drivers, and use Synaptic to downloaded and installed hostap driver.
however, xubuntu cannot find my wireless card. i type iwconfig, and it returns no wireless interface. ifconfig -a, only find ethernet card.
what's the problem? please help.

---

### Post by chili555 on 2008-05-02
I am not sure it's the orinoco driver you want to blacklist; I think it's the prism2. Find out which prism is being loaded:```
lsmod | grep prism
```It will be prism2_pci or plain old prism2 or something. Blacklist it and while you are in there, remove the orinoco listing. Reboot.

Did your wireless spring to life?

---

### Post by 052d on 2008-05-03
> **chili555 said:**
> I am not sure it's the orinoco driver you want to blacklist; I think it's the prism2. Find out which prism is being loaded:```
lsmod | grep prism
```It will be prism2_pci or plain old prism2 or something. Blacklist it and while you are in there, remove the orinoco listing. Reboot.

Did your wireless spring to life?

after install xubuntu on my laptop, and install hostap driver,
type iwconfig, it appears following message:
ivy@ivy-laptop:~$ iwconfig
lo          no wireless extensions.
eth0        no wireless extensions.
irda0       no wireless extensions.
eth1        IEEE 802.11b  ESSID:"ABCD"  Nickname:"Prism  I"
         Mode:Managed  Frequency:2.452 GHz  Access Point: 00:16:AA:82:54:00   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
         Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/92  Signal level=-32 dBm  Noise level=-149 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

there is no prism2_pci or something

if i use lsmod | grep prism
it returns nothing

if use lsmod | grep orinoco
it returns
orinoco_cs               16396  1 
orinoco                  42772  1 orinoco_cs
hermes                    8448  2 orinoco_cs,orinoco
pcmcia                   40876  2 orinoco_cs
pcmcia_core              40596  5 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

when i type sudo modprobe hostap, then use lsmod | grep hostap, the result is :
ivy@ivy-laptop:~$ lsmod | grep hostap
hostap_cs                 62868  0 
hostap                   110724  1 hostap_cs
ieee80211_crypt            7040  1 hostap
pcmcia                    40876  1 hostap_cs
pcmcia_core               40596  4 hostap_cs,orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

when i blacklist orinoco_cs, and reboot computer, my wireless card does not work anymore.
use iwconfig, will get such result:
ivy@ivy-laptop:~$ iwconfig
lo          no wireless extensions.
eth0        no wireless extensions.
irda0       no wireless extensions.

if i restore blacklist and reboot, then everything is ok, but the driver of my wireless card still is orinoco_cs.

why?

---

### Post by Paris Heng on 2008-05-03
> **052d said:**
> i have a pcmia prism 2.5 wireless card, and wish to use hostap driver.
after installing xubuntu 8.0.4, i followed some people's guide, blacklisted orinoco drivers, and use Synaptic to downloaded and installed hostap driver.
however, xubuntu cannot find my wireless card. i type iwconfig, and it returns no wireless interface. ifconfig -a, only find ethernet card.
what's the problem? please help.

I believe nobody using Prsim here, you need to go for the hostap mailing list.

---

