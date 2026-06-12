---
title: "WUSB54GP ver 4 problems"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by rose34 on 2007-03-08
Hi All,

Apologies if this is a question that has been asked countless times before, but I can't find the answer by searching the forum or help pages...

I have wanted to try linux for a couple of years, and downloaded Ubuntu version 6.10 yesterday, which is now dual booted on my PC with Windows XP. Everything seems to work fine, apart from my Linksys WUSB54GP version 4 wireless network adapter.

the option of wireless connection shows up in the networking window, and I can ping the router, so it seems as if the adapter is connecting to the router but not the internet? I have tried everything I can think of, including ddisabling the encryption on the router as I read WPA doesn't always work.

If anyone can help with this problem I would be really grateful, I know my way around windows fairly well but have not a clue with linux! However I would really like to learn, and am keen to try any solution suggested.

thank you very much

Joe

---

### Post by Floppyjoe on 2007-03-08
Can you open a terminal window by clicking Applications/Accessories/Terminal and enter the following and post the results here:
```
iwconfig
```
This will show your wireless adapters and any associations with routers with IP addresses listed as well.

---

### Post by rose34 on 2007-03-08
the results for iwconfig are:

lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"Sitecom"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Floppyjoe on 2007-03-08
Ok it looks like you are associated with your router but I was wrong about the IP part.
Enter the following at the terminal to see if you have an IP designated to your wireless interface:
```
ifconfig
```

If you can confirm an IP address here then that means your problem is probably a DNS problem.

---

### Post by rose34 on 2007-03-08
ifconfig brings up the following:

eth0      Link encap:Ethernet  HWaddr 00:13:D3:F7:2A:0D  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4708 (4.5 KiB)  TX bytes:4708 (4.5 KiB)

rausb1    Link encap:Ethernet  HWaddr 00:12:17:7D:D5:B0  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe7d:d5b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:611676 (597.3 KiB)  TX bytes:38636 (37.7 KiB)



my apologies for the delay in replying, I have to reboot into ubuntu, copy the results and then reboot into XP to connect... 

the help is really appreciated, thanks a lot!

---

### Post by rose34 on 2007-03-08
hang on, it seems to have converted some of the code into smilies...

eth0      Link encap:Ethernet  HWaddr 00:13:D3:F7:2A:0D  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4708 (4.5 KiB)  TX bytes:4708 (4.5 KiB)

rausb1    Link encap:Ethernet  HWaddr 00:12:17:7D:D5:B0  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe7d:d5b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:611676 (597.3 KiB)  TX bytes:38636 (37.7 KiB)



this one should be smilie free!

---

### Post by Floppyjoe on 2007-03-08
If you want to connect to your router using the wireless interface I would disable the ethernet(wired) adapter in System/Administration/Networking.

---

### Post by rose34 on 2007-03-08
I've tried disabling the wired adapter, so that the only connection shown is the wireless one - it still has no effect. Because I've tried with it on and off several times to see if it had any effect, it's on at the moment just because that's how I last tried it. Will the results for the wireless connection be different with the ethernet turned off?

---

### Post by Floppyjoe on 2007-03-08
> **rose34 said:**
> I've tried disabling the wired adapter, so that the only connection shown is the wireless one - it still has no effect. Because I've tried with it on and off several times to see if it had any effect, it's on at the moment just because that's how I last tried it. Will the results for the wireless connection be different with the ethernet turned off?
I would think there would be no conflict through which path packets would try to move then.
Both your network adapters show the same IP address.

---

### Post by rose34 on 2007-03-08
so, is the problem a DNS problem then? I'll have another read through that part of the help guide, if you can suggest anything else...

thanks a lot for all the help so far, it really means a lot to get this level of detailed help from someone who knows what they're doing!!

---

### Post by Floppyjoe on 2007-03-08
With your wired adapter disabled use the ping utilities by clicking System/Administration/Network Tools to see if you can ping 82.211.81.186.
If that is successful then try to ping ubuntuforums.org. 
If the latter is unsuccessful then it is a DNS problem.

