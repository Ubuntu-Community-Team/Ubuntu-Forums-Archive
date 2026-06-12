---
title: "Wireless suddenly stops working"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by tylersticka on 2007-02-18
So I've had my wireless card working on my Xubuntu laptop for several weeks (thanks to the fine people at this forum), and I've had no significant problem.

Then, today, it stopped working!

There are only a few things that happened between it working, and it not working at all:

- I reinstalled Wine
- I closed the laptop lid (Gnome-Power-Manager is installed)
- I plugged in AC power with the lid closed
- I opened the lid upon returning to the computer

That's all that happened between it working and it not working. Wireless internet is working fine on all other computers in the house, nothing has been altered on the router.

When I attempt to sudo /etc/init.d/networking restart it will attempt a DHCP request and then drop out. If I specify a static IP address with tested and working values, it will hang before the DHCP request. Wifi-Radar shows me connected with a DHCP-obtained IP, but opening Firefox the internet just stops at "Looking Up" and never gets any further.

Any suggestions would be greatly appreciated, thank you for your time!

---

### Post by tylersticka on 2007-02-19
More information...

Network Settings is set to a Manual Configuration, this has worked for the last two weeks with no problems.

Wifi-Radar shows the signal as being "Master," connected and configured for that IP.

ifconfig returns this:

```
ath0      Link encap:Ethernet  HWaddr 00:0D:54:99:1E:2E  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:54ff:fe99:1e2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4827 (4.7 KiB)  TX bytes:18660 (18.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11391 (11.1 KiB)  TX bytes:11391 (11.1 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-54-99-1E-2E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3233 errors:0 dropped:0 overruns:0 frame:43
          TX packets:1171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:247219 (241.4 KiB)  TX bytes:66834 (65.2 KiB)
          Interrupt:11 
```

iwconfig returns this:

```
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"spamlives"  Nickname:"spamlives"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:4E:A8:89   
          Bit Rate:11 Mb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by eppoh on 2007-02-19
Did you update your kernel recently to -11? If so, go back to -10.  11 broke some cards

---

### Post by sdide on 2007-02-19
Hey,

That seems wierd. Your ath0 seems up and connected, you recieve and transmit bytes.

Please post output from 

# ip route 

# cat /etc/resolv.conf

---

### Post by tylersticka on 2007-02-19
I haven't updated to -11 from -10... it's taken me a while to get 10 working the way I want it to, so that probably wouldn't be in my best interest.

Oddly, I'm on my school network now and it's working fine. I'm wondering if it was some power management hiccup... we'll see if it's resolved itself when I get back home and try to connect to that network once more. Once there, I'll post the results of the commands you mention above.

Thanks for your help so far!

---

### Post by tylersticka on 2007-02-20
Still not working from home, I still can't figure out why.

> **sdide said:**
> Hey,

That seems wierd. Your ath0 seems up and connected, you recieve and transmit bytes.

Please post output from 

# ip route 

# cat /etc/resolv.conf

ip route:
```
192.168.1.0/24 dev ath0  proto kernel  scope link  src 192.168.1.109  default via 192.168.1.1 dev ath0
```

cat /etc/resolv.conf:
```
nameserver 4.2.2.4
nameserver 4.2.2.5
nameserver 4.2.2.6
```

---

### Post by tylersticka on 2007-02-20
Fixed!

I apologize for wasting everyone's time who helped on this, but apparently it was the router after all. After unplugging the modem and router for thirty seconds, then plugging it in again, Swiftfox was able to talk to the internet again.

For any other beginners like myself who may stumble upon this thread, the lesson learned is that even if your Ubuntu/Xubuntu machine is the only one in the house unable to connect to the internet wirelessly, that doesn't mean you can rule out the router being the issue. Try a reset of the router anyway!

Thanks for all your help. :-)

---

### Post by tylersticka on 2007-06-13
This problem actually popped up a couple more times, which I had never had happen with any other wireless receiver.

I thought I'd mention that this problem and others were solved simply by switching from wifi-radar to wicd, which I talk about on [this thread]("http://ubuntuforums.org/showthread.php?t=357749&page=2#post2838731").

---

