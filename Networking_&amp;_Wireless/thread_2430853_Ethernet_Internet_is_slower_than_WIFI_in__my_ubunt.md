---
title: "Ethernet Internet is slower than WIFI in  my ubuntu 18.04.3 LTS"
date: 2019-11-08
forum: Networking &amp; Wireless
---

### Post by nicktz4 on 2019-11-08
Hello everyone,i recently changed from Windows to Ubuntu,and i have a problem.
My Wifi internet is working perfectly. This is how it must work.But ethernet,is much slower,some pages wont even load.
Do you have  an idea how could i  make Ethernet work fine?I have seen some "solutions" but none worked.
Thanks

---

### Post by ajgreeny on 2019-11-08
Hi nicktz4, and welcome to the forums.

So what are these "solutions" you have tried unsuccessfully, and also what is the hardware you're using?

Please show us the output of ***inxi -Fzx*** in terminal. 
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 
See my signature below for a **How-to**

---

### Post by nicktz4 on 2019-11-08
Hello Master,thanks for your welcome.



so what are these "solutions" you have tried unsuccessfully: i wrote on /etc resolve.conf  #nameserver 127.0.0.53
                                                                                                                                    nameserver 8.8.8.8
                                                                                                                                    nameserver 8.8.4.4

My hardware is:  Lenovo Legion Y530-15ICH (i7-8750H/8GB/1TB + 128GB/GeForce GTX 1050/FHD/W10) 

```


System:    Host: nicktzpc Kernel: 5.0.0-32-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.3 LTS
Machine:   Device: laptop System: LENOVO product: 81FV v: Lenovo Legion Y530-15ICH serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0R32862 WIN serial: N/A
           UEFI: LENOVO v: 8JCN52WW date: 06/14/2019
Battery    BAT0: charge: 19.1 Wh 37.0% condition: 51.6/52.5 Wh (98%)
           model: SMP L17M3PG1 status: Discharging
CPU:       6 core Intel Core i7-8750H (-MT-MCP-) 
           arch: Skylake rev.10 cache: 9216 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26496
           clock speeds: max: 4100 MHz 1: 900 MHz 2: 900 MHz 3: 900 MHz
           4: 900 MHz 5: 900 MHz 6: 900 MHz 7: 900 MHz 8: 900 MHz 9: 900 MHz
           10: 900 MHz 11: 900 MHz 12: 901 MHz
Graphics:  Card-1: Intel Device 3e9b bus-ID: 00:02.0
           Card-2: NVIDIA GP107M [GeForce GTX 1050 Mobile] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.4 )
           drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 2560x1080@59.98hz, 1920x1080@60.03hz
           OpenGL: renderer: GeForce GTX 1050/PCIe/SSE2
           version: 4.6.0 NVIDIA 430.26 Direct Render: Yes
Audio:     Card-1 Intel Cannon Lake PCH cAVS
           driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 NVIDIA GP107GL High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k5.0.0-32-generic
Network:   Card-1: Intel Wireless-AC 9560 [Jefferson Peak]
           driver: iwlwifi bus-ID: 00:14.3
           IF: wlp0s20f3 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 port: 3000 bus-ID: 07:00.0
           IF: enp7s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1128.2GB (7.1% used)
           ID-1: /dev/nvme0n1 model: RPFTJ128PDD2EWX size: 128.0GB
           ID-2: /dev/sda model: WDC_WD10SPZX size: 1000.2GB temp: 0C
Partition: ID-1: / size: 116G used: 74G (68%) fs: ext4 dev: /dev/dm-0
           ID-2: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A gpu: 0.0:48C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 338 Uptime: 1:22 Memory: 2085.1/7846.0MB
           Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 


```

---

### Post by ajgreeny on 2019-11-08
[B]I wrote on /etc resolve.conf #nameserver 127.0.0.53
nameserver 8.8.8.8
nameserver 8.8.4.4[/B]

I am not completely sure what you mean by this in your post.  Please tell us in detail what you edited and how you did this as on my system at least, there is no **/etc/resolve.conf **file. There is, however, an **/etc/systemd/resolved.conf** file but it does not have lines as you show; in fact all lines in mine are commented out.

Assuming you are using a full install of one of the Ubuntu family with a complete GUI, it is often easier to change your nameserver using the network-manager by clicking on the network icon in the panel, adding the 8.8.8.8 and 8.8.4.4 (google's public DNS nameservers) as your primary and secondary DNS

---

### Post by nicktz4 on 2019-11-08
[B]In my system there is /etc/resolve.conf.I just found that i had copy that on /etc/resolv.conf 
i Delete the texts from there and i add them on /etc/resolve.conf
[/B]i also changed IPv4 DNS from automatic to 8.8.8.8. Now i think its working Perfectly.
Thanks

---

### Post by ajgreeny on 2019-11-08
Ah-ha !!

It was ***/etc/resolv.conf*** that you changed which is why I didn't find the original ***/etc/resolve.conf*** file you mentioned.
It just shows how easy it can be to mess up your system by editing system files when you're not completely sure about the possible results of doing so.

Anyway, I'm delighted that you managed to sort out the problem and thanks for marking it as SOLVED.

---

