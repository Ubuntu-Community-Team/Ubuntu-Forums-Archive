---
title: "avahi problems with wireless?"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by kenobee on 2007-07-13
I am new to ubuntu and am using 7.04 i386  on an AMD Athlon machine I have been working for a few days on getting my edimax ralink usb adaptor to work. I bought it from Linux Emporium and ran their install script which seems to have installed the rt73 driver correctly. My problem when I try to start wireless, I get no DCHP offers. ifconfig shows eth0:avah with an ip address and rausb0:av with an ip address. I can get wireless running by using
sudo  ifconfig eth0 down
sudo ifconfig rausb0 down
sudo ifdown rausb0
sudo ifup rausb0
If it comes up with just rausb0 it will get a DHCP offer and connect. If an av or an avah driver is showing in ifconfig, they will have an ip address and I guess that ip uses one of those to send dhcp and fails. If none are showing, then my wireless will get an ip address and work. I have to repeat these commands a few times until I "get lucky"
I read a thread about disabling AVAHI by setting AVAHI_DAEMON_START=0 in /etc/default/avahi-daemon but it did not work. I poked around and found /etc/network/if-up.d/avahi-daemon. On line 7 it has a comment "dont bother if AVAHI_DAEMON_START=0 in /etc/default/avahi-daemon. the next line sets it to 1. I set it to 0 and re-started but no good still my avah devices appear. I put in exit 0 at the beginning of the script but still my avahi appear on restart. 
Can anyone tell me how to eliminate the rausb0:av and etho:avah neatly? Will I miss AVAHI if I do get rid of it? 
 Some output follows to show what I am getting.

Listening on LPF/rausb0/00:0e:2e:cd:7e:26
Sending on   LPF/rausb0/00:0e:2e:cd:7e:26
Sending on   Socket/fallback
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
ifroot@TV-PC:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:61:95:D9:6F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xed00 

eth0:avah Link encap:Ethernet  HWaddr 00:04:61:95:D9:6F  
          inet addr:169.254.8.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1002 (1002.0 b)  TX bytes:1002 (1002.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:0E:2E:CD:7E:26  
          inet6 addr: fe80::20e:2eff:fecd:7e26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

rausb0:av Link encap:Ethernet  HWaddr 00:0E:2E:CD:7E:26  
          inet addr:169.254.5.136  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:

---

### Post by RHTopics on 2007-07-13
The problem you are having is because of  the "avahi-autoipd" application, not avahi-daemon.

It is a separate package that can be removed using Synaptics, but removing it will also remove the meta-package "ubuntu-desktop".  There also command line arguments you can pass to the running avahi-autoipd daemon to kill it on your rausb0 interface.  See the man page for avahi-autoipd for more information.

If you are manually starting your wireless connection after booting your computer, then avahi-autoipd is starting up before that in the boot process.  Need to ensure the correct module for your network adapter is loaded when the computer is being booted.

I am considering removing the package "avahi-autoipd", but I have not done it yet, so I can't tell you if doing so will cause any bad side effects.

---

### Post by RHTopics on 2007-07-13
Just had a another possible reason that avahi-autoipd is being started.  Your wireless access point maybe your problem.  The times when avahi-autoipd has started up on me is when my wireless router was turned off.  May want to check the signal strength of the access point you are trying to connect to.

---

### Post by kenobee on 2007-07-14
Thanks very much for the reply. The signal strength is very good - 2 metres away from router. I tried "ifup rausb0" then "avahi-autoipd -k rausb0" as you suggested. Sure enough rausb0:av disappears on an ifconfig but when I try "dhclient rausb0" I still get no dhcp offers and an ifconfig shows pesky rausb0:av alive and well again. Any more advice? on gently disabling avahi-autoipd for rausb0 without  causing repercussions elsewhere in the system?

---

### Post by RHTopics on 2007-07-14
I would consider avahi-autoipd a symptom of an underlying problem of not being able to reliably get an IP address from your DHCP server.

Is your router also a switch where you could run a cable to your computer?  If so check and see if you get a IP address assigned when connecting through eth0.  If it consistently assigns an IP address without avahi-autoipd getting in the way, then I would like stated before re-verify that the default rt73 driver provided by Ubuntu is blacklisted and the driver provided with your network adapter is being loaded.

If the driver looks correct, then do a search in this sub-forum on the rt73 driver.  There may something you can tweak about it that will allow you to get reliable connections.

---

### Post by kenobee on 2007-07-15
Thanks again for the help. Yes you are right about avahi-autoipd. The rausb0:av only comes up AFTER the wireless fails to connect. I also notice on the first attempt to ifup after a re-boot, the activity light on the usb wireless dongle remains off, whereas after ifconfig down followed by ifdown followed by ifup, the activity light flashes during DHCP DISCOVERY. However, that  little trick for getting connected no longer works at all. So I cannot get wireless any more.

 lsmod | grep rt73 only reveals usbcore and rt73 drivers installed.
I see what you mean about the finger of suspicion pointing to router. It is a BTVOYAGER2110. It works fine on my window xp laptop and also I loaded windows into the AMD to make sure all my hardware was OK and it also worked fine with it. I have checked the wep key and name a hundred times. I am really stuck here. I may re-post as it is not really an avahi problem as you helped confirm.

---

### Post by kenobee on 2007-07-16
I am finally beginning to make progress. Sorry ahavi not your problem. I had two problems working against me. One was encryption. I tried removing it from time to time but did not like leaving it off as 2 other machines are on the network. When I had it off the other problem sometimes reared its head. Anyway the problem was WEP AUTHTYPE set to SHARED on my Ubuntu /etc/Wireless/RT73STA/rt73sta.dat file. I changed it to OPEN as is the router and also the windows systems and I get connected. However there is still one problem. When I boot up and then try ifup rausb0 initially it will not work. I can see that the usb light is not flashing so there is no wireless activity. There is only one driver installed (rt73) no bad drivers as far as I can see. However if i ifdown and up a few times suddenly the usb light starts to flash, I get a DCHPACK and I am up. Anyone got an idea as to why??

---

### Post by mechdave on 2007-10-21
I too had the same problem with the eth1:avah virtual interface. The answer was so simple I overlooked it a couple of times! :(  All I had to do was uncheck the radio box "Automatic Service Discovery" in System --> Administration --> Network under the General tab! 
I spent a couple of hours finding that obscure one :( Much happier now, the wireless comes straight up on boot without any problema at all :) I hope that is your problem too...

Cheers,
              Mechdave

---

