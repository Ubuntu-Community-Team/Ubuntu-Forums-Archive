---
title: "Ethernet conection stops working after a while"
date: 2023-07-30
forum: Networking &amp; Wireless
---

### Post by androy518 on 2023-07-30
```
OS: Ubuntu 23.04 x86_64
Host: HP Pavilion Laptop 15t-cs200
Kernel: 6.2.0-26-generic
Uptime: 1 hour, 2 mins
Packages: 3616 (dpkg), 40 (flatpak)
Shell: bash 5.2.15
Resolution: 1920x1080
DE: GNOME 44.3
WM: Mutter
WM Theme: Adwaita
Theme: Yaru-purple-dark [GTK2/3]
Icons: Yaru-purple [GTK2/3]
Terminal: gnome-terminal
CPU: Intel i7-8565U (8) @ 4.600GHz
GPU: Intel WhiskeyLake-U GT2 [UHD Graphics 620]
Memory: 8412MiB / 31968MiB
```

Recently, the ethernet connection on my laptop has stopped working properly. When I restart my computer, it works properly for a while but then stops working after a period of time even though the Ethernet symbol still shows that it is connected. When I turn it off and on again, the symbol has 3 dots in front of it for a while then I get a notification that says "Connection failed" and "Activation of network connection failed". I get 3 - 5 of those notifications before the Ethernet turns off automatically. The WiFi works normally.

```
ifconfig -a
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 80:e8:2c:1c:32:7b  txqueuelen 1000  (Ethernet)
        RX packets 1743554  bytes 961956533 (961.9 MB)
        RX errors 0  dropped 3372  overruns 0  frame 0
        TX packets 2139002  bytes 2229473766 (2.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6217  bytes 530774 (530.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6217  bytes 530774 (530.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.26  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::89fd:d55f:2ef0:f768  prefixlen 64  scopeid 0x20<link>
        inet6 2603:9001:5007:5200:31f0:373f:8213:f7fd  prefixlen 64  scopeid 0x0<global>
        inet6 2603:9001:5007:5200:7637:6f77:ecb4:410e  prefixlen 64  scopeid 0x0<global>
        ether 58:a0:23:96:1b:3f  txqueuelen 1000  (Ethernet)
        RX packets 84248  bytes 36876232 (36.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 136243  bytes 172298048 (172.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; preset: enabled)
     Active: active (running) since Sun 2023-07-30 08:55:16 EDT; 1h 20min ago
       Docs: man:NetworkManager(8)
   Main PID: 776 (NetworkManager)
      Tasks: 4 (limit: 38259)
     Memory: 8.8M
        CPU: 3.068s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;776 /usr/sbin/NetworkManager --no-daemon

Jul 30 10:14:02 Laptop NetworkManager[776]: <info>  [1690726442.9781] device (eno1): state change: prepare -> config (reason 'no>
Jul 30 10:14:02 Laptop NetworkManager[776]: <info>  [1690726442.9787] device (eno1): state change: config -> ip-config (reason '>
Jul 30 10:14:02 Laptop NetworkManager[776]: <info>  [1690726442.9798] dhcp4 (eno1): activation: beginning transaction (timeout i>
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3124] device (eno1): state change: ip-config -> failed (reason '>
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3132] manager: NetworkManager state is now DISCONNECTED
Jul 30 10:14:48 Laptop NetworkManager[776]: <warn>  [1690726488.3136] device (eno1): Activation: failed for connection 'Profile >
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3143] device (eno1): state change: failed -> disconnected (reaso>
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3501] dhcp4 (eno1): canceled DHCP transaction
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3501] dhcp4 (eno1): activation: beginning transaction (timeout i>
Jul 30 10:14:48 Laptop NetworkManager[776]: <info>  [1690726488.3502] dhcp4 (eno1): state changed no lease
```


Things that I have tried
Restarting
 - Works for a while then stops working
Turning it off and on again
 - Does not work
Unplugging the ethernet cable and plugging it back in
 - Does not work
Using a different Ethernet cable
 - Does not work
sudo /etc/init.d/networking restart
sudo systemctl restart networking
sudo systemctl restart NetworkManager
 - Does not work
netplan apply
 - Does not work
nmcli networking off
nmcli networking on
 - Does not work
 - Option to connect to ethernet does not appear in the menu
ifconfig -a
 - eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
 - Not running
sudo ifconfig eno1 up
 - Still not running

Now it is saying that the cable is unplugged in the settings under the wired network.

Does anyone know how to solve this issue?

---

### Post by zaffiro on 2023-07-30
From the log, it looks like something is wrong with the DHCP. Would it be possible to test your Ethernet connection in a different network?

---

### Post by androy518 on 2023-07-30
I do not have another network to do that with.

---

### Post by aljames2 on 2023-07-31
This may be a long-shot, but have you tried checked your router DHCP range of IPs.  If you have a very narrow range of IPs that are all taken by the plethora of stuff in our homes grabbing for the internet, your PC may not have an available IP in your reservation list.  I prefer to give all wired computers a static IP outside the DHCP range.

If you have a switch between your router & PC, have you tried replacing the ethernet cable on both sides of the switch.

Can you post the contents of your /etc/netplan/*.yaml file(s).  There likely is only 1 file here unless you are using, or have tried some network customizations.

---

