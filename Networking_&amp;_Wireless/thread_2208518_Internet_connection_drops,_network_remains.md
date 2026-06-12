---
title: "Internet connection drops, network remains"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by ace214 on 2014-02-28
I have an interesting issue.

It seems my router configuration is working for other computers on my network (Windows and Mac), but not Ubuntu. I have tried to access it with my built-in wireless (Intel AC-7260) and a USB adapter (Edimax EW-7811Un). 

When I connect to the network (WIFIHICKS), I am able to use it for anywhere between 30 seconds to a few minutes. After some amount of time (seemingly random), I lose the internet connection (and connection to the router web interface as well as any network activity), but am still connected to the network via the network manager.

This is the only network I have these issues with, and no one in my house seems to have the same issues. I am running a System76 computer, and don't have Windows installed, so I'm not able to test that.

Right now, I have another router plugged into the cable one (from Charter), and am running successfully off that.

1 ) Machine Brand and Model (PC/Laptop):
```
System76 Gazelle Pro
```
2 ) Wireless Brand, Model and Wireless Chipset:
```
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)

```

ifconfig and iwconfig while working:
```
jon@jon-Gazelle-Pro:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:5f:25:5d  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e8b:fdff:fe5f:255d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10563687 (10.5 MB)  TX bytes:2044576 (2.0 MB)

jon@jon-Gazelle-Pro:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"WIFIHICKS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 7C:E9:D3:8C:35:03   
          Bit Rate=115.6 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          **Tx excessive retries:51**  Invalid misc:41   Missed beacon:0

```

ifconfig and iwconfig after it stops working
```
jon@jon-Gazelle-Pro:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:5f:25:5d  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e8b:fdff:fe5f:255d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12265923 (12.2 MB)  TX bytes:2419124 (2.4 MB)

jon@jon-Gazelle-Pro:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"WIFIHICKS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 7C:E9:D3:8C:35:03   
          Bit Rate=104 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          **Tx excessive retries:671**  Invalid misc:56   Missed beacon:0

```


dmesg output:
```
[ 2447.267672] wlan0: authenticate with 7c:e9:d3:8c:35:03
[ 2447.268380] wlan0: send auth to 7c:e9:d3:8c:35:03 (try 1/3)
[ 2447.270355] wlan0: authenticated
[ 2447.271596] wlan0: associate with 7c:e9:d3:8c:35:03 (try 1/3)
[ 2447.274838] wlan0: RX AssocResp from 7c:e9:d3:8c:35:03 (capab=0x411 status=0 aid=2)
[ 2447.275762] wlan0: associated

```

6 ) Network configuration
```
jon@jon-Gazelle-Pro:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 73
       serial: 0c:8b:fd:5f:25:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-18-generic firmware=22.1.7.0 ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f7d00000-f7d01fff

```

Ubuntu 13.10
3.11.0-18-generic x86_64

---

### Post by varunendra on 2014-03-03
> **ace214 said:**
> ..my built-in wireless (**Intel AC-7260**) and a USB adapter (Edimax EW-7811Un).
...<snip>...
**3.11.0-18-generic** x86_64

I get it that you are probably experiencing it on the USB adapter as well, but for the internal card, please try (based on a recent experience in [this thread]("http://ubuntuforums.org/showthread.php?t=2208210")) -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlmvm **power_scheme=1**
```
This will be a temporary change that will be lost at next boot. Try the stability without rebooting and if it seems to help, make it permanent as mentioned in the above linked thread (post #9).

If that doesn't help, also try it along with some other parameters -
```
sudo modprobe -rv iwlmvm
sudo modprobe -v iwlwifi **[COLOR="#B22222"]bt_coex_active=N[/COLOR] [COLOR="#0000CD"]swcrypto=1[/COLOR] [COLOR="#FF0000"]11n_disable=1[/COLOR]**
sudo modprobe -v iwlmvm **power_scheme=1**
```
The "11n_disable=1" parameter will disable the N-speeds, so you may wish to omit that unless it is really required.

To have a better understanding of what these parameters do and how to try them, please read the post #9 in the above linked thread. And please let us know if any of these works. :)

---

### Post by ace214 on 2014-03-15
> **varunendra said:**
> 
The "11n_disable=1" parameter will disable the N-speeds, so you may wish to omit that unless it is really required.

Hmm... Unfortunately, this was the only one that worked. Is there a way to disable it for this connection only? I'm not sure if I come in contact with other N-rated networks.

---

### Post by varunendra on 2014-03-16
The parameters suggested above will become permanent ONLY if you create a .conf file with them. The method suggested in my previous post loads them only temporarily (for one session or during one driver unload-reload cycle). So it would already be ineffective if you try connecting to another network after a reboot (or after reloading the driver without parameters).

By rebooting or by reloading the driver without parameters (the parts highlighted in bold/colour), the driver will load with full support. Although if the other networks don't have support for N-channel, there is no point in enabling it.

However, if you have made it permanent following post #9 of the previously linked thread, and now wish to make it temporary again, simply delete that .conf file(s) you created -
```
sudo rm /etc/modprobe.d/iwlwifi.conf
```

---

