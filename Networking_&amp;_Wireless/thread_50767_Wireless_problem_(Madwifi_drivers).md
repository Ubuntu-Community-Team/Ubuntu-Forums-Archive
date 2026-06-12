---
title: "Wireless problem (Madwifi drivers)"
date: 2005-07-21
forum: Networking &amp; Wireless
---

### Post by Sniper PT on 2005-07-21
I have follow that tutorial (i have DWL-G650):
[http://ubuntuforums.org/showthread.php?t=36800](http://ubuntuforums.org/showthread.php?t=36800)

What i have did:
0) sudo apt-get install build-essential
1) sudo apt-get install linux-headers-2.6.10-5 and sudo apt-get install linux-headers-2.6.10-5-386
2) i don't have the file in /usr/src folder, so i only have copy the folder (in ubuntu CD) /pool/main/l/linux-source-2.6.10
3) i have try: sudo apt-get install sharutils, but that not works, and i have follow that steps: [http://www.ubuntuforums.org/showthr...stall+sharutils](http://www.ubuntuforums.org/showthr...stall+sharutils)
4) tar jxvf madwifi-cvs-current.tar.bz2
5) sudo make clean
sudo make
sudo make install
6) i have copy the new files (in the new files i doesn't have ath_rate_onoe.ko but i have ath_rate_sample.ko, so i cp and rename...)

I have restart ando still not working...

So, what is wrong?

Thanks in advance

---

### Post by kleeman on 2005-07-21
That is my howto. What do you mean it doesn't work?
what does 
dmesg | grep ath

give.

There is a madwifi wiki with a troubleshooting section here
[http://madwifi.sourceforge.net/dokuwiki/doku.php?id=troubleshooting&DokuWiki=d0ed0ec8988f8595a0dfa418e894d94f](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=troubleshooting&DokuWiki=d0ed0ec8988f8595a0dfa418e894d94f)

Notice the What does ''HAL status 13'' mean? section there.......

---

### Post by Sniper PT on 2005-07-21
There is the result:


ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath_rate_sample: 1.2
ath_pci: 0.9.6.0 (EXPERIMENTAL)
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: H/W encryption support: WEP AES AES_CCM TKIP
ath0: mac 5.6 phy 4.1 radio 4.6
ath0: Use hw queue 1 for WME_AC_BE traffic
ath0: Use hw queue 0 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Use hw queue 8 for CAB traffic
ath0: Use hw queue 9 for beacons
ath0: Atheros 5212: mem=0xfebf0000, irq=5
ath0: no IPv6 routers present


Look what i did in 6) step.

---

### Post by varunus on 2005-07-21
That dmesg output looks exactly like mine, and mine works, so I think you should be good...Try opening a terminal and typing:
```

sudo ifconfig ath0 up
sudo iwconfig ath0 essid <insert SSID of router here>
sudo dhclient ath0

``` 

Does this get you on the net?  If it does, you can try configuring your card from System->Administration->Networking or you can get GTKWifi (its available on these forums in the "3rd party projects" section, very nice wireless config tool).  Good luck.

---

### Post by Sniper PT on 2005-07-21
[QUOTE=varunus]That dmesg output looks exactly like mine, and mine works, so I think you should be good...Try opening a terminal and typing:
```

sudo ifconfig ath0 up
sudo iwconfig ath0 essid <insert SSID of router here>
sudo dhclient ath0

``` 

Does this get you on the net?[/QUOTE]
No..   :-?

---

### Post by varunus on 2005-07-21
Can you post the output of "iwconfig" and "ifconfig" in a terminal after you followed those instructions?

---

### Post by kleeman on 2005-07-21
Look through the whole dmesg output and make sure you do not see

HAL status 13

anywhere. If you do then it means your firmware is not yet supported.
If not then try

sudo lsmod | ath

then what does 

ifconfig

show

and then what does

iwconfig

show?

---

### Post by kleeman on 2005-07-21
Also what are the lights doing on the card?

---

### Post by kleeman on 2005-07-21
btw in step 6) what do you mean that you renamed the ath_rate_sample.ko file.
If the driver has been updated and the make install now produces files with different names then you must leave the names intact just copy them to the correct spot.

---

