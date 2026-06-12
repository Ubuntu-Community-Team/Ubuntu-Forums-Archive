---
title: "Wireless does not start on boot, needs service restart to work"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by PolishPaul on 2008-07-28
I'm having a problem where the wireless network does not automatically start upon boot up. I have to restart the network service and it works fine.

I have a Lenovo T61 laptop running Ubuntu 8.04. nic =  PRO/Wireless 3945ABG Network Connection

The network interfaces file looks like this:
```

root@Atari130XL:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.130
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp
```

when i added the last 2 lines, it did not work. I simply restart network service and things work. I want to be able to boot up and just have the network start. 

I'm honestly not sure how to even approach this problem - the card works, just doesn't start. I remember once reading something about enabling certain things after hibernation but i can't find the article.

---

### Post by chili555 on 2008-07-29
First, the lines you added are commented out; they will have no effect. Perhaps you commented them out when you saw they had no effect.

Second, I doubt the interface for your 3945ABG is either eth0 or eth1. I also wonder how it is getting connected without an ESSID being declared, at a minimum. Please run, in a terminal:```
iwconfig
```Let's see what the interface really is.

---

### Post by PolishPaul on 2008-09-19
```
pczopowik@Atari130XL:~$ sudo /etc/init.d/networking restart (ARGH!!!)
[sudo] password for pczopowik: 
 * Reconfiguring network interfaces...                                   [ OK ] 
pczopowik@Atari130XL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Home"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:EB:AA:9B   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=63/100  Signal level=-69 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Yeah, i commented them out. Where is the ESSID supposed to be declared?

---

### Post by deltamort on 2008-09-20
i'm experiencing the same problem on my lenovo y410 too.

the wifi only starts with a reboot. can anyone help in this problem? it must have some problem on the restart service:(

---

