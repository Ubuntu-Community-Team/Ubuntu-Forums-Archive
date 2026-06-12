---
title: "&quot;Connected&quot; to WiFi, but cannot access anything"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by anastos2 on 2017-07-19
I recently booted up an old PC and got Windows 10 running on it. I then installed Ubuntu Desktop 16.04.2 on another partition on the same machine. I am able to access the internet on the Windows partition completely, but on Ubuntu I am only able to access it through a wired ethernet connection.

When I connect to my network via WiFi on Ubuntu, Network Settings says I am connected, but I am not able to access anything on the internet (Firefox says "Server not found", "ping google.com" returns nothing, etc.). I am not even able to access other computers on the same network (e.g. "ping 10.0.0.14" returns nothing).

I ran [this script]("https://github.com/UbuntuForums/wireless-info") to help diagnose the problem, and [here]("https://pastebin.com/xesFzikv") is the output.

Any ideas what the problem might be, and how to fix it? Thanks in advance.

---

### Post by chili555 on 2017-07-19
Please see:> Cell 01 - Address: <MAC 'HOME-0692' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"HOME-0692"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048925c49d2
                    Extra: Last beacon: 152ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot and show us:```
ping -c3 10.0.0.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by anastos2 on 2017-07-19
Ok. I changed the Security Mode on my gateway from "WPAWPA2-PSK (TKIP/AES)" to "WPA2-PSK (AES)". I then wrote to /etc/default/crda with `REGDOMAIN=US`. I then rebooted. Here is the output you wanted (they all failed):

[FONT=courier new]$ **ping -c3 10.0.0.1**
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2028ms

[/FONT][FONT=courier new]$ **ping -c3 8.8.8.8**[/FONT]
[FONT=courier new]PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.[/FONT]

[FONT=courier new]--- 8.8.8.8 ping statistics ---[/FONT]
[FONT=courier new]3 packets transmitted, 0 received, 100% packet loss, time 2032ms

$ **ping -c3 www.ubuntu.com**
ping: unknown host www.ubuntu.com
[/FONT]

---

### Post by chili555 on 2017-07-19
Krazy with a capital K!!!

Please get a connection with the ethernet and show us:```
ifconfig -a
route -n
```

---

### Post by anastos2 on 2017-07-19
(EDIT: accidentally did `ifconfig`, not `ifconfig -a`)

Ok, here it is:
```

**$ ifconfig -a**
enp4s0    Link encap:Ethernet  HWaddr f0:4d:a2:53:28:26  
          inet addr:10.0.0.19  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:742:8180:59d0:78ba:8a17:5174:9edb/64 Scope:Global
          inet6 addr: 2601:742:8180:59d0:4a9c:d6c5:814e:3b2b/64 Scope:Global
          inet6 addr: fe80::928d:2dd8:8795:47f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:595 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:443544 (443.5 KB)  TX bytes:71421 (71.4 KB)


enx64d4da01a4f1 Link encap:Ethernet  HWaddr 64:d4:da:01:a4:f1  
          NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:84947 (84.9 KB)  TX bytes:84947 (84.9 KB)


wlp3s0    Link encap:Ethernet  HWaddr 00:23:15:1f:cc:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:215599 (215.5 KB)  TX bytes:262965 (262.9 KB)


**$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 enp4s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp4s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0

