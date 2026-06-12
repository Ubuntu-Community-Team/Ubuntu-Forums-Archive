---
title: "Intel Pro IPW3945 and Gutsy"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by tedrow on 2007-11-06
Full disclosure - I'm a Ubuntu noob, functionally literate with Unix from 10 years ago.

New Dell Latitude D630, XP-Pro original load.  Loaded Dapper but no wireless, so scrapped that and went to Gutsy after 10/18 release.  Took default install option from LiveCD, no swap-space (4gbs memory) only failure was security.  Otherwise, seemingly good install.

Now booted to 7.10 Kernal 2.6.22-14-generic - still no wireless.  Network Mangler indicates the router target is valid, WAP-Personal key is OK, auto DHCP correct, and Network tools used to ping my router - no response.  WiFi laptop light blinks fast and constantly.  Receive packets constantly rise.

I'm stumped - I've studied most/all of the ipw3945 posts, no help.  Tried 
sudo apt-get install linux-restricted-modules
but the command line doesn't find the restricted modules.

Ideas, please?  And, thanks for your help.
------- terminal output below ----

lshw -C network:
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:c2:88:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:0b:c8:a5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes
------------------
iwconfig:
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:213   Missed beacon:0
----------------
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1C:23:0B:C8:A5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:C2:88:D4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:219 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 Memory:f9fff000-f9ffffff 

eth1:avah Link encap:Ethernet  HWaddr 00:1B:77:C2:88:D4  
          inet addr:169.254.9.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 Memory:f9fff000-f9ffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)
----------------
sudo iwlist eth1 scan:
eth1      Scan completed :
          Cell 01 - Address: 00:0F:B3:35:1D:B7
                    ESSID:**{neighbor router - deleted}**
          Cell 02 - Address: 00:15:05:26:97:07
                    ESSID:**{neighbor router - deleted}**
          Cell 03 - Address: 00:14:51:6B:BD:BB
                    ESSID:"6bbdbb" **{MINE}**
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-74 dBm  Noise level=-74 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 236ms ago
          Cell 04 - Address: 00:11:95:19:D9:CA
                    ESSID:**{neighbor router - deleted}**
---------------
sudo iwconfig eth1 essid "myrouter":
...returns no error, and network admin reflects correct target
--------------
sudo dhclient eth1:
... chews awhile, eventually responds "No DHCPOFFERS received.  No working leases in persistent database - sleeping."
----------------
dmesg | grep ipw3945:
detects the connect and the geography.
-----------
lspci -nn:
returns a valid entry for the network controller.

---

### Post by elctb on 2007-11-07
I have the same laptop (Dell latitude D630).

What ipw3945 driver version are you using ?

