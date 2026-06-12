---
title: "prism and other problems"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by sheine on 2007-04-22
Yesterday I installed Feisty on my desktop without trouble and made a DSL connection. Today I installed it on my laptop and assumed that I could configure the wireless in the same way that I did with Edgy, using the wlan package. There is no wlan package available with synaptic in Feisty.

The built-in network tools did not let me configure my prism3 card. I then looked at previous threads here and found that I had to install packages like linux-wlan-ng. When I tried to get them through synaptic these packages were not there. I then went back to my desktop and the linux-wlan packages were available through synaptic.

The only thing different was that I had also installed automatix in my desktop. When I tried to install automatix on my laptop it did not install with a reference to a python2.4 dependency. I remembered that after I installed automatix on my desktop it did add another file automatically presumably this python file. Since it did not do it automatically in my laptop, I decided to add it through synaptic. In synaptic, I found that python2.5 was installed and there was no python 2.4 package available.

So how do I get my wireless to work?

---

### Post by sheine on 2007-04-23
The "other problems" all seem to be related to libbonoboui2-0 for which I get the error message "libbonobui2-0 is missing final newline". I have not been able to reinstall libbonobui2-0 using synaptic. 

What I don't understand is that using the same installation disk on my desktop and laptop, I did not have this problem on my desktop.

---

### Post by az on 2007-04-23
The linux-wlan-ng package is still in feisty, and it should be on the install cd.  Just boot Ubuntu and when at the desktop, insert the cd.  The package manager should start and you should be able to install that package from the cd.

---

### Post by sheine on 2007-04-23
> **az said:**
> The linux-wlan-ng package is still in feisty, and it should be on the install cd.  Just boot Ubuntu and when at the desktop, insert the cd.  The package manager should start and you should be able to install that package from the cd.

I followed this suggestion and with the CD installed it showed the linux-wlan-ng package as available. But, I still could not install it because of the libbonoboui2-0 problem referred to before.

I may try Kubuntu since this seems to be a gnome file.

---

### Post by az on 2007-04-23
Try running 

sudo dpkg --clear-avail

and then

sudo apt-get -f install

This is not a Gnome thing, but you seem to have currupted your package database.   That or you have a bad block or filesystem error on your disk.

---

### Post by sheine on 2007-04-24
I have now installed linux-wlan and based on hardware information Ubuntu sees my prism card. However, I have no internet connection and see no way to configure anything. I tried iwconfig without success.

---

### Post by az on 2007-04-24
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28linux-wlan-ng%29](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28linux-wlan-ng%29)

---

### Post by sheine on 2007-04-24
> **az said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28linux-wlan-ng%29](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28linux-wlan-ng%29)

I went to this site but it does not seem to relate to feisty. Because the packages were different in edgy, I could connect with it.

I then tried wifi-radar which did not connect me.

---

### Post by sheine on 2007-04-28
I tried Kubuntu. It recognizes my card and says that the device and network are active but it does not pick up a signal. My guess is that it needs a driver.

---

### Post by dbott67 on 2007-04-28
> **sheine said:**
> I tried Kubuntu. It recognizes my card and says that the device and network are active but it does not pick up a signal. My guess is that it needs a driver.


It may be related to the same problem in [this thread]("http://ubuntuforums.org/showthread.php?p=2546045#post2546045").  The fix/workaround requires [blacklisting the prism modules.]("http://ubuntuforums.org/showthread.php?p=2549142#post2549142")  

-Dave

---

### Post by sheine on 2007-04-28
> **dbott67 said:**
> It may be related to the same problem in [this thread]("http://ubuntuforums.org/showthread.php?p=2546045#post2546045").  The fix/workaround requires [blacklisting the prism modules.]("http://ubuntuforums.org/showthread.php?p=2549142#post2549142")  

-Dave

I added the blacklist ext and it still does not connect.

---

### Post by dbott67 on 2007-04-28
A few questions:

1. Are you running NetworkManager?

2. Can you post the output of the following commands:
```
sudo lshw -C network
``````
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
iwlist scanning
```Thanks,
Dave

---

### Post by sheine on 2007-04-28
> **dbott67 said:**
> A few questions:

1. Are you running NetworkManager?

Networkanager is installed but I see no place to run it.

2. Can you post the output of the following commands:
```
sudo lshw -C network
``````
cat /etc/network/interfaces
```

description: Ethernet interface physical id:1 logical none : wlan0
serial: 00:0a:e9:04:3c:83
capabilities: ethernet physical
configuration Broadcast=yes driver=p80211_prism_usb
driverversion=0.25
link=0 multicast=yes

cat /etc/network/interfaces
auto wlan.inet dhcp

```
ifconfig -a
```
wlan0 
Link encap:Ethernet HWaddr 00:0A:E9:04:3C:83
UP Broadcast Multicast MTU:1500 Metric 1
Rx packets:8 errors:1 dropped:0 overruns:0 frames:1
Tx packets :16 errors:0 dropped:0 overruns:0 carriers:0   collisions:0       txqueuelin:100
Rx bytes:1694 (1.6 KiB) Tx bytes:2074 (2.0KiB)

```
iwlist scanning
```
wlan0 No scan results

Thanks,
Dave

Thank you.

---

### Post by sheine on 2007-04-28
Apparently the combination:
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap

did work with the right follow-up. 

I restarted and tried to configure with the network icon on the panel. This failed. I then went through Adminisrtrative-Network, and iwconfig recognized my wireless connection. I am not sure whether that solved the problem because I then went to wifi radar and got a signal.

---

