---
title: "New Install Packet Loss On Home Network"
date: 2019-06-14
forum: Networking &amp; Wireless
---

### Post by zagamaphatoadis on 2019-06-14
Hello,

I recently installed Ubuntu 16.04 on a old HP 2000 notebook. 

Unfortunately, now the wifi does not work on the laptop, but only over my home network. I used it over wifi at my library and it worked fine. (0% packet loss when pinging google, web browsing worked fine.) But on my home network I get 50-80% packet loss when pinging google or the router. 

I don't think the issue is my router because my windows computer and android phone both connect fine (0% packet loss to google over windows). Another thing that complicates my trouble shooting is that I don't have easy access to the physical router, since I get my wifi from a guy in the dorm next to mine.

I also am super new to linux, this computer is the first one I've downloaded it on. So I apologize in advance if anything I've said is unclear or I've made obvious mistakes.

---

### Post by wildmanne39 on 2019-06-14
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone will most likely be able to help.

---

### Post by zagamaphatoadis on 2019-06-14
Alright, here is the pastebin link:

[https://pastebin.ubuntu.com/p/WnvHgvQJJm/](https://pastebin.ubuntu.com/p/WnvHgvQJJm/)

Thank you

---

### Post by praseodym on 2019-06-15
Lets try
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
sudo iwconfig wlo1 power off
```

---

### Post by zagamaphatoadis on 2019-06-15
I entered the commands exactly as you said and received this output:
 ```

ryan@ryan-HP-2000-Notebook-PC:~$ echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf[sudo] password for ryan: 
options rt2800pci nohwcrypt=1
ryan@ryan-HP-2000-Notebook-PC:~$ sudo modprobe -rfv rt2800pci
rmmod rt2800pci
rmmod eeprom_93cx6
rmmod rt2x00pci
rmmod rt2800mmio
rmmod rt2x00mmio
rmmod rt2800lib
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211
ryan@ryan-HP-2000-Notebook-PC:~$ sudo modprobe -v rt2800pci
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko 
insmod /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko nohwcrypt=1 
ryan@ryan-HP-2000-Notebook-PC:~$ sudo iwconfig wlo1 power off



```

It still get's ~80% packet loss when I ping 8.8.8.8

-Thanks so much for the help

---

### Post by praseodym on 2019-06-16
Ok, lets see
```

cat /etc/network/interfaces
route -n
ifconfig -a
iwlist chan
sudo iwlist scan
```

---

### Post by zagamaphatoadis on 2019-06-16
Here is the result of those commands: ```

ryan@ryan-HP-2000-Notebook-PC:~$ cat /etc/network/interfaces# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
ryan@ryan-HP-2000-Notebook-PC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlo1
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
ryan@ryan-HP-2000-Notebook-PC:~$ ifconfig -a
eno1      Link encap:Ethernet  HWaddr 78:e3:b5:79:50:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:170423 (170.4 KB)  TX bytes:170423 (170.4 KB)


wlo1      Link encap:Ethernet  HWaddr 08:3e:8e:0c:bb:4c  
          inet addr:10.0.0.219  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:8201:cdfa::c9aa/128 Scope:Global
          inet6 addr: fe80::4095:bde7:e6a9:9058/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:789 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272549 (272.5 KB)  TX bytes:99449 (99.4 KB)


ryan@ryan-HP-2000-Notebook-PC:~$ iwlist chan
eno1      no frequency information.


wlo1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


lo        no frequency information.


ryan@ryan-HP-2000-Notebook-PC:~$ sudo iwlist chan
[sudo] password for ryan: 
eno1      no frequency information.


wlo1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)


lo        no frequency information.


ryan@ryan-HP-2000-Notebook-PC:~$



```


Now it get's 100% packet loss and says destination host unreachable. It still claims to be connected to my wifi network though.

Thank you for the continued help
(EDIT) misspelled a word

---

### Post by zagamaphatoadis on 2019-06-22
I installed ubuntu 18.04 from usb, this fixed whatever issue was occurring in ubuntu 16.08 on the device. It is now connecting just fine to the wifi with 0% packet loss.

---

