---
title: "Can't connect to internet"
date: 2018-09-23
forum: Networking &amp; Wireless
---

### Post by faber812 on 2018-09-23
Hello Everybody,

I have just installed Ubuntu 18.4.1 (coming from Windows 10) on my laptop Asus.  

Everything seems to work fine except the computer can't connect to the internet. If I try the Wifi I get stucked in an infinite loop where Ubuntu keeps asking for the Wifi password (that I wrote correctly). 

Even with a cable, I cannot manage to connect and I get an "unable to connect" message. The network works just fine on any other device in the house. 

I am new to Ubuntu (and Linux in general) but I did some homeworks before posting and run some commands to check things myself (I went as far as a noob can go :) ) :

sudo rfkill list:

```
0: phy0: Wireless LAN
                 Soft blocked: no
                 Hard blocked: no
            1: hci0: Bluetooth
                     Soft blocked: no
                     Hard blocked: no
```

sudo lshw -c network:

```
 *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 40:e2:30:ac:bb:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
        configuration: broadcast=yes driver=ath9k  driverversion=4.15.0-29-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: enp5s0f1
       version: 12
       serial: 08:62:66:b4:af:d3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:19 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff
```


sudo ifconfig -a:

```
ifconfig: command not found
```  ###This one puzzles me. I think I miss some package but without internet I have no idea how to get them

iwconfig:

```
wlp4s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



```


lspci -nn | grep -i net:

```
04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
05:00.1  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 12)

```

I am not sure I understand every single output nor that I did the right checks (again, I am a noob :( ) 

I have even tried to reinstall the whole OS but the problem persisted. 

Any idea how I could solve this? 

Thank you all in advance.

---

### Post by surya.durgaputra on 2018-09-23
Ubuntu has some known issues regarding wifi connectivity. I also created another thread on the same forum few minutes ago.
That said, is your machine dual boot? And are you able to connect to the internet (wifi and wired both ways) when on the other OS (I guess windows) on the same PC (this will rule out possibility of damaged network card hardware).
Also, ifconfig is part of net-tools package that you need to install like so:
sudo apt-get install net-tools

---

### Post by faber812 on 2018-09-23
Hi,

No unfortunately the other OS is gone for good. Only ubuntu left.

---

### Post by surya.durgaputra on 2018-09-23
This helps?
[https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8](https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8)

---

### Post by jeremy31 on 2018-09-23
Can you connect with wifi after
```
sudo iwconfig wlp4s0 txpower 20
```
Or do you get an error?

---

### Post by faber812 on 2018-09-23
Nope, I don't get any error message but still it does not connect to the net. Just keeps asking the password over and over. 

I have tried to connect using my mobile phone as an hotspot and surprise, it works!  At least I can rule out any hardware damage. However I can't use this trick often because it is a bit costly :)

---

### Post by jeremy31 on 2018-09-23
See the wireless script link in my signature.  Can you connect your phone to wifi and then use USB tethering to the computer?

---

### Post by faber812 on 2018-09-23
Hi Jeremy31,

I am checking the guides in the signature. 

For the phone tethering, if I understand correctly you mean connect my laptop to the net through the phone. It seems that I am unable to do it. It works only if I activate the data roaming (thus paying money) on the phone.

But maybe I am missing some pieces. I'll look for some guide on this as well.

---

### Post by faber812 on 2018-09-23
Tried but still nothing. Btw I don't think I have a broadcom because when I try the code in the guide I get no output.  

From the previous outputs I believe I have a realtek. Not sure though, I haven't used this laptop in a while.

---

### Post by jeremy31 on 2018-09-23
You have a Qualcomm Atheros AR9485, they can be picky about router encryption settings, see chili555's post at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

---

### Post by faber812 on 2018-09-23
Nope, very same issue. 

I also think it is an authentication or encryption. Any other suggestion?

---

### Post by faber812 on 2018-09-23
Nope. Still same problem! :(

---

### Post by faber812 on 2018-10-02
Hello guys

Any other idea how to solve this issue? I still can't connect :(

---

