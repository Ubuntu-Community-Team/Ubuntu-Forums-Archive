---
title: "Unable to connect to Wireless Internet"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by kamlesh30rao on 2008-10-12
Hi,

I am unable to connect to the Wireless Router from my AMD Computer.  This AMD computer has both WinXP and Ubuntu operating system.  I am having NetGear USB Wireless Adapter. Everything works fine from WinXP partition.  On Ubuntu OS, the adapter is being recognized and I can also see all the Wireless connections using the Wireless Assistant tool.  However, my connection to the Wireless Router is failing (Refer the [screenshot]("http://www.flickr.com/photos/22065133@N07/2933916962/") here).  In this case my wireless router name is "Link$ys".

Can you please help me to troubleshoot this problem?

My wireless router is Linksys WRT54G and I have configured the Wireless Security as WPA Personal.  The output of some of the configuration related commands are as given below:

```

amd-ubuntu:~$ uname -a
Linux amd-ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
amd-ubuntu:~$ 

amd-ubuntu:~$ lsusb
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
amd-ubuntu:~$ 

amd-ubuntu:~$ sudo lsusb
Bus 002 Device 002: ID 0846:4260 NetGear, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

amd-ubuntu:~$ sudo ndiswrapper -l
wg111v3 : driver installed
	device (0846:4260) present
amd-ubuntu:~$ sudo modprobe ndiswrapper
amd-ubuntu:~$ 
amd-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

amd-ubuntu:~$ 

```

Please help!

---

### Post by Sava8420 on 2008-10-12
In the terminal run:
```
sudo iwlist wlan0 scan
```
Post results and will be able to help you more.

---

### Post by kamlesh30rao on 2008-10-12
Hi, thanks for your response. Here's the output of iwlist command, you asked for.

```

kamlesh30rao@amd-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:69:84:E0
                    ESSID:"LSHomeRouter"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 02:E0:E5:DF:5D:11
                    ESSID:"LSHomeRouter"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

kamlesh30rao@amd-ubuntu:~$ 

```

Please let me know your response.
Regards,
Kamlesh

---

### Post by Sava8420 on 2008-10-12
Ok so I should have paid closer attention as to your encryption type.  So I will have to refer you to a thread but don't worry as the thread is very direct in setting up networks.  So here ya go: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)  This will show you precisely how to configure the network.

---

### Post by kamlesh30rao on 2008-10-12
Sigggggh! thats manual procedure and lengthy too.  

For the time being, I have disabled Security and enabled MAC Address Filtering.  I am up and running with this setting now.

If I go back to WEP/WPA, then I will refer the link that you provided me.

Thanks once again for your assistance.

Regards,
Kamlesh

---

### Post by Sava8420 on 2008-10-12
> **kamlesh30rao said:**
> Sigggggh! thats manual procedure and lengthy too.  

For the time being, I have disabled Security and enabled MAC Address Filtering.  I am up and running with this setting now.

If I go back to WEP/WPA, then I will refer the link that you provided me.

Thanks once again for your assistance.

Regards,
Kamlesh

So if you decide to change it to WEP encryption I can give you specific commands.  There is good reason for you to learn the terminal and the post I referenced is a good one to learn from as it is pretty complete.  Like I said if you decide to switch to WEP let me know I can make it pretty painless.

---

