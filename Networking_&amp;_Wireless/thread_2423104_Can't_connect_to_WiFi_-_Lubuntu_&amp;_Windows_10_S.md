---
title: "Can't connect to WiFi - Lubuntu &amp; Windows 10 Surface Go dual boot"
date: 2019-07-17
forum: Networking &amp; Wireless
---

### Post by jbnelson on 2019-07-17
[LEFT][COLOR=#242729][FONT=inherit]Some background info:[/FONT][/COLOR][COLOR=#242729][FONT=inherit]On a Surface Go tethered to iPhone for ethernet.[/FONT][/COLOR][COLOR=#242729][FONT=inherit]

cat /etc/os-release[/FONT][/COLOR][/LEFT]
```
NAME="Ubuntu"
VERSION="19.04 (Disco Dingo)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 19.04"
VERSION_ID="19.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=disco
UBUNTU_CODENAME=disco

```
[LEFT][COLOR=#242729][FONT=inherit]I can connect to the ethernet, but my nm thing in the tray says "wifi networks: Device Not Ready"[/FONT][/COLOR][COLOR=#242729][FONT=inherit]Also, I installed wicd and it says its scanning for wifi networks but can't find any.  Windows 10 wifi works fine.

I'm brand new to Linux, and this is me dipping my toes in with Ubuntu.   Any help at all would be hugely appreciated. Thanks in advance! 

[/FONT][/COLOR][COLOR=#242729][FONT=inherit]uname -r[/FONT][/COLOR][/LEFT]
```
5.0.0-20-generic

```[LEFT][COLOR=#242729][FONT=inherit]

ifconfig -a
[/FONT][/COLOR][/LEFT]
```
enp0s20f0u1c4i2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.10.2  netmask 255.255.255.240  broadcast 172.20.10.15
        inet6 2600:380:547b:756c:ecd0:5a07:651b:e2ae  prefixlen 64  scopeid 0x0<global>
        inet6 2600:380:547b:756c:f9c3:42eb:8d27:c57c  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::e530:577e:be5a:b18d  prefixlen 64  scopeid 0x20<link>
        ether ****************  txqueuelen 1000  (Ethernet)
        RX packets 2195  bytes 1346965 (1.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2258  bytes 341216 (341.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536                                           
        inet 127.0.0.1  netmask 255.0.0.0                                              
        inet6 ::1  prefixlen 128  scopeid 0x10<host>                                   
        loop  txqueuelen 1000  (Local Loopback)                                        
        RX packets 2004  bytes 147422 (147.4 KB)                                       
        RX errors 0  dropped 0  overruns 0  frame 0                                    
        TX packets 2004  bytes 147422 (147.4 KB)                                       
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0                     

wlp1s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500                                      
        ether *****************  txqueuelen 1000  (Ethernet)                           
        RX packets 0  bytes 0 (0.0 B)                                                  
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
[LEFT][COLOR=#242729][FONT=inherit]lshw -C network[/FONT][/COLOR][/LEFT]

```
*-network DISABLED        
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 32
       serial: d8:c4:97:b0:53:29
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.0.0-20-generic firmware=RM.4.4.1.c2-00057-QCARMSWP-1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:139 memory:b1400000-b15fffff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:1
       logical name: enp0s20f0u1c4i2
       serial: 42:9c:28:21:30:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=172.20.10.2 link=yes multicast=yes

```[LEFT][COLOR=#242729][FONT=inherit]
rfkill list all[/FONT][/COLOR][/LEFT]
```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```[LEFT][COLOR=#242729][FONT=inherit]

dmesg | grep ath10

[/FONT][/COLOR]```
[COLOR=#242729][FONT=Arial][    7.547393] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    7.819132] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 168c:3370
[    7.819136] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    7.820045] ath10k_pci 0000:01:00.0: firmware ver RM.4.4.1.c2-00057-QCARMSWP-1 api 6 features wowlan,ignore-otp,no-4addr-pad,raw-mode crc32 e061250a
[    7.891523] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=168c,subsystem-device=3370 from ath10k/QCA6174/hw3.0/board-2.bin
[    7.891925] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    7.966586] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[    7.984500] ath10k_pci 0000:01:00.0: htt-ver 3.56 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    9.010258] ath10k_pci 0000:01:00.0: suspend timed out - target pause event never came
[   10.075286] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   10.521167] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   13.650266] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   13.650273] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   13.732770] ath10k_pci 0000:01:00.0: Could not init core: -110
[   13.964114] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   17.234484] ath10k_pci 0000:01:00.0: wmi command 16387 timeout, restarting hardware
[   17.234501] ath10k_pci 0000:01:00.0: failed to enable idle_ps_config: -11
[   17.234973] ath10k_pci 0000:01:00.0: could not suspend target (-108)
[   17.316160] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started
[   17.656238] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   20.818323] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   20.818335] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   20.900252] ath10k_pci 0000:01:00.0: Could not init core: -110
[   21.107557] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   24.146492] ath10k_pci 0000:01:00.0: wmi command 16387 timeout, restarting hardware
[   24.146507] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   24.147095] ath10k_pci 0000:01:00.0: could not suspend target (-108)
[   24.228965] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started
[   24.440183] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   27.474464] ath10k_pci 0000:01:00.0: wmi command 16387 timeout, restarting hardware
[   27.474480] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   27.476551] ath10k_pci 0000:01:00.0: could not suspend target (-108)
[   27.557557] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started
[   27.796453] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   31.058472] ath10k_pci 0000:01:00.0: wmi command 16387 timeout, restarting hardware
[   31.058485] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   31.059061] ath10k_pci 0000:01:00.0: could not suspend target (-108)
[   31.141546] ath10k_pci 0000:01:00.0: cannot restart a device that hasn't been started
[   33.228110] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   36.434364] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   36.434372] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   36.517144] ath10k_pci 0000:01:00.0: Could not init core: -110
[   38.208434] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   41.298485] ath10k_pci 0000:01:00.0: htt version request timed out
[   41.298495] ath10k_pci 0000:01:00.0: failed to setup htt: -110
[   41.381500] ath10k_pci 0000:01:00.0: Could not init core: -110
[   41.592113] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   44.626426] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   44.626434] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   44.708975] ath10k_pci 0000:01:00.0: Could not init core: -110
[   44.912739] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   47.954518] ath10k_pci 0000:01:00.0: htt version request timed out
[   47.954525] ath10k_pci 0000:01:00.0: failed to setup htt: -110
[   48.036645] ath10k_pci 0000:01:00.0: Could not init core: -110
[   55.216253] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   58.450473] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   58.450481] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   58.532643] ath10k_pci 0000:01:00.0: Could not init core: -110
[   58.736406] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   61.778294] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   61.778306] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   61.860216] ath10k_pci 0000:01:00.0: Could not init core: -110
[   72.216308] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   75.346466] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   75.346475] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   75.428482] ath10k_pci 0000:01:00.0: Could not init core: -110
[   75.632182] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   78.674479] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   78.674488] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   78.757108] ath10k_pci 0000:01:00.0: Could not init core: -110
[   89.216565] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   92.242491] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   92.242500] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   92.324965] ath10k_pci 0000:01:00.0: Could not init core: -110
[   92.528321] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[   95.570477] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   95.570486] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   95.652937] ath10k_pci 0000:01:00.0: Could not init core: -110
[  106.208278] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[  109.394457] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  109.394466] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  109.476865] ath10k_pci 0000:01:00.0: Could not init core: -110
[  109.680406] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[  112.722458] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  112.722467] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  112.805277] ath10k_pci 0000:01:00.0: Could not init core: -110
[  243.232089] ath10k_pci 0000:01:00.0: unsupported HTC service id: 1536
[  246.354422] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  246.354429] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  246.437047] ath10k_pci 0000:01:00.0: Could not init core: -110
    [/FONT][/COLOR]
```
[COLOR=#242729][FONT=inherit]
[/FONT][/COLOR][/LEFT]

---

### Post by likwidoxigen on 2019-08-08
It's been 3 weeks with no reply but i figured I'd point out 

> *-network DISABLED        
       description: Wireless interface
That your wireless network is disabled? Try the shortcut toggle switches on/off on the keyboard? Do you have a hardware on-off switch? wicd also has a "switch off wifi" checkbox that should be empty.

---

