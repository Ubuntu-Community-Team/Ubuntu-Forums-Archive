---
title: "Kubuntu Edgy + Inspiron 8600 + Intel PRO/Wireless Problem"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by jmacdonagh on 2007-02-01
So I've had wireless working just fine when I went from Dapper to Edgy. However, I recently reinstalled Edgy straight from the disk, and haven't had much success with wireless.

I first tried to use Kubuntu's Wireless Assistant, since it worked fine before without any configuration. However, connection would fail no matter what I tried.

Then I moved on to the Network Settings applet in System Settings. I manually entered the ESSID and WEP key and hit Apply. It sits there for a while (attempting to get an address) and never gets one. I temporarily fixed the issue yesterday by going to the Routes tab and entering 192.168.1.1 (IP address of my wireless router) for the Default Gateway. After that, I could enable / disable the network interface and get an IP.

This morning I went to my University and connected to their network. Again, I had to change the Gateway IP address (luckily I knew it). Again, I've never had to do this before.

Now back at home, I can get an IP from my router, but no Internet access. A wired connection straight to the router lets me get Internet.

Anyway, information:

```
$ lspci | grep "PRO/Wireless"
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

```
$ ifconfig -a -v
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:20:EF:66
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe20:ef66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:804997 (786.1 KiB)  TX bytes:168256 (164.3 KiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:0E:35:4E:4B:0B
          inet6 addr: fe80::20e:35ff:fe4e:4b0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:504 errors:43 dropped:43 overruns:0 frame:0
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:229451 (224.0 KiB)  TX bytes:57020 (55.6 KiB)
          Interrupt:7 Base address:0xa000 Memory:faffc000-faffcfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6800 (6.6 KiB)  TX bytes:6800 (6.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Five Minus Two"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:14:6C:3F:4C:34
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-25 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:98  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:5

sit0      no wireless extensions.
```

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Five Minus Two

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I don't know what to do at this point. Any clues?

Thanks,

Johann

---

### Post by jmacdonagh on 2007-02-01
So I've done a little more investigation. Using ifup/ifdown, I've been able to reliably get an IP address. Also, the default gateway automatically fills itself out.

However, Wireless Assistant is still not working. When I use ifup I can see it as connected. I can disconnect using Wireless Assistant. However, whenever I try and connect it says connection failed within 5 seconds (I changed the DHCP timeout in its options to 45 seconds).

Come to think of it, I remember after I re-installed Edgy. The first time I opened Wireless Assistant and typed in my password (for sudo) it opened up but a message popped up saying that I do not have the correct permissions to do wireless administration.

I've tried sudo dpkg-reconfigure wlassistant, but I get the same problem. Anyone have any solutions for wlassistant not working? I might upgrade to Fiesty's new "auto network connector" which seemed to work last time I tried it.

---

### Post by griffjon on 2007-02-14
I'm having this same problem - I have an old system with Dapper and it's doing great, but my new laptop running a fresh install of edgy can't connect to networks without a lot of sudo passwords, ifdown/ups, and handholding - why does edgy have such a problem connecting automagically to the nearest best network like Dapper did?  Is there an easy way to fix this?

---

### Post by cknight on 2007-03-25
I'm still quite new to all this and having problems myself, but something I read somewhere is that if you're ESSID has spaces in it, try putting quotes around your ESSID (in your /etc/network/interfaces file) or renaming it to be without spaces.  Good luck!

---

### Post by rushkoff on 2007-03-29
I'm in Edgy with the same issues. I'm afraid to upgrade to Fiesty, though. 

If I know the IP address of the wireless server, I can find it through Network Settings. And I just tried that on a whim. But the coffee shops and places I go for wireless in general have no idea what their addresses are. So I sit next to Windows people and beg them to let me poke around. 

You think an upgrade to F will cure?

---