I had no luck using the stable driver from Intel's site. I downloaded version 1.2.2 from this site :
    [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

And now my wireless works perfect. I also removed the network-manager since it got confused a few times.

I'm using kenel 2.6.23.1 that I built myself to get sound working.

---

### Post by tedrow on 2007-11-08
Thanks for the response, elctb - I've read everything else you put in here in wireless, but did not completely understand it.

IPW3945 driver, per lshw is:

configuration: broadcast=yes driver=ipw3945 **driverversion=1.2.2mp.ubuntu1** firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

I don't understand yet what that "unassociated" means yet, wonder if it is part of my problem.

I don't know how else to verify driver version, so I'll assume based on lshw that I have the same version you do.

But that raises another question: when you loaded Gutsy - what option did you use?  I brought up the LiveCD - played in the product a few minutes, then loaded the generic option.

Part of my problem is weak Linux knowledge - I have a lot of research to digest before I can do anything like my own kernal build.  I'll pick up an Ubuntu OS book at lunch to determine how to remove the network manager.  But - if you can get it running, I should be able to do so as well.  For the moment, I'm not concerned about sound, that will come later.  Right now - I can't cut the Mickeysoft cord until I get the wireless working - everything else is low priority.

Thanks
tedrow

---

### Post by elctb on 2007-11-08
Oops

---

### Post by elctb on 2007-11-08
sudo dhclient eth1:
... chews awhile, eventually responds "No DHCPOFFERS received.  No working leases in persistent database - sleeping."

I think you got your wireless card working. This message means no one replied to your DHCP request. It could be that myrouter doesn't have a dhcp server running on it. I would try using a static ip address and see if it works. You need an ip address in the same subnet as myrouter.

If that doesn't work, dothe following"
sudo ifconfig eth1 up
sudo wireshark &
    Then capture packets on eth1
sudo dhclient eth1

(wireshark is a program that allows you to see all ip traffic. You can install it with synaptic).
Wait until you get the "No DHCPOFFERS" message, stop the capture and see if you received anything on eth1.

Also, I wonder if network-manager is getting confused. I had all kinds of problems when it was running. To remove it do the following:
    . sudo synaptic
    . Search for network-manager
    . Select network-manager and mark for complete removal
    . Apply

---

### Post by elctb on 2007-11-08
I forgot to mention I believe you need to configure wep/wpa for dhcp to work.

---

### Post by tedrow on 2007-11-09
Your continued assistance is appreciated.  More details:

I'm hanging off an Apple Airport Wireless router that services 4 machines in the house - my wife's Vista PC, my Mac and this dual-boot laptop running XP-Pro / Ubuntu 7.10.

Up under Gutsy I set a unique static IP (10.0.1.10) and a netmask equal to the Mac (255.255.255.0) and my router is 10.0.1.1.

Under 'normal' operations, Vista and XP and the Mac all connect using dhcp using WAP-Personal with a key - automatically, successfully and stable.

With a static IP under Gutsy - no bueno.  Network Tools Ping does not find the router Pinging 10.0.1.1 or find the Mac at 110.0.1.4,  but the GUI for net-tools (eth1) does show traffic in and out (some, not as many packets as I might expect) and the WiFi laptop idiot light flickers fast (under normal ops, it is on constantly.)

I removed Network Manager totally - no change.  Couldn't start Wireshark - don't see it is Synaptics list altho what we need to know may be found in the Net-tools data.  I agree the wireless net-card is there, and alive, but not successfully shaking hands with anything.

I'm still lost..... but thanks for your help.

tedrow

---

### Post by elctb on 2007-11-09
To install wireshark using synaptic you need the universe repository.

Since the command "iwlist scan" finds your router the driver must be working. It could be a buggy or misconfigured 802.11/encryption layer.  Can you disable security/encryption on your router for a few minutes and see if you can connect ? I've only tested my wireless connection with an open access point so I'm not sure encryption works for me either.

Also make sure the ieee802.11 subsystem is version 1.1.11 or newer. You can find out with the modinfo command:
modinfo ieee80211

Don't forget to set the key before running the "sudo dhclient eth1" command:
sudo iwconfig eth1 key <your-key>

---

### Post by jfank on 2007-11-09
I took a look at that website with the instructions, and I don't understand one bit of how to do the drivers.  I'm extremely new to this, and nothing at all makes any sence to me. lol

---

### Post by tedrow on 2007-11-14
elctb -

Went through everything you offered, then felt it was time to go back to a fresh 7.10 load (from format/scratch) and be sure I wasn't working against myself with either a setting or a switch that had been thrown in previous efforts (and forgotten.)

This time, first thing after re-booting to the fresh load - I went directly to the NetworkManager util in the top bar and used it to set the network router and WAP/key -...... and the d*&$ed thing connected instantly.  In fact, every time I reboot the machine, that network connection is up, on and stable by the time the desktop has been released for human interface (I wish my XP load would connect that quick.)

I've gone through all my notes, and I never used the Net-Mgr tool to set the wireless in the first place.  At one point you (reasonably) recommended unloading it to prevent confusion during the testing and configurations we worked through together.  I couldn't figure out how to re-establish that interface to check that avenue out again - hence the rebuild.

I'm up and online, and I want to thank you for your time and help.  I learned a lot following your recommendations.

And, if anyone needs to know:  Intel Pro IPW3945 with Gutsy is A-OK, without any additional loads from other sources - but be sure you use the Network Manager to configure it.

Again, thanks -
tedrow

---

### Post by elctb on 2007-11-15
I'm glad you got it sorted out.

The other thing I had trouble with my D630 was audio. I finally also got it to work, but that's another thread.

---

