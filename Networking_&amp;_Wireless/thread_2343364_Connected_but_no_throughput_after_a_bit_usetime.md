---
title: "Connected but no throughput after a bit usetime"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by capt.chuffy on 2016-11-15
Hello,

I got my XPS 13 9360 Developer Edition last Saturday. It had preinstalled Ubuntu 16.04 LTS. I did sudo apt-get update, upgrade and dist-upgrade.

My problem is that I get a connection to my router but when i download or use the internet for a bit(a minute or so) it just can't get a connection to the internet. The Laptop and Router are still connected.I tried updating the driver but it didnt work then anymore.

It might be some incompatibilty between the router and the driver cause i did a bit of testing. It works on Windows without problems. In my university there is one room(one router) where i can use the internet without any problems on Ubuntu too.
So i would conclude that the driver has some setting activated that might let it lose the connection or lets it stop getting data.

Here is the output of
```
lshw -c network
```
...
```

  *-network               
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3a:00.0
       logical name: wlp58s0
       version: 32
       serial: 9c:b6:d0:d1:73:f9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-47-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 ip=192.168.88.113 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:282 memory:dc000000-dc1fffff

```
Here is the output of
```
[COLOR=#000000][FONT=&amp]ifconfig -a[/FONT][/COLOR]
```
...
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:319540 (319.5 KB)  TX bytes:319540 (319.5 KB)


wlp58s0   Link encap:Ethernet  HWaddr 9c:b6:d0:d1:73:f9  
          inet addr:192.168.88.113  Bcast:192.168.88.255  Mask:255.255.255.0
          inet6 addr: 2003:88:6f22:d07f:f41c:3970:1db4:81f1/64 Scope:Global
          inet6 addr: 2003:88:6f22:d07f:9961:276a:9ed9:77ea/64 Scope:Global
          inet6 addr: fe80::6d8:dc0c:cbc6:4c88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:273424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404811674 (404.8 MB)  TX bytes:13006360 (13.0 MB)

```
Here is the output of
```
iwconfig
```
...
```
lo        no wireless extensions.

wlp58s0   IEEE 802.11abgn  ESSID:"WLAN-AFEF7124GHZ"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 84:9C:A6:AF:EF:2C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0

```
and here is the output of
```
dmesg | grep ath
```
...
```

