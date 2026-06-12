---
title: "Realtek RTL8723BE Poor Signal Strength on Ubuntu 17.04 &amp; HP Laptop"
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by awbaader on 2017-07-27
Hi there, I've been trying to get my wireless card working properly for a while now. The best I have managed is to get it to work within about 3 feet of the router. 
I ran the wifi analysis script and the results are in the [pastebin here]("http://paste.ubuntu.com/25183428/").
It is, as I'm sure you understand, incredibly frustrating to have to use Windows when I'm anywhere but my kitchen table. Hahahaha.

Any help is gratefully received.

Andy

---

### Post by johndough2 on 2017-07-27
Hi

The results say that you have a working WiFi.

Is the Windows WiFi connecting to the same ESSID:"WLAN-F55428" ?

There are a few things that intrigue me, one is the nameserver you are using.
Mine is something like - Server:  cache1.service.ubunt2.net  Address:  1.8.8.1
Yours is nameserver 127.0.0.53

I would like to compare your Windows values with your Ubuntu values.

C:\>> nslookup /ns

C:\>>ipconfig -all

Then perhaps we can resolve your issues.   The script shows a strong signal so your remark about short range means something like channel 1 is overpopulated.

Please post windows details, then we will try and help.

---

### Post by awbaader on 2017-07-27
Hi John, I was sat right next to the router when I ran the script. Perhaps that has something to do with it?
How would I get the Windows details?
Edit: Doh, just spotted the commands. Will give that a try now.

---

### Post by awbaader on 2017-07-27
This is the output from the commands in Windows.

Microsoft Windows [Version 10.0.10586]
(c) 2015 Microsoft Corporation. All rights reserved.


C:\Users\Andy>nslookup /ns
DNS request timed out.
    timeout was 2 seconds.
^C
C:\Users\Andy>
C:\Users\Andy>ipconfig -all


Windows IP Configuration


   Host Name . . . . . . . . . . . . : LAPTOP-V2LQES7Q
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Speedport_W_723V_1_43_000


Ethernet adapter Ethernet 2:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe FE Family Controller #2
   Physical Address. . . . . . . . . : 98-E7-F4-83-F4-24
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Wireless LAN adapter Local Area Connection* 3:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter
   Physical Address. . . . . . . . . : CE-B0-DA-66-C6-5B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Wireless LAN adapter WiFi:


   Connection-specific DNS Suffix  . : Speedport_W_723V_1_43_000
   Description . . . . . . . . . . . : Realtek RTL8723BE 802.11 bgn Wi-Fi Adapter
   Physical Address. . . . . . . . . : CC-B0-DA-66-C6-5B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2003:ca:7bde:ce01:319e:9cee:f277:8b2f(Preferred)
   Temporary IPv6 Address. . . . . . : 2003:ca:7bde:ce01:c4b8:dd2e:4fe7:a46c(Preferred)
   Link-local IPv6 Address . . . . . : fe80::319e:9cee:f277:8b2f%9(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.103(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 27 July 2017 13:30:19
   Lease Expires . . . . . . . . . . : 27 July 2017 19:30:19
   Default Gateway . . . . . . . . . : fe80::1%9
                                       192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 130855130
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-21-06-89-91-98-E7-F4-83-F4-24
   DNS Servers . . . . . . . . . . . : fe80::1%9
                                       192.168.2.1
   NetBIOS over Tcpip. . . . . . . . : Enabled


Ethernet adapter Bluetooth Network Connection:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : CC-B0-DA-66-C6-5C
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.Speedport_W_723V_1_43_000:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : Speedport_W_723V_1_43_000
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Local Area Connection* 5:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Teredo Tunneling Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:78cf:41a:2955:a869:9de0(Preferred)
   Link-local IPv6 Address . . . . . : fe80::41a:2955:a869:9de0%7(Preferred)
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 117440512
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-21-06-89-91-98-E7-F4-83-F4-24
   NetBIOS over Tcpip. . . . . . . . : Disabled


C:\Users\Andy>

---

### Post by awbaader on 2017-07-27
And now it seems to working elsewhere in the house...
I just give up. I don't have a clue why it would be working now but I ran the script again and pasted the results [here]("http://paste.ubuntu.com/25183841/"),

---

### Post by johndough2 on 2017-07-27
Hi

Well can we try and balance out some pro's and cons?

You Windows should not really time out, I suggest you fix a few things.

Make your IP fixed, and your DNS servers.  Then do the same in Ubuntu.

I note that  SONIC95 is a stronger signal than WLAN-F55428 and could it be swamping your signal?

Move channel on your router to a quieter one. Earlier versions of inSSIDer were free and showed signal strength etc, and perhaps LinSSID for Ubuntu.  If you can get one running it shows a colour chart for WiFI and you can see the strength and spread of signals.  Obviously routers can be turned off and come alive later and cause problems, but you can see all of it in live time.

if I think of anything else relevant I will post again.

Sorry it's bugging me, so read this

[http://   www    dot    tomshardware](http://   www    dot    tomshardware)  dot  co dot  uk/faq/id-1890089/find-fastest-dns-server-configure-windows.html

---

### Post by johndough2 on 2017-07-27
Now

I ran namebench.exe and got (takes 20 - 30 minutes)

Recommended configuration    (fastest + nearest)
Primary Server:-     194.168.4.100      --   	SYS-194.168.4.100
Secondary Server:- 198.153.192.1      --  	Norton DNS US
Tertiary Server:-     198.153.194.1      --     	Norton DNS-2 US

My second best is in the US of A, but it is nice to see the UK coming first.

The whole point of this is that it does not seem to be a problem intrinsic to Ubuntu, but network configs.  
So get Windows right and then transfer those settings to Ubuntu.

So please indicate what path you would like to follow and I will try and guide you.

---

### Post by chili555 on 2017-07-27
I see two things that you might tweak to try to help connectivity:> Channel occupancy:

      [COLOR="#FF0000"]12   APs on   Frequency:2.412 GHz (Channel 1)[/COLOR]
      1   APs on   Frequency:2.432 GHz (Channel 5)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)And your access point is on:> Cell 01 - Address: <MAC 'WLAN-F55428' [AC1]>
                    Channel:1
                    [COLOR="#FF0000"]Frequency:2.412 GHz (Channel 1)[/COLOR]
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"WLAN-F55428"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a43aaa84
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKSo you are trying to connect in the most congested, noisiest channel possible! Do you have the option to switch to channel 13?

Next, we see: > Region: Europe/Berlin (based on set time zone)

global
country 00: DFS-UNSETPlease set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

I think you have already done most of what needs to be done here:> [/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=1

---

