---
title: "Wireless instable BCM4313 on 14.04"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by ErikSlinger on 2014-09-28
Good evening,
Last week I've updated to 14.04 and since then the wifi connection is poor; I can connect to the network but there is no traffic from time to time.
Over the last days I've been trying to find a solution on this forum but I've the feeling that now I'm doing more harm than good to my system.
The same issue came up when installing 12.04 but I cannot remember how I sorted that out back then.

I hope that the info below will give somebody an idea.

Thanks a lot in advance.

```

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5105]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 5986:0299 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a5c:21f4 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"MSFH_ABE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 MSFH_ABE>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

---

### Post by Hadaka on 2014-09-28
Hi, try this
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
your card is special case#1 last in the list of the pci-id's
post back if you need additional information.
thanks.

---

### Post by ErikSlinger on 2014-09-28
Thanks Hadaka for your fast reply. Unfortunately this didn't solve the issue. Before I also tried to disable the N protocol and I've installed a kernel.  There are some more threads I followed but with the current connection I'm having I cannot trace them back. Thanks again.

---

### Post by ErikSlinger on 2014-09-29
Regarding the kernel, I've tried to install it using 
```
sudo apt-get install firmware-b43-installer
```
but it didn't work.

---

### Post by ErikSlinger on 2014-09-29
The "b43" and "ssb" drivers are also blacklisted. 

Confirmed it with
```
lsmod | egrep 'b43|ssb|brcm'
```

---

### Post by Hadaka on 2014-09-29
H, i noticed you have the wl driver loaded for your wireless,
past experience has shown that is not the best driver for your card.
What you want to end up with is the bcma (part of the b43 crowd) and
the brcmsmac also known as the native driver; so let's try this.
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then do..
```
sudo modprobe bcma
sudo modprobe brcmsmac 
```
test.

---

### Post by ErikSlinger on 2014-09-29
Thanks again for your reply.
On the first code I got the reply that this was not installed.
The second group of codes gave no feedback so I assume it's ok.
Before and after rebooting the connection keeps on dropping every minute or so.

---

### Post by Hadaka on 2014-09-29
Hi, it should not have said "not installed" ..it was on your lspci list
let's run the wireless script and see what is lurking..
[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
thanks.

---

### Post by ErikSlinger on 2014-09-30
Hello Hadaka,
Thanks again for your feedback. Please find below the output of the script as run just now.
Now the bcmwl is not ther anymore.

```

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5105]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 5986:0299 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0a5c:21f4 Broadcom Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"MSFH_ABE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 MSFH_ABE>   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:138   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
2: phy0: Wireless LAN                  no            no
3: hci0: Bluetooth                     no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              630653  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211
bcma                   52096  2 brcmsmac
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o==========o===========o=========o===========o==============o===========
 Interface & ID             | Type        | Driver   | State     | Default | Speed     | Support      | HW Addr   
============================o=============o==========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169    | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.2.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
----------------------------+-------------+----------+-----------+---------+-----------+--------------+-----------
 wlan0  [MSH_ABE]          | 802.11 WiFi | brcmsmac | connected | no      | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


```

---

### Post by ErikSlinger on 2014-10-02
I hope that this part of the script is sufficient.

---

### Post by Hadaka on 2014-10-02
Hi, well, thats an improvment. I need the full wireless
report, not just pieces parts. But do this firsrt, turn off
the computer, as in power down, turn off the router,
power back the router, wait 5, power back the computer,
remove the ethernet cable,
if you still have no wireless,reconnect the cable and run the script again and report
the full output.
thanks.

---

### Post by ErikSlinger on 2014-10-03
Good evening,
Just now I've followed your suggestion regarding router and laptop. Attached the result of the script.
I hope this will help finding a solution. I managed to download the script but didn't manage to sign in on the forum using the wifi. Now connected to the ethernet cable again.
Thanks for your support!

[ATTACH]256924[/ATTACH]

---

### Post by Hadaka on 2014-10-03
Hi please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
then do,with ethernet cable not attached
```
ping -c3 192.168.2.1
ping -c3 8.8.8.8
ping -c3 yahoo.com
```
post the outputs
re attach the internet cable and
run and post the wireless scrip again please
thanks.

---

### Post by ErikSlinger on 2014-10-04
Good morning,

I ran the code and booted the laptop. Then I ran the codes to ping twice since from time the time the connection drops and comes back. So I got 2 different outputs.

```

   erik@erik-ThinkPad-Edge-E135:~$ ping -c3 192.168.2.1 
 PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data. 
  
 --- 192.168.2.1 ping statistics --- 
 3 packets transmitted, 0 received, 100% packet loss, time 2000ms 
  
 erik@erik-ThinkPad-Edge-E135:~$ ping -c3 8.8.8.8 
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 
  
 --- 8.8.8.8 ping statistics --- 
 3 packets transmitted, 0 received, 100% packet loss, time 2015ms 
  
 erik@erik-ThinkPad-Edge-E135:~$ ping -c3 yahoo.com 
 ping: unknown host yahoo.com 
```

```

   
erik@erik-ThinkPad-Edge-E135:~$ ping -c3 192.168.2.1 
 PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data. 
 64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.40 ms 
 64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=3.29 ms 
 64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=6.56 ms 
  
 --- 192.168.2.1 ping statistics --- 
 3 packets transmitted, 3 received, 0% packet loss, time 2003ms 
 rtt min/avg/max/mdev = 1.402/3.752/6.563/2.132 ms 
 erik@erik-ThinkPad-Edge-E135:~$ ping -c3 8.8.8.8 
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 
 64 bytes from 8.8.8.8: icmp_seq=1 ttl=44 time=862 ms 
 64 bytes from 8.8.8.8: icmp_seq=2 ttl=44 time=810 ms 
 64 bytes from 8.8.8.8: icmp_seq=3 ttl=44 time=877 ms 
  
 --- 8.8.8.8 ping statistics --- 
 3 packets transmitted, 3 received, 0% packet loss, time 2001ms 
 rtt min/avg/max/mdev = 810.922/850.361/877.548/28.566 ms 
 erik@erik-ThinkPad-Edge-E135:~$ ping -c3 yahoo.com 
 ping: unknown host yahoo.com 
```

Then I ran the wireless script again. Attached to this message.

Thanks a lot for your feedback. It is very much appreciated.

---

### Post by Hadaka on 2014-10-04
please edit your wifi network connection to look exactly
like the screen shots..be sure to save.
thanks

[ATTACH=CONFIG]256941[/ATTACH][ATTACH=CONFIG]256940[/ATTACH]

---

### Post by ErikSlinger on 2014-10-05
Hey Hadaka,
First of all, thanks a lot for your support on this. This last post, setting the settings to "forget" made it all work very smooth. The wifi seems to be very stable and uninterrupted.
Will now mark the thread as solved.
Thanks again,
Erik

---

### Post by Hadaka on 2014-10-05
This is good news !! glad to see it working.
You are welcome.

---

