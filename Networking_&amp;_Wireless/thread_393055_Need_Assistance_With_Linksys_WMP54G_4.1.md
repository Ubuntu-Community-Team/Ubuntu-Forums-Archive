---
title: "Need Assistance With Linksys WMP54G 4.1"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by JengaBlocks on 2007-03-25
Need step by step instructions on how to install a Linksys WMP54G 4.1 wireless card

I bought this card yesterday on recommendation that this was to run "out of the box" as stated in the notes - far from it. Here's what I've done so far:

1) Synaptic Package Manager to obtain the current ndiswrapper
2) Copied the 4.1 driver set off the Linksys CD
3) NDisWrapper -i Rt61.INF

NDisWrapper -l
  rt61 driver installed, hardware present

/etc/network/interfaces
  auto lo
  iface lo inet loopback
  auto wlan0
  iface wlan0 inet static
  wireless-essid MyCompany
  wireless-key blahblah
  address 192.168.0.4
  netmask 255.255.255.0
  gateway 192.168.0.1

iwconfig
  wlan0  IEEE 8.2.11g       ESSID: MyCompany
            Mode: Managed   Frequency: 2.412Ghz   Access Point: Not Associated
            RTS thr off         Fragment thr=2346 B
            Encryption key: off

ifconfig
  wlan0   Link encap: Ethernet  HWaddr 00:18F8:2D:DB:66
           inet addr: 192.168.0.4  Mask: 255.255.255.0
           inet6 addr: fe88::218::f88f::fe2d::db66/64 Scope:Link
          UP RUNNING MULTICAST MTU:1500 Metric:1
          Rx Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 366 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 0
          RX bytes: 0 (0.0.b) TX bytes: 18576 (18.1KiB)

Pinging to 192.168.0.1 (my router)
    PING 192.168.0.1 56(84) bytes of data
    PING icmp seq=1 Desitination Host Unreachable

Ping yahoo.com just sits there doing nothing and returns unknown host yahoo.com
Can't google.com through Firefox either

Pretty much hosed

---

### Post by chili555 on 2007-03-25
Here is a little problem; from interfaces:```
wireless-key blahblah
```and this from iwconfig:```
Encryption key: off
```Evidently iwconfig is not aware you have or want a key. Please do:```
sudo iwconfig wlan0 key on
sudo iwconfig wlan0
```and see if the key shows up, like this:```
wlan0     IEEE 802.11g  ESSID:"myrouter1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:62:8D:F7   
          Bit Rate=48 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:096C-XXXX-XXXX-XXXX-XXXX-4E4A-FE
```Some names have been changed here.

Is your key a 10- or 26-character hex key or some other thing that is tricky to impossible to get working?

---

### Post by JengaBlocks on 2007-03-25
after doing:

iwconfig wlan0 key on
iwconfig wlan0

the encryption key is still off and there is no key sequence like you've shown in your example

the wep key is a 10 character HEX code

it doesn't appear that the wireless-essid and wireless-key parameters in /etc/network/interfaces is being picked up either
That info came from the System | Administration | Networking of which I entered upon installation and didn't work

---

### Post by chili555 on 2007-03-25
May we see /etc/network/interfaces? Perhaps we can fine-tune it. Please obscure half of your WEP key.

---

### Post by JengaBlocks on 2007-03-25
/etc/network/interfaces

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-essid ESSIDHERE
wireless-key xxxxxxxxxx  (no hashes, straight hex)
address 192.164.0.4
netmask 255.255.255.0
gateway 192.168.0.1

---

### Post by JengaBlocks on 2007-03-25
More info... the card is working because when I do:
  iwlist wlan0 scan

I see all the cells in my area including mine.

When I do a :
  iwconfig wlan0 mode Managed

I get an error:
  SET failed on device wlan0 : Device or resource busy

I then tried to do a iwconfig wlan0 key restricted XXXXXXXXXX
  but after I did this, a iwconfig returned no change to the encryption key (its still off)

---

### Post by chili555 on 2007-03-25
Is this a typo?```
address 192.164.0.4
``` Should't it be 192.16**8**.0.4?

You'll probably have to **sudo** iwconfig wlan0 mode Managed.

---

### Post by JengaBlocks on 2007-03-25
yes it was a typo (i.e. I had 192.168.0.4 listed correctly in the file)

I have "Allow local system administrator login" checked and am logged in as root. Does that get around using sudo? (newbie here). Regardless, I typed in sudo iwdong wlan0 mode Managed and still got back the "SET failed on device wlan0 ; Device or resource busy" error.

---

### Post by chili555 on 2007-03-25
It may be because it's already in Managed mode:```
iwconfig
wlan0 IEEE 8.2.11g ESSID: MyCompany
Mode: Managed Frequency: 2.412Ghz Access Point: Not Associated
RTS thr off Fragment thr=2346 B
Encryption key: off
```When you scan, please jot down the address of the access point you want to associate with:```
wlan0     Scan completed :
          Cell 01 - Address: **00:13:10:62:D8:G7**
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11g

```Then let's try:```
sudo iwconfig wlan0 ap 00:13:10:62:D8:G7
sudo iwconfig wlan0 key open
/sudo /etc/init.d/networking restart
```And let us know.

---

### Post by JengaBlocks on 2007-03-25
SIOCSIFFLAGS: Input/output error
Failed to bring up wlan0

---

### Post by chili555 on 2007-03-25
May we see the entirety of sudo iwconfig?

---

### Post by JengaBlocks on 2007-03-25
iwconfig

lo                       no wireless extensions.
eth0                   no wireless extensions.
wmaster0           IEEE 802.11g   Frequency 2.412Ghz
                        RTS thr:off       Fragment thr=2346 B

wlan0                IEE 802.11g     ESSID="ESSIDHERE"
                        Mode:Managed Frequence:2.412 Ghz Access Point: XX:XX:XX:XX:XX:XX
                       RTS thr: off       Fragment thr=2346 B
                       Encryption key: off
sit0                  no wireless extensions

Access point above had the same address as what was from the iwlist wlan0 scan

The encryption/WEP just doesn't work. Its not getting picked up.

---

