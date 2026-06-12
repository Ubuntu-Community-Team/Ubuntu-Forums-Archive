---
title: "Unstable Wireless with 12.04 Atheros AR9462, can't compile a new ath9k driver"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by suaf on 2014-01-03
Hello,

I bought a new Acer Aspire M3-481 laptop and put Ubuntu 12.04 LTS. Everything works more or less OK but the wireless connection, which is very unstable, disconnects every several minutes. The Wireless card is Atheros AR9462, and as far as I could find on the forums, many people have problems with it.

1. I tried this decision, it seemed quite popular and working, but it did not help:

[http://ubuntuforums.org/showthread.php?t=2081714](http://ubuntuforums.org/showthread.php?t=2081714)

It suggested modifying the *ath9k.conf* by adding *options ath9k nohwcrypt=1*.

2. I found out that some people compiled backported drivers, as suggested here:

[http://ubuntuforums.org/showthread.php?t=2133296&page=2](http://ubuntuforums.org/showthread.php?t=2133296&page=2)

and most of all here:

[http://ubuntuforums.org/showthread.php?t=2035902&page=4](http://ubuntuforums.org/showthread.php?t=2035902&page=4)

However, the information is very old. The backports page looks completely different now, none of the described commands are working, and I am not really into compiling. So I couldn't actually install the latest ath9k driver to see what will happen. I followed the instructions here: 

[https://backports.wiki.kernel.org/index.php/Documentation#Usage_guide](https://backports.wiki.kernel.org/index.php/Documentation#Usage_guide)

But the latest backports don't show the ath9k driver in the menu. I tried about 5 different versions. Maybe I'm doing something wrong.

Any ideas? Thanks a lot.

---

### Post by chili555 on 2014-01-03
Please get a temporary wired ethernet connection and do:

```
sudo apt-get install linux-headers-generic build-essential
```

I suggest you download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd ~/Desktop/backports-3.12.2-1/
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k
```

Your wireless should now be working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd ~/Desktop/backports-3.12.2-1/
make clean
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k

```Post back if you get stuck.

---

### Post by suaf on 2014-01-03
make defconfig-ath9k


So that's what I was missing... It worked perfectly, thank you very much for the quick reply! I've been using the wifi for a few hours now, and it seems to work great!

---

### Post by neil18 on 2014-10-22
> **chili555 said:**
> Please get a temporary wired ethernet connection and do:

```
sudo apt-get install linux-headers-generic build-essential
```

I suggest you download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd ~/Desktop/backports-3.12.2-1/
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k
```

Your wireless should now be working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd ~/Desktop/backports-3.12.2-1/
make clean
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k

```Post back if you get stuck.


Hi, I have problem when I rebooted my machine, wireless connected is disabled and i have to do it again :( . How can i make this permanent? Thanks!

---

### Post by chili555 on 2014-10-22
> **neil18 said:**
> Hi, I have problem when I rebooted my machine, wireless connected is disabled and i have to do it again :( . How can i make this permanent? Thanks!Please reboot. Check to see if the module *ath9k* is loaded:```
lsmod | grep ath9k
```If not, load it:```
sudo modprobe ath9k
```Then add it to the list of modules that are to loaded automatically:```
sudo -i
echo ath9k  >>  /etc/modules
exit
```You should be all set.

---

### Post by neil18 on 2014-10-23
Thanks! It works like a charm!

---

### Post by Koli14 on 2015-02-11
Hy!
I also stuck with my WIFI connection. I tried a lot of suggested solution, but non of them helped.
If i try your solution, then by 'make' i get a lot of warning and error:[ http://pastebin.com/ZJgTdsuF]("http://pastebin.com/ZJgTdsuF")
I use linux mint 17.1 Rebecca - Cinnamon 64-bit
uname -r : 3.13.0-37-generic
Acer Aspire V3-371, Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
And here is the output of mintwifi:
> mintwifi
-------------------------
* I. scanning WIFI PCI devices...
  -- Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
      ==> PCI ID = 168c:0034 (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 30:65:ec:4b:3b:bc  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3265:ecff:fe4b:3bbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32610444 (32.6 MB)  TX bytes:315023138 (315.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92886 (92.8 KB)  TX bytes:92886 (92.8 KB)

wlan0     Link encap:Ethernet  HWaddr c0:38:96:75:a7:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2015-02-11
> **Koli14 said:**
> Hy!
I also stuck with my WIFI connection. I tried a lot of suggested solution, but non of them helped.
If i try your solution, then by 'make' i get a lot of warning and error:[ http://pastebin.com/ZJgTdsuF]("http://pastebin.com/ZJgTdsuF")
I use linux mint 17.1 Rebecca - Cinnamon 64-bit
uname -r : 3.13.0-37-generic
Acer Aspire V3-371, Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
And here is the output of mintwifi:If you are running a 3.13 kernel version, installing backports 3.*12*, an older driver version, is unlikely to help, even if it compiled properly.

I suggest you ask the question here: [http://forums.linuxmint.com/viewforum.php?f=53](http://forums.linuxmint.com/viewforum.php?f=53)

---

### Post by Koli14 on 2015-02-12
Ubuntu forum is just much more alive. :P But thanks. I tried it with other backports (3.18, 3.17, 3.14) but did not fixed the issue.
Kolos

---

### Post by chili555 on 2015-02-12
> **Koli14 said:**
> Ubuntu forum is just much more alive. :P But thanks. I tried it with other backports (3.18, 3.17, 3.14) but did not fixed the issue.
KolosAnd what, exactly, is the issue?

It seems that many newer users think a newer or, in your case, older (!!) driver is the answer to everything.

If your car is out of fuel, for example, a different driver isn't going to change anything.

---

### Post by Cem_Ara on 2015-03-24
> **chili555 said:**
> And what, exactly, is the issue?

It seems that many newer users think a newer or, in your case, older (!!) driver is the answer to everything.

If your car is out of fuel, for example, a different driver isn't going to change anything.

The issue is the wifi doesn't work correctly.
List of SSID shows up fine but the wifi card can't connect to any of them.
dmesg shows that authentication with <mac address of router> timed out.
I tried turning off password, WEP, WPA2 but none worked.
I have the same laptop model as him, I tried to search for a solution for weeks.
A few result with this same laptop stated that they give up trying to fix it.
I tried kernel versions from 3.13 to 4.0 and it is still not working.
The laptop is a fairly new Broadwell CPU model but the wifi adapter reports the model which is AR9462.
I think there might be a difference in the model even though the version reported is the same, that's why none of the solutions posted worked. 

Tried different distro, ubuntu, linux mint, debian and all 3 didn't work.

---