[  10.132527] ath10k_pci 0000:3a:00.0: enabling device (0000 -> 0002)[   10.135455] ath10k_pci 0000:3a:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.379317] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/cal-pci-0000:3a:00.0.bin failed with error -2
[   10.379583] ath10k_pci 0000:3a:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   10.379590] ath10k_pci 0000:3a:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   12.564211] ath10k_pci 0000:3a:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 2 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[   12.564218] ath10k_pci 0000:3a:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   12.631034] ath: EEPROM regdomain: 0x6c
[   12.631038] ath: EEPROM indicates we should expect a direct regpair map
[   12.631041] ath: Country alpha2 being used: 00
[   12.631042] ath: Regpair used: 0x6c
[   12.641310] ath10k_pci 0000:3a:00.0 wlp58s0: renamed from wlan0
[   46.421921] ath: EEPROM regdomain: 0x8114
[   46.421923] ath: EEPROM indicates we should expect a country code
[   46.421924] ath: doing EEPROM country->regdmn map search
[   46.421925] ath: country maps to regdmn code: 0x37
[   46.421926] ath: Country alpha2 being used: DE
[   46.421927] ath: Regpair used: 0x37
[   46.421928] ath: regdomain 0x8114 dynamically updated by country IE
[  177.225823] ath: EEPROM regdomain: 0x8114
[  177.225826] ath: EEPROM indicates we should expect a country code
[  177.225827] ath: doing EEPROM country->regdmn map search
[  177.225828] ath: country maps to regdmn code: 0x37
[  177.225829] ath: Country alpha2 being used: DE
[  177.225830] ath: Regpair used: 0x37
[  177.225831] ath: regdomain 0x8114 dynamically updated by country IE
[  287.881661] ath: EEPROM regdomain: 0x8114
[  287.881664] ath: EEPROM indicates we should expect a country code
[  287.881665] ath: doing EEPROM country->regdmn map search
[  287.881666] ath: country maps to regdmn code: 0x37
[  287.881667] ath: Country alpha2 being used: DE
[  287.881668] ath: Regpair used: 0x37
[  287.881669] ath: regdomain 0x8114 dynamically updated by country IE
[  432.480844] ath: EEPROM regdomain: 0x8114
[  432.480848] ath: EEPROM indicates we should expect a country code
[  432.480849] ath: doing EEPROM country->regdmn map search
[  432.480851] ath: country maps to regdmn code: 0x37
[  432.480852] ath: Country alpha2 being used: DE
[  432.480853] ath: Regpair used: 0x37
[  432.480855] ath: regdomain 0x8114 dynamically updated by country IE
[  495.954101] ath: EEPROM regdomain: 0x8114
[  495.954103] ath: EEPROM indicates we should expect a country code
[  495.954105] ath: doing EEPROM country->regdmn map search
[  495.954106] ath: country maps to regdmn code: 0x37
[  495.954107] ath: Country alpha2 being used: DE
[  495.954108] ath: Regpair used: 0x37
[  495.954109] ath: regdomain 0x8114 dynamically updated by country IE
[  545.130897] ath: EEPROM regdomain: 0x8114
[  545.130905] ath: EEPROM indicates we should expect a country code
[  545.130910] ath: doing EEPROM country->regdmn map search
[  545.130913] ath: country maps to regdmn code: 0x37
[  545.130917] ath: Country alpha2 being used: DE
[  545.130920] ath: Regpair used: 0x37
[  545.130925] ath: regdomain 0x8114 dynamically updated by country IE
[  799.693046] ath: EEPROM regdomain: 0x8114
[  799.693049] ath: EEPROM indicates we should expect a country code
[  799.693051] ath: doing EEPROM country->regdmn map search
[  799.693052] ath: country maps to regdmn code: 0x37
[  799.693053] ath: Country alpha2 being used: DE
[  799.693054] ath: Regpair used: 0x37
[  799.693055] ath: regdomain 0x8114 dynamically updated by country IE
[ 1596.146181] ath: EEPROM regdomain: 0x809c
[ 1596.146192] ath: EEPROM indicates we should expect a country code
[ 1596.146197] ath: doing EEPROM country->regdmn map search
[ 1596.146202] ath: country maps to regdmn code: 0x52
[ 1596.146207] ath: Country alpha2 being used: CN
[ 1596.146211] ath: Regpair used: 0x52
[ 1954.182765] ath: EEPROM regdomain: 0x8114
[ 1954.182767] ath: EEPROM indicates we should expect a country code
[ 1954.182768] ath: doing EEPROM country->regdmn map search
[ 1954.182769] ath: country maps to regdmn code: 0x37
[ 1954.182769] ath: Country alpha2 being used: DE
[ 1954.182770] ath: Regpair used: 0x37
[ 1954.182771] ath: regdomain 0x8114 dynamically updated by country IE
[ 3097.797416] ath: EEPROM regdomain: 0x8114
[ 3097.797419] ath: EEPROM indicates we should expect a country code
[ 3097.797420] ath: doing EEPROM country->regdmn map search
[ 3097.797421] ath: country maps to regdmn code: 0x37
[ 3097.797422] ath: Country alpha2 being used: DE
[ 3097.797423] ath: Regpair used: 0x37
[ 3097.797424] ath: regdomain 0x8114 dynamically updated by country IE
[ 3146.178743] ath: EEPROM regdomain: 0x809c
[ 3146.178754] ath: EEPROM indicates we should expect a country code
[ 3146.178760] ath: doing EEPROM country->regdmn map search
[ 3146.178764] ath: country maps to regdmn code: 0x52
[ 3146.178769] ath: Country alpha2 being used: CN
[ 3146.178772] ath: Regpair used: 0x52
[ 5542.362267] ath: EEPROM regdomain: 0x8114
[ 5542.362272] ath: EEPROM indicates we should expect a country code
[ 5542.362274] ath: doing EEPROM country->regdmn map search
[ 5542.362276] ath: country maps to regdmn code: 0x37
[ 5542.362278] ath: Country alpha2 being used: DE
[ 5542.362279] ath: Regpair used: 0x37
[ 5542.362281] ath: regdomain 0x8114 dynamically updated by country IE
[ 6387.571623] ath: EEPROM regdomain: 0x8114
[ 6387.571626] ath: EEPROM indicates we should expect a country code
[ 6387.571627] ath: doing EEPROM country->regdmn map search
[ 6387.571629] ath: country maps to regdmn code: 0x37
[ 6387.571630] ath: Country alpha2 being used: DE
[ 6387.571631] ath: Regpair used: 0x37
[ 6387.571633] ath: regdomain 0x8114 dynamically updated by country IE

```

---

### Post by benni-obda on 2016-11-27
i have the same problem but no solution. Please let me know, if you find something.

---

