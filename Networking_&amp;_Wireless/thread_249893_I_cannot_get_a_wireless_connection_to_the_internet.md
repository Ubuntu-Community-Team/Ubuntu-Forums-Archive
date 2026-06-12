---
title: "I cannot get a wireless connection to the internet"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by tomduffy on 2006-09-03
Any help would be appreciated, I have got a wireless ZyDAS 1211 card in my desktop that will not connect to the internet. I used the Linux drivers that came with the card. I can see the card has been picked up and has installed Wireless connection eth1 in networking. I have configured this and entered the essid and wep key as Hex but still no look. I have run the usual commands but I am not really very good at disifering the outputs. can anybody see from the outputs below what might be the problem. I am currently connected using ethernet cable and this works fine but I have disabled this to see if it would help but no difference. I have put the outputs with Ethernet activated and deactivated.

With Ethernet Deactivated
sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11b/g NIC  ESSID:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:72/100  Signal level:72/100  Noise level:7/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3640  Invalid misc:10   Missed beacon:0

sit0      no wireless extensions.

 sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:02:72:56:2C:7A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0ace:1215 ZyDAS

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:4A:BE:99
                    ESSID:"BTHomeHub-146A"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=100%,LinkQuality:24%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:14:A4:64:6D:43
                    ESSID:"WANADOO-4615"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Extra:SignalStrength=47%,LinkQuality:80%
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20

---

### Post by tomduffy on 2006-09-03
Appologies for all the smilies I don't know why they are on the thread but I got a message saying I used to many and I didn't know I had used any?, here is the outputs with ethernet activated. ](*,) 

With Ethernet activated

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      802.11b/g NIC  ESSID:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality:55/100  Signal level:50/100  Noise level:7/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30940  Invalid misc:28   Missed beacon:0

sit0      no wireless extensions.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:08:01:23:78
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:8ff:fe01:2378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23100 (22.5 KiB)  TX bytes:4658 (4.5 KiB)
          Interrupt:9 Base address:0xcf00

eth1      Link encap:Ethernet  HWaddr 00:02:72:56:2C:7A
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)
:confused:

---

### Post by tomduffy on 2006-09-04
Come on people, someone must know how. Beginning to think Windows XP is the answer after all:grin:

---

### Post by MrHorus on 2006-09-04
Where did you enter the essid and key, was it a GUI window or the console?

---

### Post by tomduffy on 2006-09-05
First of all I went into Tools admin networking from the dropdown menu, clicked on wireless connection properties and configured it in there. I also edited the Etc/Network interface file (because I read I should try this), that file now looks like this
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid BTHomeHub-146A
wireless-key **********
wireless-channel 11
wireless_mode Managed


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid BTHomeHub-146A
wireless-key **********
wireless-channel 11
wireless_mode Managed

auto eth0

---

