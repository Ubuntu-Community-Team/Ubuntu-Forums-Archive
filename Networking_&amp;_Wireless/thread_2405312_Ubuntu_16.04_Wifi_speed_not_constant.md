---
title: "Ubuntu 16.04 Wifi speed not constant"
date: 2018-11-04
forum: Networking &amp; Wireless
---

### Post by shashank-sharma-15 on 2018-11-04
I have detected this problem while playing a game, usually what happens is that after every 10-15 seconds of interval my ping get increases and then again come back to normal. For example if my normal ping is 50 then after 10 seconds it gets to 100-120-160-180 and then stay there for 2 - 3 seconds and then slowly come back to normal and this event occurs every time for past 1 month.

I am pretty sure that it is not my internet problem but something related to wifi driver but I am not sure why it is happening. I usually use internet with ethernet because of this problem but I am not sure how to fix this wifi problem so I am pretty sure that it is not a game problem too.

Any help is much appreciated.

My network information

    ```
shashank@shashank:~$ lspci -v | grep -i network -A 6
    03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 31)
    Subsystem: Lite-On Communications Inc Device 08a6
    Flags: bus master, fast devsel, latency 0, IRQ 132
    Memory at b4000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
```


    ```
shashank@shashank:~$ sudo lshw -C network
      *-network               
       description: Wireless interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 31
       serial: 3c:a0:67:ad:88:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-45-generic firmware=WLAN.TF.1.0-00002-QCATFSWPZ-5 ip=192.168.88.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:132 memory:b4000000-b41fffff
```

---

### Post by jeremy31 on 2018-11-04
It could be the result of a few things, see the wireless script link in my signature and post results

---

### Post by shashank-sharma-15 on 2018-11-04
Hi
Thank you for responding, here is the result which I get:
Link: [http://paste.ubuntu.com/p/bRT4Q9TmzT/](http://paste.ubuntu.com/p/bRT4Q9TmzT/)

---

### Post by jeremy31 on 2018-11-04
I would change the encryption on the wifi router so it is WPA2 only with AES, no WEP/TKIP/WPA and also do
```
sudo iwconfig wlp3s0 power off
```
See if the power management stays off

---

### Post by shashank-sharma-15 on 2018-11-04
I tried doing this:

shashank@shashank:~$ sudo iwconfig wlp3s0 power off
shashank@shashank:~$ sudo service network-manager restart

And yet no change, still the same problem is happening, after 20 seconds again my ping was increased and then after 5 seconds it gradually decreases and it keeps on going again and again.
Here is the output after executing those commands:
Link: [http://paste.ubuntu.com/p/8J5Cv4b5Dx/](http://paste.ubuntu.com/p/8J5Cv4b5Dx/)

---

### Post by jeremy31 on 2018-11-04
You still have mixed mode encryption on the router
```
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
```

---

### Post by shashank-sharma-15 on 2018-11-04
But for this I need to change settings of router but this problem is happening with all different router. So is it possible that the problem is something else ?

---

### Post by jeremy31 on 2018-11-04
Check ```
dmesg | tail -20
```
When it happens to see if it might be something else

---

### Post by shashank-sharma-15 on 2018-11-04
Ok so I tried doing `dmesg -w` and then started my game, I observed same situation (getting high ping) but no log was generated during that period of time so I guess there was no error generated or caused.

---

