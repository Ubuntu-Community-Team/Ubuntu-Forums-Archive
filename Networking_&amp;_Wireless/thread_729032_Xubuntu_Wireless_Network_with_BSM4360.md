---
title: "Xubuntu Wireless Network with BSM4360"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by Tjcrazy on 2008-03-19
Hello all,

I am a linux noob. I installed Xubuntu a couple of days ago cause XP doesnt really work on 128 RAM and 530Mhz. Anyway... I got a BT Voyager 1060 wireless card which has a BCM 4360 chipset. I followed this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) using the offline installation (Well dur... I have no internet connection). Anyway the network I am connecting to is WPA-TKIP. I enabled Roaming Mode and connected to the network I am using. I enter the passcode and then it says it connected at 48% strength. I load of Firefox and no connection, I then open up all the other netowkr applications and none work. Is it to do with the I.P settings? I am a bit stressed today cause I had my I.T GCSE exam and to much computer hassle today.

Thanks,

Tjcrazy

---

### Post by honeydew on 2008-03-19
can you ping any IP addresses on the network?  it could be a dns issue?  

run these commands and post the output 
```
 ping 64.233.167.99
```

```
 cat /etc/resolv.conf
```

---

### Post by Tjcrazy on 2008-03-19
1st one:

Error: Network unreachable

2nd one:
Error: File unreachable or something..

---

### Post by Tjcrazy on 2008-03-19
I think it has comething to do with the DNS. It says its connected and everything just no internet connection. ANyone help??

---

### Post by honeydew on 2008-03-20
hrmm file unreachable dosnt make alot of sense to me..  you *should* have /etc/resolv.conf

---

### Post by perhhk on 2008-03-20
Try, if you haven;t already to set the primary dns address to the ip address of ur router.

---

### Post by Tjcrazy on 2008-03-20
Ive got and installed wicd on xubuntu. It manages to go online and get I.P, it has about 50% connection... But on system monitor when at 100% network status, it is not even doing 1kbs. This means its slower than dial-up. And its not wireless. Any suggestions?

---

### Post by dstew on 2008-03-20
Post the output of ```
iwconfig
```

---

### Post by Tjcrazy on 2008-03-20
timster@Tim:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"HORIZON"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:B5:54:16:72   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is the iwconfig, I can post the lspci and lspci -n if needed.

---

### Post by dstew on 2008-03-20
It seems that the link is poor. The bit rate is low, and the link quality bad. Is the antenna connected well? Try to reconnect (disable in Network, then enable again). Maybe it did not get the correct channel setting.

---

### Post by Tjcrazy on 2008-03-20
Well, it only goes through 1 solid wall. And the router signal strength is usually in the 40% area. I am really puzzled by this one. Many of my friends who are pro linux users cannot figure it out. Ive tried re-entering the DNS and IP settings I have also tried using wicd. Wicd worked but at less than 1kbs. When I had it working with the default xubuntu linux manager for a while at a good speed (200kbs) but I cannot get it working again. PLEASE HELP

Tjcrazy

---

### Post by dstew on 2008-03-20
Try unticking Enable Roaming in the System --> Administration --> Network --> eth0 --> Properties. This was suggested in the same guide you used, down in the Troubleshooting section. Apparently, if you have Enable Roaming clicked, the configuration is managed by network-manager (the icon in the top bar) instead of network-admin (in the System menu).

---

### Post by Tjcrazy on 2008-03-20
On Xubuntu there is no option for System --> Administration --> Network --> eth0 --> Properties. There is also no network-admin.

---

### Post by dstew on 2008-03-20
Sorry. Try disabling roaming mode however you do that on Xubuntu.

---

### Post by Tjcrazy on 2008-03-21
Without roaming mode, I have to enter in the Network information. When I enter in on the manual configuartion, nothing happens.

---

