---
title: "Can't connect to the internet."
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Chukchi Husky on 2007-12-29
I recently installed Ubuntu on a seperate computer and got it working better then it was before.  I managed to get a Netgear WG111v2 to work and connect to a wireless network (the four bar signal image replaces the two monitor network image), but when I open up Firefox it can't access the internet.

I'm currently using a different computer to post this.

---

### Post by Edho on 2007-12-29
Right-click on the 4 bars icon.

Can you see 
Enable networking?
Enable wireless?

Can you enable them?

Can you see 
Connection information?

Left-click on that en you have to see a Ip...enso.

---

### Post by Chukchi Husky on 2007-12-29
Enable networking is ticked.
Enable wireless is ticked.
When I click connection information, it says IP is 0.0.0.0.

---

### Post by Edho on 2007-12-29
So, you don't have a usable IP number (=adress).
It's normal the browser don't work.

Is the error on he Router-side or the adaptor(pc) side?
Give more information.
Did you configured the router yourself?
How ?

Goto..Applications...Accesoirs...Terminal.

In terminal give the command :

sudo iwconfig



Post the output.

---

### Post by Chukchi Husky on 2007-12-29
The router is working.  The computer I'm using to post this is connected to it with a wire, and a Xbox 360 and Wii are connected wirelessly.

The router(Philips SNB5600) has a setup wizard and and copied the MAC address from this computer so it can connect to the internet.  I haven't configured any wireless security, but I given an SSID.

Here are the results I got from sudo iwconfig

lo            no wireless extensions
wlan0     IEEE 802.11g ESSID="Wolf"
              Mode: Managed Frequency: 2.472GHz Access Point: 00:1A:2A:92:A0:C8
              Bit Rate=54Mb/s Tx-Power=20dBm Sensitivity=0/3
              RTS thr:off Fragment thr:off
              Encryption key:off
              Power Management:off
              Link Quality:25/100 Signal level:-80 dBm Noise level:-96 dBm
              Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
              Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by Edho on 2007-12-29
Looks good, compared with mine.

Except for the signal=strenght.
25/100 is low ?  i don't have exper ...mine is 98%

Code:
lspci
Code:
iwlist scanning
Code:
iwconfig
Code:
ifconfig
Code:
cat /etc/network/interfaces

---

### Post by Chukchi Husky on 2007-12-29
iwlist scanning
lo interface doesn't support scanning
wlan0 Scan completed
Cell 01 0 Address 00:1A:2A:92:A0:C8
ESSID: "Wolf"
Protocol: IEEE 802.11g
Mode: Managed
Frequency: 2.472 GHz (Channel 13)
Quality 39/100 Signal level: -71 dBm Noise level: -96 dBm
Encryption key: off
Bitrates: 1Mb/s, 2Mb/s, 5.5Mb/s, 11Mb/s, 8Mb/s, 12Mb/s, 24Mb/s, 36Mb/s, 9Mb/s, 12Mb/s, 48Mb/s, 54Mb/s
Extra:  bcn int=100
Extra: atim=0

ifconfig
Link encap: Local Loopback
inet add: 127.0.0.1 Mask 255.0.0.0
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
Rc packets: 128 errors: 0 dropped: 0 overruns: 0 frame: 0
Tx packets: 128 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 Txquelelen: 0
RX bytes: 9984 (9.7 KB) TX bytes: 9984 (9.7KB)

cat /etc/network/interface
auto lo
iface lo inst loopback

---

### Post by Edho on 2007-12-29
In menu...

System...Administration...Netwrk.

Can you see 
- Wireless
- Wired

In Tab DNS you have to see the ServerDNS.
Mine is 192.168.1.1 (from my Netgear-router)

Select the wireless...hit "properties"

Can you enable "Roaming mode".?

---

### Post by Chukchi Husky on 2007-12-29
I can see wireless and modem connection.  Roaming mode is enabled.  DNS is blank.

---

### Post by Chukchi Husky on 2008-01-02
Isn't there anything else I can try to make it work?

---