---

### Post by rose34 on 2007-03-08
With the wired network disabled and trying to ping to 82.211.81.186, I get the message Destination Host Unreachable. 

This is just guesswork, but it seems to me like the wireless adapter is connecting to the router but not the internet? However, I'm using the exact same adapter/router under windows and it works fine, and I have removed all encryption from the router, so I can't see why this would be. Or is it DNS?

---

### Post by Floppyjoe on 2007-03-08
> **rose34 said:**
> With the wired network disabled and trying to ping to 82.211.81.186, I get the message Destination Host Unreachable. 

This is just guesswork, but it seems to me like the wireless adapter is connecting to the router but not the internet? However, I'm using the exact same adapter/router under windows and it works fine, and I have removed all encryption from the router, so I can't see why this would be. Or is it DNS?
If the adapter can get an ip address from the router then it should be able to ping IP addresses on the internet. Are you using DHCP or Static here? Can you ping your router IP address? IF the DNS servers are not set up correctly then you would not be able to ping domain names.

---

### Post by rose34 on 2007-03-08
> **Floppyjoe said:**
> If the adapter can get an ip address from the router then it should be able to ping IP addresses on the internet. Are you using DHCP or Static here? Can you ping your router IP address? IF the DNS servers are not set up correctly then you would not be able to ping domain names.

I'm using Static with the following settings:
IP: 192.168.0.1
Subnet mask: 255.255.255.0
Gateway address: 192.168.0.1



When I ping the above address for the router, I get the following:
joe@joe-desktop:~$ ping -c 4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.039 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.040 ms

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.037/0.038/0.040/0.007 ms




When I ping to a different IP address, such as the one you gave me:
joe@joe-desktop:~$ ping -c 4 82.211.81.186
PING 82.211.81.186 (82.211.81.186) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=1 Destination Host Unreachable
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable
From 192.168.0.1 icmp_seq=4 Destination Host Unreachable

--- 82.211.81.186 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3009ms
, pipe 3

---

### Post by Floppyjoe on 2007-03-08
Just for the sake of curiosity what is in your /etc/resolv.conf file?
```
sudo gedit /etc/resolv.conf
```

This is where your computer stores the DNS server IP addresses.

---

### Post by rose34 on 2007-03-09
> **Floppyjoe said:**
> Just for the sake of curiosity what is in your /etc/resolv.conf file?
```
sudo gedit /etc/resolv.conf
```

This is where your computer stores the DNS server IP addresses.


I apologise for the delay in replying, sleep and university took priority!

When I type in the command given, it opens up what appears to be a blank gedit file - the bar at the top says the file is /etc/resolv.conf, but there is no text or anything, just a blank document

Joe

---

### Post by Floppyjoe on 2007-03-09
Try entering these nameservers into the /etc/resolv.conf file and saving the file.
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

These are OpenDNS nameservers which work fine for me.

---

### Post by rose34 on 2007-03-09
> **Floppyjoe said:**
> Try entering these nameservers into the /etc/resolv.conf file and saving the file.
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

These are OpenDNS nameservers which work fine for me.

just tried that, entering those numbers into the file via gedit and then saving has no effect, other than altering firefox - before modifying the file, when I typed in a web address firefox went straight to the web page not found display, now it takes several minutes before the page comes up? not sure quite what this means.

thanks for all the help once again!

Joe

---

### Post by rose34 on 2007-03-10
I just tried the method suggested in this sticky thread from the forum: [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

Now, when I restart the computer and type in "sudo ndiswrapper -m", I get the message "modprobe config already contains alias directive"

I'm beginning to wonder if I will get this working, or if I will have to return to windows... Does anyone have any suggestions please?

---

### Post by rose34 on 2007-03-11
I finally got it working!

It took reinstalling ubuntu without the wireless adapter plugged in, then plugging it in while the computer restarted after the install - worked fine the minute I logged in and set up the details for the network!

so, if anyone has trouble with this adapter, try reinstalling without the adapter plugged into the usb port - don't know why it worked, but it did!

---