### Post by Sniper PT on 2005-07-21
when i run:
sudo Ismod | ath
-> That return "Command not found"


**iwconfig:** 

lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"Manteigas"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



**ifconfig:**

ath0       Encapsulamento do Link: Ethernet  Endereço de HW 00:0D:88:C7:22:6D
          endereço inet6: fe80::20d:88ff:fec7:226d/64 Escopo:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:17 dropped:0 overruns:0 frame:17
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          IRQ:5 Memória:ccae0000-ccaf0000

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACKRUNNING  MTU:16436  Métrica:1
          RX packets:8886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8886 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:0
          RX bytes:801619 (782.8 KiB)  TX bytes:801619 (782.8 KiB)




The light is always blinking...


About the step 6):

I have all the 9 new files in the folder /lib/modules/2.6.10/net/ i have copy like your instructions but there ins't the file ath_rate_onoe.ko., is another: "ath_rate_sample.ko"
So, i must copy that file to /lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_rate/onoe/ folder or to  /lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_rate/sample/ ?

---

### Post by kleeman on 2005-07-21
OK the iwconfig looks good. Is Manteigas your router essid? as far as the modules copy goes, check the directory structure created by your make install. If there is a sample subdirectory (/ath_rate/sample/) where the program created the modules then I would guess this is needed in the kernel module tree as well. Strangely I don't have this subdirectory in my tree which is a bit worrying....

Next if you are using dhcp then try

sudo dhclient ath0

and report output....

---

### Post by Sniper PT on 2005-07-21
"Manteigas" is my essid. I have that in file in the sample directory, but the other file (ath_rate_onoe.ko) i don't have...

sudo dhclient ath0 as return:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0d:88:c7:22:6d
Sending on   LPF/ath0/00:0d:88:c7:22:6d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kleeman on 2005-07-21
Make sure the kernel tree structure you get on compilation is the one your copy over i.e. if you have a sample subdirectory then copy this (and its contents) over. Don't change the names or positions in the directory structure of anything.

Reboot and then

sudo ifconfig ath0
sudo iwlist ath0 scanning
sudo dhclient ath0

and report the output from the second and third commands.

---

### Post by Sniper PT on 2005-07-21
When you say "kernel tree structure you get on compilation" is the files created in /lib/modules/2.6.10/net/?

if yes, they are all in same directory... withou sub-folders...

---

### Post by Sniper PT on 2005-07-21
About my last post: if your answer is yes, i must copy all files to the same folder in kernel folder?

There is the outputs:


sudo iwlist ath0 scanning:

ath0      Scan completed :
          Cell 01 - Address: 00:0F:3D:39:19:26
                    ESSID:"Manteigas"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100



sudo dhclient ath0:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0d:88:c7:22:6d
Sending on   LPF/ath0/00:0d:88:c7:22:6d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kleeman on 2005-07-21
Sorry I was wrong about the directory structure. As you say all the modules are in the one subdirectory after the make install command. 

It appears from this link
[http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg04755.html](http://www.mail-archive.com/pld-cvs-commit@lists.pld-linux.org/msg04755.html)

that the driver has changed as of 7/14/05 and the module you have (ath_rate_sample.ko) is new. I don't know at all how this is supposed to work out with the kernel tree so what I would suggest is that you download a version of the driver from BEFORE that date and recompile that. You can find the old drivers here:


[http://madwifi.otaku42.de/2005/07/](http://madwifi.otaku42.de/2005/07/)

they have dates so choose one from before the 14th and see whether you get the modules I listed in my howto or not....

---

### Post by Sniper PT on 2005-07-21
No problem...  ;-) 

I will try with this package: madwifi-cvs-snapshot-2005-07-13.tar.bz2

In 10 minutes i will say something... :-P

---

### Post by Sniper PT on 2005-07-21
With the package madwifi-cvs-snapshot-2005-07-13.tar.bz2 i don't get the modules of your how to...

Are you sure the correct snapshot is before 14/07/2005 ?

---

### Post by kleeman on 2005-07-21
No not sure   :) . Try July 1

---

### Post by kleeman on 2005-07-21
I tried July 1 and it does produce the same list as the how to but leaves ath_rate_sample.ko in /lib/modules/2.6.10/net Just ignore it and copy the other files as in the howto.....

