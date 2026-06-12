---
title: "WMP54Gv4 and WPA"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by jdmpike on 2007-04-09
I have followed so many different threads trying to get this to work, I don't know what to do now. So, I decided to create my own because I am sure there is someone smarter/more dedicated/more lucky than me out there.

**Problem: Setup a wireless connection from my bedroom PC to wireless router in living room using WPA2 (AES+TKIP).**

My steps thus far:

1) Does the system recognize the card?

```

lspci
01:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 22
        Memory at fc9fc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

```

2) Is the card listed as a wireless interface?

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"JDM"
          Mode:Managed  Frequency=2.437 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm  
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-198 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

```

3) Can it see the AP I want to connect to?

```

iwlist ra0 scan
          Cell 04 - Address: 00:18:39:EC:FC:94
                    Mode:Managed
                    ESSID:"JDM"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-66 dBm  Noise level:-199 dBm


```

Up to this point, I feel like Ubuntu is doing it's part, now it should just be up to me to get the card talking to my AP correctly... so I followed this [thread]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-6acc96b6588b47952c4fba9f4a3f49e2339c493b").

4) Did you set up your /etc/network/interfaces correctly? (Not so sure about this)

```

cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto ra0
iface ra0 inet static
address 192.168.1.101
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
pre-up iwconfig ra0 essid "JDM"
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=6
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="MY_KEY_FROM_WPA_PASSPHRASE"
pre-up iwpriv ra0 set TxRate=0
pre-up ifconfig ra0 up

```

5) Restart the network

```

sudo /etc/init.d/networking restart

```

Didn't work... Boot the machine... Still nothing...

Can anyone help me figure out what I am doing wrong?

It will be a very good day when this starts working!

Thanks for the help,

jdmpike

---

### Post by 68hc11 on 2007-04-09
[http://ubuntuforums.org/showthread.php?p=2423423#post2423423](http://ubuntuforums.org/showthread.php?p=2423423#post2423423)

I haven't run WAP yet but can you run the network open first?

---

### Post by jdmpike on 2007-04-10
I haven't tried to get it to work without encryption, but that isn't what I want to do.

Can anyone help me resolve this issue? Anyone with a working WMP54G that uses RT2500 drivers, can you post your /etc/network/interfaces file so I can see how you set it up?

Thanks,

jdmpike

---

### Post by bionnaki on 2007-04-11
see my signature.

---

### Post by TRinQtown on 2007-04-11
Thank you - I recently installed Ubuntu on a 1 GHz Pentium III - 512 MB Gateway. Windows ME had crashed beyond all hope so I decided to give EE and (shortly thereafter) FF a try. Everything is working except for the WPA thing. I currently have this computer connected to the router through ethernet, but it has the above wireless card installed and I eventually want to use it again.

---

### Post by jdmpike on 2007-04-17
The hardware is recognized, the driver is working, it associates with no encryption...

I still can't seem to get this working with WPA... when will wlassistant just be able to handle WPA or least provide some detail about why it isn't working? I have no idea which log files, etc, I should look at as to why it will not work with WPA enabled...

I am teh frustrated...

---

### Post by jdmpike on 2007-04-17
... and about wlassistant - I just checked, and it looks like 0.5.7 supports WPA/WPA2 - woot!

I hope this makes it into the feisty repos on Thursday!

---

### Post by smo0th on 2007-04-18
Also check you don't have duplicate DNS, this is how it worked for me:

[http://ubuntuforums.org/showthread.php?p=2472174#post2472174](http://ubuntuforums.org/showthread.php?p=2472174#post2472174)

\\:D/

---

### Post by winter7 on 2007-04-18
Hmm... not sure if this helps as I don't really know what I'm doing, but I recall reading somwhere that you don't use quotes if the passkey was generated from wpa_passphrase. I think you use the quotes when it's just your passkey.

HTH

---

### Post by wieman01 on 2007-04-20
Does the Ralink driver support "AES"? I am not entirely sure here. Give "TKIP" a go instead. Might be the solution.

---

