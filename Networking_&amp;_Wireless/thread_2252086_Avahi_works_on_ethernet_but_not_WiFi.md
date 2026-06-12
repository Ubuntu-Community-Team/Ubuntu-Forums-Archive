---
title: "Avahi works on ethernet but not WiFi"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by Mustafa_Khan on 2014-11-08
I have a WIFI access point set up in my room which has a wired connection to my raspberry pi and would like to ssh into it through wifi.  

When I'm connected through ethernet to the access point with my laptop, I can connect to the pi using [email]username@pi.local[/email] in terminal.  

But when I'm on the wifi signal, the [email]username@pi.local[/email] method doesn't work and I have to resort to using the IP address of the pi to connect through ssh.

the pi cannot be set up with a static IP address because the DHCP server is not under my control (it is controlled by the residence building administrators).

I am stumped by not being able to connect using the wifi when wired connection to the network on the same subnet allows me to ssh.

Does anybody have any ideas about what is going on?  What should I try to fix the problem?

---

### Post by papibe on 2014-11-09
Hi Mustafa_Khan.

Could you get into the laptop when on Wifi, open a terminal, run these commands and post back the results (you can copy/paste the text)?
```
route -n

avahi-browse -a
```
Regards.

---

### Post by Mustafa_Khan on 2014-11-09
Here's the output for the wifi.  Avahi-browse -a stalled for a while so I had to exit the command through Ctrl-C
```
mustafa@mustafa-ThinkPad:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         141.x.x.x   0.0.0.0         UG    0      0        0 wlan0
141.x.x.x   0.0.0.0         255.255.252.0   U     9      0        0 wlan0
mustafa@mustafa-ThinkPad:~$ avahi-browse -a
+  wlan0 IPv6 mustafa-ThinkPad [28:e3:47:5f:e7:ae]          Workstation          local
+  wlan0 IPv4 mustafa-ThinkPad [28:e3:47:5f:e7:ae]          Workstation          local
^CGot SIGINT, quitting.
mustafa@mustafa-ThinkPad:~$ 



```

---

