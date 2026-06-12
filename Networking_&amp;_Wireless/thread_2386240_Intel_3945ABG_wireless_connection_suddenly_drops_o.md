---
title: "Intel 3945ABG wireless connection suddenly drops on 17.10"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by bertar on 2018-03-02
I have an old laptop Toshiba SATELLITE L350-150 with an Intel® PRO/Wireless 3945ABG network card.

I used mkusb to create a persistent USB stick with Lubuntu 17.10.

Booting the OS works fine and the wireless connection works well, until suddenly it drops. Network manager indicates 'Device not ready'.

The [=iwl3945#firmware"]latest firmware]("https://wireless.wiki.kernel.org/en/users/drivers/iwlegacy?s[) 15.32.2.9 is used (see lshw output).

Any ideas how to fix this?


**Troubleshooting**


Did not solve the problem 

```
sudo service network-manager restart

sudo modprobe -r iwl3945 && sudo modprobe iwl3945

```

Here is some output:

**Network-manager**

    ```
lubuntu@lubuntu:~$ sudo service network-manager status 
    
    &#9679; NetworkManager.service - Network Manager
       Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
       Active: active (running) since Fri 2018-03-02 18:15:05 CET; 32min ago
         Docs: man:NetworkManager(8)
     Main PID: 1503 (NetworkManager)
        Tasks: 4 (limit: 4915)
       CGroup: /system.slice/NetworkManager.service
               &#9492;&#9472;1503 /usr/sbin/NetworkManager --no-daemon
    
    mrt 02 18:47:13 lubuntu NetworkManager[1503]: <info>  [1520012833.5817] device (wlp3s0): supplicant interface state: starting -> down
    mrt 02 18:47:23 lubuntu NetworkManager[1503]: <warn>  [1520012843.6283] device (wlp3s0): re-acquiring supplicant interface (#1).
    mrt 02 18:47:24 lubuntu NetworkManager[1503]: <error> [1520012844.1776] sup-iface[0x55e96410c5c0,wlp3s0]: error adding interface: wpa_supplicant couldn't grab this interface.
    mrt 02 18:47:24 lubuntu NetworkManager[1503]: <info>  [1520012844.1777] device (wlp3s0): supplicant interface state: starting -> down
    mrt 02 18:47:34 lubuntu NetworkManager[1503]: <warn>  [1520012854.6367] device (wlp3s0): re-acquiring supplicant interface (#2).
    mrt 02 18:47:35 lubuntu NetworkManager[1503]: <error> [1520012855.1842] sup-iface[0x55e96410c2a0,wlp3s0]: error adding interface: wpa_supplicant couldn't grab this interface.
    mrt 02 18:47:35 lubuntu NetworkManager[1503]: <info>  [1520012855.1843] device (wlp3s0): supplicant interface state: starting -> down
    mrt 02 18:47:45 lubuntu NetworkManager[1503]: <warn>  [1520012865.6367] device (wlp3s0): re-acquiring supplicant interface (#3).
    mrt 02 18:47:46 lubuntu NetworkManager[1503]: <error> [1520012866.1907] sup-iface[0x55e96406b530,wlp3s0]: error adding interface: wpa_supplicant couldn't grab this interface.
    mrt 02 18:47:46 lubuntu NetworkManager[1503]: <info>  [1520012866.1907] device (wlp3s0): supplicant interface state: starting -> down
```


**lspci**
    
    ```
lubuntu@lubuntu: lspci 
    03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```


**lshw**
    
    ```
lubuntu@lubuntu:~$ sudo lshw -class network
      *-network DISABLED
           description: Wireless interface
           product: PRO/Wireless 3945ABG [Golan] Network Connection
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: wlp3s0
           version: 02
           serial: 00:1f:3c:8a:71:54
           width: 32 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwl3945 driverversion=4.13.0-21-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11
           resources: irq:27 memory:d4300000-d4300fff
```


**rfkill**
    
    ```
lubuntu@lubuntu:~$ rfkill list all
    0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```


**dmesg**
    
    ```
[ 1976.616299] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
    [ 1978.103671] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
    [ 1978.117286] r8169 0000:02:00.0 enp2s0: link down
    [ 1978.117386] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
    [ 1978.120365] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
    [ 1978.168538] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.168548] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.215241] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.215247] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.261955] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.261960] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.308659] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.308665] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.355358] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.355362] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.392715] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
```

---

### Post by chili555 on 2018-03-03
>  [ 1978.168538] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.168548] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
    [ 1978.215241] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a2, s/b 0xf802020
    [ 1978.215247] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5You have a bug! [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1408963](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1408963) and also: [https://bugzilla.kernel.org/show_bug.cgi?id=93041](https://bugzilla.kernel.org/show_bug.cgi?id=93041)

The suspected fix is to disable power saving. From the terminal: ```

sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*


```Post back and let us know if this helps.

---

### Post by bertar on 2018-03-04
Thank you chili555,

I checked the wifi power saving setting and this was enabled (value = 3)
```
lubuntu@lubuntu:/etc/NetworkManager/conf.d$ cat default-wifi-powersave-on.conf 
[connection]
wifi.powersave = 3

```
Like you adviced, I changed it to value 2, i.e. disabled. I will test this setting for a while and then report the result here in this thread.

---

### Post by bertar on 2018-04-14
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
``` solved the issue!
Thank you [COLOR=#000000]chili555![/COLOR]

---

### Post by kurt18947 on 2018-04-15
Could you mark the thread "solved" using the thread tools in the first post (I think)? This seems like it could be a recurring question.

---

