---
title: "Toshiba A210 Wireless (net8187b) no networks"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by damphoud on 2008-03-22
Hello, having a hard time with toshiba wireless ... I've installed ndiswrapper with out any problems/errors, drive net8187b, but i can't find any wireless networks. I have been able to find them, maybe once or twice, but even then, when I went to enter in my WEP passphrase, it wouldn't connect.

```

$ lspci
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

ndiswrapper -l
net8187b : driver installed
        device (0BDA:8197) present

```

thanks!

---

### Post by damphoud on 2008-03-22
I've tried the Fn+f8(wireless) to make sure it wasn't disabled. Also made sure the switch was turned on and there is no weird settings in the bios. stumped :(

---