### Post by Mustafa_Khan on 2014-11-09
Here's the output for the ethernet.  Avahi-browse -a also stalled for this command.
> mustafa@mustafa-ThinkPad:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         141.x.x.x   0.0.0.0         UG    0      0        0 eth0
141.x.x.x   0.0.0.0         255.255.252.0   U     1      0        0 eth0
mustafa@mustafa-ThinkPad:~$ avahi-browse -a
+   eth0 IPv6 mustafa-ThinkPad [20:1a:06:c5:b8:1a]          Workstation          local
+   eth0 IPv4 mustafa-ThinkPad [20:1a:06:c5:b8:1a]          Workstation          local
+   eth0 IPv4 mkhanpi [b8:27:eb:2b:db:d1]                   Workstation          local
+   eth0 IPv4 Samsung ML-1430 @ mkhanpi                     Internet Printer     local
+   eth0 IPv4 aries [d4:be:d9:05:34:e6]                     Workstation          local
+   eth0 IPv4 DAVID                                         _nvstream._tcp       local
+   eth0 IPv4 ARJUN                                         _nvstream._tcp       local
+   eth0 IPv6 Will-Q                                        _mwg-cc._tcp         local
+   eth0 IPv4 saned                                         _sane-port._tcp      local
+   eth0 IPv4 mkhanpi                                       Remote Disk Management local
+   eth0 IPv4 Yang-PC                                       _xrdovertcp._tcp     local
+   eth0 IPv4 CHANGFU                                       _nvstream._tcp       local
+   eth0 IPv4 CC-PC                                         _nvstream._tcp       local
+   eth0 IPv4 Akshay-PC                                     Microsoft Windows Network local
+   eth0 IPv4 Akshay-PC                                     _ni-logos._tcp       local
+   eth0 IPv4 AKSHAY-PC Web-based Configuration             Web Site             local
+   eth0 IPv4 ORANGER_WANG                                  _nvstream._tcp       local
+   eth0 IPv4 NERECCO                                       _nvstream._tcp       local
+   eth0 IPv4 Will-Q                                        _mwg-cc._tcp         local
+   eth0 IPv4 ONIONS                                        _nvstream._tcp       local
+   eth0 IPv4 Kaylee___s Library                            iTunes Audio Access  local
+   eth0 IPv4 Kaylee___s Library                            Apple Home Sharing   local
+   eth0 IPv4 Anthony-PC                                    _ni-logos._tcp       local
+   eth0 IPv4 Shikhil___s MacBook Pro                       _HippoRemote._tcp    local
+   eth0 IPv4 Shikhil___s MacBook Pro                       _atc._tcp            local
+   eth0 IPv4 A72862C8BB5DD3E5                              iPod Touch Music Library local
+   eth0 IPv4 Shikhil Kharotia___s Library                  Apple Home Sharing   local
+   eth0 IPv6 Shikhil___s MacBook Pro                       _HippoRemote._tcp    local
+   eth0 IPv6 Shikhil___s MacBook Pro                       _atc._tcp            local
+   eth0 IPv6 A72862C8BB5DD3E5                              iPod Touch Music Library local
+   eth0 IPv6 Shikhil Kharotia___s Library                  Apple Home Sharing   local
+   eth0 IPv4 SLYSCAR                                       _nvstream._tcp       local
+   eth0 IPv4 aries                                         Remote Disk Management local
+   eth0 IPv4 MANOJKUMAR                                    _nvstream._tcp       local
+   eth0 IPv6 40716                                         _keepalive._dns-sd._udp local
+   eth0 IPv4 40716                                         _keepalive._dns-sd._udp local
+   eth0 IPv6 c8:e0:eb:a8:87:e9@fe80::cae0:ebff:fea8:87e9   _apple-mobdev2._tcp  local
+   eth0 IPv4 c8:e0:eb:a8:87:e9@fe80::cae0:ebff:fea8:87e9   _apple-mobdev2._tcp  local
+   eth0 IPv4 6010                                          _keepalive._dns-sd._udp local
+   eth0 IPv6 6010                                          _keepalive._dns-sd._udp local
+   eth0 IPv6 66069                                         _keepalive._dns-sd._udp local
+   eth0 IPv4 66069                                         _keepalive._dns-sd._udp local
+   eth0 IPv4 HT-PC                                         _nvstream._tcp       local
+   eth0 IPv4 SUKHI                                         _nvstream._tcp       local
+   eth0 IPv4 MARK-PC                                       _nvstream._tcp       local
+   eth0 IPv4 BHARATH                                       _nvstream._tcp       local
+   eth0 IPv4 347D7320BE3736A07BF1EE55BD88D6                _tunnel._tcp         local
+   eth0 IPv4 Friendly_32E4A1934898A800_71784E99A98C4529    _bp2p._tcp           local
+   eth0 IPv4 Invoke_466C40F1D0B4F942_1D69608D5BD7717C      _bp2p._tcp           local
+   eth0 IPv4 webdav_5CA4CBABAD3A0BBF_F7A63C7813000000      _bp2p._tcp           local
^CGot SIGINT, quitting.
mustafa@mustafa-ThinkPad:~$





---

### Post by papibe on 2014-11-09
Thanks.

I see that using ethernet not only discover the pi (mkhanpi), but several other machines over the building.

I believe could be a setting/filtering  on the wireless AP.

Could you run this also?
```
mtr -nrc 2 <pi_ip>
```
replacing <pi_ip> with the actual pi's IP.

Regards.

---

### Post by Mustafa_Khan on 2014-11-09
Here's the output for wifi:
> mustafa@mustafa-ThinkPad:~$ mtr -nrc 2 141.x.x.x
Start: Sun Nov  9 19:11:12 2014
HOST: mustafa-ThinkPad            Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 141.x.x.x            0.0%     2    6.5   5.9   5.2   6.5   0.0




---

### Post by papibe on 2014-11-09
Thanks. They have a direct connection.

This is what I think right now:

If you have a firewall on the laptop, you have to open the port 5353 both over eth0 and wlan0.

Make sure that your AP supports (and it's enabled) 'Multicast streams'. You may have to go the the manufacture's support forums or other specialized forums for the answer.

If you share your AP brand and model, they may be other users that could help you to find the setting, or comment  on its multicast capabilities.

Regards.

---

### Post by Mustafa_Khan on 2015-01-16
I don't know what changed but I've simply kept my pi and ubuntu updated and now I can connect via both interfaces.

---

