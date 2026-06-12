---
title: "Wifi not working in Ubuntu 16 and no available Wifi networks are shown"
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by saha96 on 2017-03-07
Here are my outputs of  - 

[B]Ifconfig

[/B]```
enp7s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500        inet 10.2.98.161  netmask 255.255.0.0  broadcast 10.2.255.255
        inet6 fe80::ce08:69a:48e6:65a1  prefixlen 64  scopeid 0x20<link>
        ether 70:5a:0f:08:3f:62  txqueuelen 1000  (Ethernet)
        RX packets 61290  bytes 62171853 (62.1 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 28933  bytes 2549107 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 26833  bytes 1633609 (1.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 26833  bytes 1633609 (1.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp19s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 30:f7:72:5f:4f:93  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```[B]lspci | grep -i net

[/B]```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
13:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter



```


I tried the 2nd solution from [http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be](http://askubuntu.com/questions/645220/unable-to-connect-wifi-ubuntu-14-04-lts-hp-pavilion-network-driver-rtl8723be)

```
[COLOR=#111111][FONT=Consolas]wget https://github.com/lwfinger/rtlwifi_new/archive/rock.new_btcoex.zip[/FONT][/COLOR]
unzip rock.new_btcoex.zip
cd rtlwifi_new-rock.new_btcoex
make
sudo -i
make install
echo "options rtl8723be ant_sel=2"  >  /etc/modprobe.d/rtl8723be.conf [COLOR=#111111][FONT=Consolas]exit[/FONT][/COLOR]
```

It did work for a while and all available wifi networks were shown and it connected easily. But after running an upgrade(I believe something in the kernel was updated, not sure), and after a reboot, it no longer worked. Tried to make clean, and then make but this time I got this error - 

```


make -C /lib/modules/4.8.0-39-generic/build M=/home/sarbajit/Files/Wifi patch/rtlwifi_new-rock.new_btcoex modules
make[1]: Entering directory '/usr/src/linux-headers-4.8.0-39-generic'
arch/x86/Makefile:140: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target 'patch/rtlwifi_new-rock.new_btcoex'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.8.0-39-generic'
Makefile:57: recipe for target 'all' failed
make: *** [all] Error 2




```

Any suggestions?

---

### Post by jeremy31 on 2017-03-07
Your kernel doesn' t need that github module
Just do a check to see what ant_sel needs to be set to
```
iwlist scan | egrep -i 'ssid|quality'
```

That will show the Access Points and the reception, then we will unload the module and try the first parameter option
```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=1
```
```
iwlist scan | egrep -i 'ssid|quality'
```

The results from the scan may be the same as original or better but we will check the last option for ant_sel

```
sudo modprobe -r rtl8723be
```
```
sudo modprobe rtl8723be ant_sel=2
```
```
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 was the best then do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

If ant_sel=2 was the better option
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

---

### Post by kc1di on 2017-03-07
Hi saha96 and welcome to Ubuntu,

This ask ubuntu page may be of help in getting you going.  [http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work]("http://askubuntu.com/questions/635625/how-do-i-get-a-realtek-rtl8723be-wireless-card-to-work")
But first give the output of this command : ```
rfkill list
```

---

### Post by saha96 on 2017-03-07
Output is 

```


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy3: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

---

### Post by saha96 on 2017-03-07
Setting ant_sel=1 seems to have worked. Signal quality for my home network is 70/70 with ant_sel=1 while it is 40/70 for ant_sel=2. Thanks a lot!

---

### Post by kc1di on 2017-03-07
Glad it works for you, enjoy :)

---