---

### Post by kleeman on 2005-07-21
Btw for future reference by looking at the documentation it appears that a sample subdrectory in /lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_rate/ is needed for ath_rate_sample.ko

---

### Post by Sniper PT on 2005-07-21
I have use the package of 1 July... i have copy, reboot... but i still without internet...

There is some outputs message:

sudo dhclient:

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/ath0/00:0d:88:c7:22:6d
Sending on   LPF/ath0/00:0d:88:c7:22:6d
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database – sleeping.




sudo ifconfig ath0:

ath0       Encapsulamento do Link: Ethernet  Endereço de HW 00:0D:88:C7:22:6D
          endereço inet6: fe80::20d:88ff:fec7:226d/64 Escopo:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:23 dropped:0 overruns:0 frame:23
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          IRQ:5 Memória:ccac0000-ccad0000

sudo iwconfig ath0
ath0      IEEE 802.11  ESSID:"Manteigas"
          Mode:Managed  Frequency:2.442 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6575-7175-6572-6F65-6E74-7261-72   Security mode:restri cted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Sniper PT on 2005-07-21
iwconfig:

lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"Manteigas"
          Mode:Managed  Frequency:2.437 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



ifconfig:

ath0       Encapsulamento do Link: Ethernet  Endereço de HW 00:0D:88:C7:22:6D
          endereço inet6: fe80::20d:88ff:fec7:226d/64 Escopo:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:23 dropped:0 overruns:0 frame:23
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          IRQ:5 Memória:ccac0000-ccad0000

lo         Encapsulamento do Link: Loopback Local
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACKRUNNING  MTU:16436  Métrica:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:0
          RX bytes:40510 (39.5 KiB)  TX bytes:40510 (39.5 KiB)

sit0       Encapsulamento do Link: IPv6 sobre IPv4
          endereço inet6: ::127.0.0.1/96 Escopo:Desconhecido
          UP RUNNING NOARP  MTU:1480  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by kleeman on 2005-07-21
Hmmm, just to check you have two lights flashing together on the card? Did you remove the ath_rate_sample.ko module?

What is strange is that your 
sudo iwconfig ath0

shows a 2.442 GHz and encryption on (key: 6575-7175-6572-6F65-6E74-7261-72)

but later iwconfig gives 2.437 GHz and no encryption.
What does 
sudo iwlist ath0 scanning

give now?

---

### Post by Sniper PT on 2005-07-21
It doen't work....

there is the output:

ath0      Scan completed :
          Cell 01 - Address: 00:0F:3D:39:19:26
                    ESSID:"Manteigas"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100

---

### Post by kleeman on 2005-07-21
Hmm well it seems pretty close to working as iwlist is showing your router and the signal seems fine. The only thing I can see is the mode is not set properly. Try the following:

sudo iwconfig mode Master

sudo dhclient ath0

---

### Post by Sniper PT on 2005-07-22
When i try sudo iwconfig mode Master, it return:
«Error:unrecognised wireless request "Master"»

---

### Post by Sniper PT on 2005-07-22
Ups, i have forget the "ath0"...

sudo iwconfig ath0 mode Master


but still not working... dhclient say it still "sleepijng..."  :-?

---

### Post by kleeman on 2005-07-22
Quick sanity check: It works under Windows right?
What is your router?

---

