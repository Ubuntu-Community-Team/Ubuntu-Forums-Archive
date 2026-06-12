---
title: "interpeting wireless information"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by audit on 2009-07-02
could someone explain to me how to interpret this information:

I entered this command "iwconfig" and received this information.

wlan1     IEEE 802.11bg  ESSID:"ScottYoder"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:8D:89:74   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-53 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I most interested in finding out if this tells me how fast I am sending information.

Thanks in advance.

forgive smiley faces I have no idea how to get rid of them

---

### Post by PatrickVogeli on 2009-07-02
From your output:

Bit Rate=1 Mb/s

That's the speed you're communicating with your wireless router. If you have a line which can do faster than 1 Mbps, you should look into that.

Could you post the outputs of:

dmesg, lsusb and lspci?

(better attach the result in a text file)

---

### Post by audit on 2009-07-02
How do I attach a text file to a thread?

---

