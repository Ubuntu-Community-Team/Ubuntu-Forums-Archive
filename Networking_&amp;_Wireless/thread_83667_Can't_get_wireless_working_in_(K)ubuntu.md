---
title: "Can't get wireless working in (K)ubuntu"
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by Mikke on 2005-10-29
I've been trying to get (k)ubuntu to connect to my wireless network. I must have read just about every forum post there is on the subject and nothing helps. I have tried both Kubuntu 5.10 and 5.04 as well as Ubuntu 5.10. My hardware is recognised and the KWifimanager finds my network and even says "Connected to: MYNETWORK" - but I can't use the net and my router can't see my computer.

I've tried all the usual suggestions on the forums like putting dashes after every 4th character in the WEP and so on. I've tried changing the key on my router from 10-digit to hexidecimal to unsecured- in short I believe I've tried everything...

I have tried all of this using live CD's since I don't want to install til i'm sure i can get on the net. I read on one forum post that the live CD doesn't work with wifi- can anyone confirm or deny this?

I've tried using the GUI in both Gnome and KDE, and also from the command line using:

sudo iwconfig wlan0 essid MYNETWORK key 1234567890
sudo ifconfig wlan0 up
sudo dhclient wlan0

this gives me the messages "unknown hardware address type 776" then "no working leases in persistent database".

I also tried copying my interfaces file from MEPIS (which I'm using right now and am connected to my wifi) into (K)ubuntu, again with no luck.

When I asked about this in the Kubuntu forums, someone recommended a piece of software called wifi-radar. It didn't work in (K)ubuntu, and when I tried the exact same settings in MEPIS it did. 

Why would the exact same configuration that works in MEPIS not work in Ubuntu? Am I doing something wrong here or does wireless just not work at all with (K)ubuntu???

---

### Post by davmac on 2005-10-29
I've had my IPW2100 card working under Ubuntu and Kubuntu without any problems.

To me it sounds like a WEP/Encryption problem. Have you tried turning WEP off for a short while, just to see if that is what is causing the problems?

If you open up a terminal and type in the followiwng three commands;

iwconfig
ifconfig
cat /etc/resolv.conf

...what output do you get?

Regards,

Dave Mac

---

### Post by Mikke on 2005-10-29
Hi, here's the output you asked for (this is when I first log in without configuring anything)

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:44/100  Signal level:21/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:31337 (30.6 KiB)  TX bytes:31337 (30.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:6E:35:10
          inet6 addr: fe80::211:95ff:fe6e:3510/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000

ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

Then I set up my network using wifi-radar, with exactly the same settings which work fine under MEPIS and I get this output:

> ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"2WIRE479"  Nickname:"2WIRE479"
          Mode:Master  Frequency:2.437 GHz  Access Point: 00:11:95:6E:35:10
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:44/100  Signal level:21/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:305227 (298.0 KiB)  TX bytes:305227 (298.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:6E:35:10
          inet6 addr: fe80::211:95ff:fe6e:3510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1026 (1.0 KiB)
          Interrupt:16 Base address:0x4000

ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

I also have a few screenshots. The first is my settings in the Ubuntu wireless config GUI. It's all set up and connected but couldn't get an IP address:

[IMG]http://fluidd.com/random/wifi2.png[/IMG]

Same story in wifi-radar:

[IMG]http://fluidd.com/random/wifi1.png[/IMG]

And just to prove I'm not crazy here's wifi-radar running under MEPIS with exactly the same settings (and it works just fine!):

[IMG]http://fluidd.com/random/wifi3.png[/IMG]

Yes I know one says "managed" and the other says "master" but I've tried it every which way....

And to answer your other question yes I have tried it with no key (you can see I don't care about security cos I just gave you my key!)

---

