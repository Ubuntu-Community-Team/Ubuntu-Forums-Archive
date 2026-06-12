---
title: "[SOLVED] Wireless Issue, Need Help :) (D-Link)"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Kiefer Rodriguez on 2008-02-01
Hey guys,
Im going to be honest here, when it comes to linux, im a complete noob.
I only switched to Linux yesterday (From WinXP), and Im still learning my way around - So go easy on me :)

Im having issues with my wireless internet connection. My specs are as follows:

OS: Kubuntu 7.10 (Gutsy)
PC Model: Acer Travelmate 520
Processor: Pent 800Mhz (Dont laugh, Hehe)
Wireless Adapter: D-Link DWL-G122 Rev.C ('lsusb' ID = 07d1:3c03)
Wireless Network: Motorola Router (Not sure of model info) with no protection (WEP etc) 

Today, when I decided to try my luck connecting to the net, I plugged in my wireless USB adapter and the 'Link' light on it lit up and stayed solid, meaning it has connected sucessfully to the PC. Then I open KNetworkManager and right-click the icon in the system-tray (Is that a Windows term? hehe sorry) and it shows all the available wireless networks, so from that i assume that my adapter is working correctly, as i wouldnt be able to view the available networks without an adapter to scan for them (duh! lol). Then I click on my wireless network name to connect, and it says:

Activating Wireless Network Connection
Motorola (wlan0)
|---------0-100%----------| (Thats my attempt at a progress bar, lol)

Once the progress bar fills upto 100% I managed to connect. I opened Konqueror and searched some random string of letters in Google, and it loaded, I clicked a random link and it didnt load, the connection had stopped working, I tried to repeat the process to no avail, the progress bar reaches around 20% (though sometimes as high as 75%) and says "Could not connect to Motorola" So I know my adapter is working - Its just establishing a connection, Any suggestions?

Heres some things I did in Konsole that might help (These were copied when the connection isnt working):

--

kiefer@Kubuntu:~$ lsusb
Bus 001 Device 005: ID 07d1:3c03 D-Link System
Bus 001 Device 001: ID 0000:0000

--

kiefer@Kubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--

kiefer@Kubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1B:11:15:AD:EC
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

--


Any Help or suggestions would be greatly appreciated, If I have left anything out, dont hesitate to ask :) 
Thanks,

Kiefer Rodriguez :D

---

### Post by Kiefer Rodriguez on 2008-02-01
Anyone? Im kinda at my witts end here :(

---

### Post by rustybronco on 2008-02-01
Wireless Adapter: D-Link DWL-G122 Rev.C ('lsusb' ID = 07d1:3c03)
rt73 chipset...

[http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)

---

### Post by Kiefer Rodriguez on 2008-02-02
Thanks for the link, The guide worked a charm.
I'm writing this from my brand spanking new Kubunutu 7.10 Konqueror browser :D
Thanks again,

Kiefer.

---