### Post by Sniper PT on 2005-07-22
Yes.. (right now i'm using another PC with windows)

My router is DI-624 (dlink)

---

### Post by kleeman on 2005-07-22
OK I have the identical router and card to you. Do you know why your router mode is listed as Master, mine is managed. If you log onto your router what does the Home--> Wireless settings show? Howb about Status---> Device Info? Anything interesting in Status--> Logs

---

### Post by kleeman on 2005-07-22
I am near the end of the road on this one. A couple of final suggestions:  try the driver I used from May 24 and report this as a bug to the madwifi mailing list and see what they say:

[http://lists.sourceforge.net/lists/listinfo/madwifi-users](http://lists.sourceforge.net/lists/listinfo/madwifi-users)

---

### Post by varunus on 2005-07-22
Can you try "dmesg | grep ath" in a terminal and post the output here?

It seems that you are able to see the access point when the card scans, but you cannot connect to it.  Try the following:

```
sudo iwconfig ath0 ap 00:0F:3D:39:19:26
```

Then post the output of iwconfig.  Also, try "sudo dhclient ath0" after entering the above.  Do you get internet access?  You almost have it working, don't give up now!

---

### Post by Sniper PT on 2005-07-22
I don't know why is listed as Master...

Router Configuration:
Wireless Radio 	On
SSID : Manteigas	
Channel : 6
Extended Range Mode :Disable
802.11g Only Mode : Disabled
SSID Broadcast : Enabled
Security : 	None

In the log i only see the other PC (with windows) trying connecting.. the PC with ubuntu i don't see anything...

-------


There is the outputs:

dmesg | grep ath

ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: mac 5.6 phy 4.1 radio 4.6
ath0: 802.11 address: 00:0d:88:c7:22:6d
ath0: Use hw queue 0 for WME_AC_BE traffic
ath0: Use hw queue 1 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Atheros 5212: mem=0xfebf0000, irq=5
ath0: no IPv6 routers present


iwconfig

lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"Manteigas"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:3D:39:19:26
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


sudo dhclient ath0

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0d:88:c7:22:6d
Sending on   LPF/ath0/00:0d:88:c7:22:6d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kleeman on 2005-07-22
Your iwconfig shows that the channel being connected to is changing. Your last post shows a different channel from the previous one. It also shows a managed mode whereas last time it was Master.
Try 

sudo iwconfig ath0 channel 06
sudo dhclient ath0

---

### Post by Sniper PT on 2005-07-22
I have install the package with the same date as your...
Reboot...

I have made what you said, in mode Master and Managed... and no Internet...

---

### Post by Sniper PT on 2005-07-23
First, I want apreciate all your help!!!! Thanks!  :grin: 

My problem is very stranger, because i have the same hardware as Kleeman, the same drivers, and no internet connection... maybe the problem is me...  ](*,) 

Must i re-install Ubuntu and try all of begin?


THANKS!!!!!


P.S.: Some consideration:
I have install sharutils by external package (and no apt-get install sharutils)...
I have copy from de Ubuntu CD the linux-source-2.6.10 folder to the /usr/src/....

---

### Post by Sniper PT on 2005-07-23
Hey, look that:

gtkwifi: depends of python2.4-gnome2-extras and it's not installed

I have this message when try install linux-headers (i have try all of the beggining), and it return "This is the last version" and also this message...

I was go to the packages admin of Ubuntu but i don't see that package...

Is that a possible solution for the problem?

---

### Post by kleeman on 2005-07-23
Yeah you have a very strange problem there. Actually the kind of error you get is what I get when I take my laptop on the road and the signals are too weak to connect. Perhaps you might want to try putting the laptop right next to the router and try
sudo dhclient ath0

The missing package is on my system. I have attached my /etc/apt/sources.list as a zipfile if you want to replace yours. After you do try

sudo apt-get update

btw sharutils and linux-source-2.6.10 are also on my system as well. Maybe your problem is that without internet you can only access the cdrom? If so I strongly recommend connecting a cable from your lan port (assuming you have one) to the router to download all this stuff first (you will nedd to configure this network of course ;-).

---

### Post by kleeman on 2005-07-23
Sorry here is the file

---

### Post by Sniper PT on 2005-07-23
I have re-install Ubuntu...
I get from Internet the linux-source-2.6.10 and tranfer with a USBPen
And i have follow all other instructions... and now Internet Works!!!

I also put the router near my PC...

Thanks for all... about the problem, maybe the reason was not install the linux-source-2.6.10 (before i have only copy the folder of the Ubuntu CD)..

---

### Post by kleeman on 2005-07-23
Great! That took an effort  :smile:  :smile:  :smile:

---

### Post by kjkrum on 2005-10-12
[QUOTE=kleeman]Btw for future reference by looking at the documentation it appears that a sample subdrectory in /lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_rate/ is needed for ath_rate_sample.ko[/QUOTE]

I just copied ath_rate_sample.ko over ath_rate_onoe.ko and it seems to work.

---