```

---

### Post by chili555 on 2017-07-19
Except for the fact that both ethernet and wireless are connected at the same time, everything looks fine. I assume that you can ping now:```
ping -c3 www.ubuntu.com
```If you reboot with the ethernet detached, is there any improvement?```
ping -c3 10.0.0.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by anastos2 on 2017-07-19
Nope, no difference. :(

---

### Post by chili555 on 2017-07-20
Time to delve into the warp core. Please run and post:```
dmesg | grep -i -E 'iwl|wlp|dns'
```If the result is more than ten or so lines, paste the result here and give us the link:  [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by johndough2 on 2017-07-20
Hi

You typed US chili555 typed IS, it might matter.


REGDOMAIN=IS

I then wrote to /etc/default/crda with `REGDOMAIN=US`.

---

### Post by anastos2 on 2017-07-20
Ok, [here]("http://paste.ubuntu.com/25134124/") is the output of `dmesg | grep -i -E 'iwl|wlp|dns'`

---

### Post by chili555 on 2017-07-20
> **johndough2 said:**
> Hi

You typed US chili555 typed IS, it might matter.


REGDOMAIN=IS

I then wrote to /etc/default/crda with `REGDOMAIN=US`.Indeed. I said also, "Of course, substitute your country code if not Iceland." If you and anastos2 are not in Iceland, then use the code you found in the link I provided. 

My apologies if that wasn't clear.

---

### Post by anastos2 on 2017-07-20
UPDATE: Just tested, and WiFi works completely when I connect it to a different network (iPhone hotspot). So the problem is specific in some way to my home network.

---

### Post by chili555 on 2017-07-20
Will you please try changing the DNS nameservers in Network Manager like this? [http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png](http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png)

Reboot.

---

### Post by anastos2 on 2017-07-20
No effect. I can't even reach anything by IP address, so I doubt it has to do with DNS.

---

### Post by johndough2 on 2017-07-21
Hi 

Despite my earlier stupid remark on the country code, I have looked again and think it is routing problem.

The WiFi connects and works.  It has Comcast for DNS, what it does not seem to have is a proper routing table.

So I would check /change my Network Manager and perhaps use WICD and go thru the IP settings again.

Set the IPv4 address, the **_SubNet Mask_** and the Default Gateway

10.0.0.18, 255.0.0.0, 10.0.0.1

---

### Post by anastos2 on 2017-07-21
Ok, I think I've done what you said to, but it is still not working. Can you let me know if this looks right? --

```

$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp3s0
10.0.0.0        0.0.0.0         255.0.0.0       U     600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0

```

[http://i.imgur.com/3X5FKW9.png](http://i.imgur.com/3X5FKW9.png)

---

### Post by Hadaka on 2017-07-21
Hi, the subnetmask should read 255.255.255.0
Try that in the IPv4 settings please.
thanks.
   [ATTACH=CONFIG]276080[/ATTACH]wlan0     Link encap:Ethernet  HWaddr ***************
          inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0  **[COLOR=#ff0000]<-[/COLOR]**
          inet6 addr: X:X:X:X:X:X:X:X:X/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:467129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:220872888 (220.8 MB)  TX bytes:40197904 (40.1 MB)

---

### Post by johndough2 on 2017-07-22
Hi

I cannot see anything wrong, you could de-select the MANUAL and choose an automatic option.

Mystified.

Looking at my WiFi I have less set than you.

SSID:  myispathome
Mode: Client
Device:  00xx00ccABBA
MTU: automatic

Security: WPA & WPA2
PROXY: NONE

IPv4 - method  - Automatic DHCP

---

### Post by Hadaka on 2017-07-22
> **johndough2 said:**
> Hi

I cannot see anything wrong, you could de-select the MANUAL and choose an automatic option.

Mystified.

Under "Netmask"..you have "8"
"Subnet" ..you have 255.0.0.0

Both should read...255.255.255.0

Where you currently have the  "8" just change that to 255.255.255.0
Thanks

---

### Post by johndough2 on 2017-07-22
Hi

Further trawling, and I hope I don't say something already said, like my faux pas with the country code.

169.254.0.0 is when there is a server fault apparently.  It appears in your routing table.  I found this at...
   serverfault    dot  com       /questions/132657/where-does-the-route-to-169-254-0-0-comes-from

and I will paste in relevant bits.

Symptom:-      Every time the system boots, the zeroconf route (169.254.0.0) is enabled. You manually disable it by turning off the firewall and remove the route with 169.254.0.0 / 255.255.0.0 using the route command.

    Example output of the route with the zeroconf route enables would like similar to the following:

# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.15.50.0      *               255.255.252.0   U     0      0        0 eth0
169.254.0.0     *               255.255.0.0     U     0      0        0 eth0

Solution:-  To disable the zeroconf route during system boot, edit the /etc/sysconfig/network file and add the following NOZEROCONF value to the end of the file:

NETWORKING=YES
HOSTNAME=localhost.localdomain
NOZEROCONF=yes

The 169.254.0.0/16 network is used for Automatic Private IP Addressing, or APIPA. If a DHCP client attempts to get an address, but fails to find a DHCP server after the timeout and retries period it will randomly assume an address from this network. This allows communication with hosts that have failed to obtain a DHCP address.
##############################

[https://askubuntu.com/questions/660355/why-169-254-0-0-appears-by-default-in-the-routing-table](https://askubuntu.com/questions/660355/why-169-254-0-0-appears-by-default-in-the-routing-table)

and chilli555 is there to be credited with an explanation.

---

### Post by johndough2 on 2017-07-22
Hi 

The netmask is fine by me.

The private 10.0.0.0 net is capable of 256 * 256 * 256 addresses, which give about 16,777,216 addresses and is happy with a /8 suffix.

---

### Post by wildmanne39 on 2017-07-22
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them, also people access the forum via mobile devices as well and won't want to use up their bandwidth on huge images. Use the forum's attachment facility which is accessed by clicking on the paperclip icon above the text box. If you don't see the paperclip icon, click on Go Advanced below the text box.

---

