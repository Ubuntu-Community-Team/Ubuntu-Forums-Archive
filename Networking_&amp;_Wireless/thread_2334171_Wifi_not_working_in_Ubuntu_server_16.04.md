---
title: "Wifi not working in Ubuntu server 16.04"
date: 2016-08-17
forum: Networking &amp; Wireless
---

### Post by yukinok25 on 2016-08-17
Hi all,

I have been trying to search online but I didn't find any solution to my issue, just to clarify I am using ubuntu server 14.04 for over a year and everything was working fine.

I have an intel NUC 2820 with an Intel wifi 7260 card, and I can use only wifi connection no ethernet.

I did a fresh install of Ubuntu 16.04 in a new SSD, and normally with Ubuntu 14.04 I would setup /etc/network/interfaces like this:

```
  # The loopback network interface
  auto lo
  iface lo inet loopback
   
  #The primary network interface
  auto wlan0
  iface wlan0 inet static
  address 192.168.11.4

  netmask 255.255.255.0
  gateway 192.168.1.1

  wpa-ssid xxxxx

  wpa-psk xxxxx

  dns-nameservers 192.168.1.1

  
```

However with 16.04 is not working, wifi doesn't connect, I cannot ping websites or download anything.

I have read online that many have problems with wifi, I have read a few thread and tried few workaround nothing works.

Someone is able to help me? I am lost honestly.

Thanks in advance,

---

### Post by ajgreeny on 2016-08-17
Possibly because the wifi connection is unlikely to be named wlan0 in 16.04.

See the info at [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) which may help you, and come back again if necessary.

Show us the output of ```
ifconfig
``` and ```
iwconfig
``` in terminal which should give more info on the name of your wifi connection which might help.

---

### Post by yukinok25 on 2016-08-17
Thank you ajgreeny.

I will read the info carefully Tomorrow.

What am I suppose to write instead of wlan0?

iwconfig unfortunately doesn't work, I did a fresh install and I am not connected to the internet, it says to download and install the wireless package.

---

### Post by yukinok25 on 2016-08-19
> **ajgreeny said:**
> Possibly because the wifi connection is unlikely to be named wlan0 in 16.04.

See the info at [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) which may help you, and come back again if necessary.

Show us the output of ```
ifconfig
``` and ```
iwconfig
``` in terminal which should give more info on the name of your wifi connection which might help.


Sorry for the late reply, the output of iwconfig is:

The program 'iwconfig' is not currently installed. You can install it by typing:

 sudo apt-get install wireless-tools

The output of ifconfig is:

lo  Link encap:Local Loopbck
                   inet addr:127.0.0.1 mask:255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK MTU :65536 Metric:1
                   RX packets:832 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:832 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0 txqueuelen:1
                   RX bytes:63440 (63.4 KB) TX bytes:63440 (63.4)

I have read the link you posted but I am not an expert in Ubuntu and I don't get how should I name my wireless lan, wlan0 was the easiest way for me.

What do you suggest?

EDIT: I actually found a way by looking on internet how to show the adapter name by typing:

```
ifconfig -a
```

I also activated the adapter by typing:

```
ifconfig "name of the adapter" up
```

I then switched wlan0 with the name of my adapter but still can't get online.

What am I missing?

---

### Post by yukinok25 on 2016-08-20
Please anyone can help me?

It has been 2 days that I am trying to connect my server to the internet without any luck, I don't know what to do anymore.

---

### Post by fillic2002 on 2016-08-20
I am also facing the same issue and so frustrated that thinking of switching to Windows.... any help in here...

I tried all the scenarios to get this wifi working on 16+ ubuntu LTS. I did read about the post on various sites and what i understoor to know the firmware i need to get the lspci details. I did that and to my machine it seems that i need to install firmware-b43-installer. I ran the command also but response is... not able to locate this firmware.I recently switched from windows to ubuntu and trying to understand how to make it work. 

However if i reboot from USB and then enable the additional driver for wifi it works like a charm.... I tried installing the same from USB but no luck..

---

### Post by yukinok25 on 2016-08-21
I have reinstalled from scratch Ubuntu server and use an ethernet cable to connect to the internet, so I could download updates and the wireless-tools package.

This is the iwconfig:

```
lo                 no wireless extensions.

enp3s0       no wireless extensions.

wlp2s0       IEEE 802.11bgn  ESSID: off/any
                    Mode:Managed  Access Point:         Not-Associated
                    Tx-Power=0 dBm
Retry short limit:7  RTS thr: off  Fragment thr: off  Power management: on
```


Seems like the ESSID is not recognised?

I also installed another driver for Linux  that I download directly from the Intel website.

Another thing I notice by searching online is that network-manager is not starting at all, seems like is not installed.

Any suggestions?

---

### Post by yukinok25 on 2016-08-25
Just for future reference, after 3 days of work I finally found a solution in the most simple way.

I reinstalled from scratch Ubuntu server 14.04 then upgrade it to 16.04, funny enough everything is work as suppose to.

---

