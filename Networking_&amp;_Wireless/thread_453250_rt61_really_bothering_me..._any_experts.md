---
title: "rt61 really bothering me... any experts?"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by jbullfrog on 2007-05-24
check out my last post please

---

### Post by MeeMaw on 2007-05-24
Sorry, I can't go live as I'm at work, but I can sneak in a couple of posts.... (and I'm not an expert, but I do have the rt61 chipset)
Do  
sudo gedit /etc/network/interfaces

(gedit is a text editor and /etc/network/interfaces is a configuration file, but I'm sure you knew that.)

If there are lines for ra0 (one saying "iface ra0 inet dhcp" or something like that)
You can add your encryption information to it with 

wireless-essid <your ESSID here>
wireless-key <your encryption key here>

save and close the file and go back to the terminal and do a 
sudo /etc/init.d/networking restart

See if you can connect.... and let us know how you did.

---

### Post by dfreer on 2007-05-24
It looks like your wireless card is working fine, you just need to connect to the network.
rather than editing your /etc/network/interfaces file (which is fine, but you'll need to edit it every time you want to change wireless networks, also, this breaks network-manager in feisty), you could do this:
```
sudo iwconfig eth1 essid "*your_wireless_AP_essid_here"* key *your_key_here*
sudo dhclient eth1
```

also, did you try Network Manager? did that work at all?

---

### Post by jbullfrog on 2007-05-24
[B]MeeMaw..I did the command

sudo gedit /etc/network/interfaces

and did not see any lines reading "lines for ra0"

dfreer, I tried 

sudo iwconfig eth1 essid "your_wireless_AP_essid_here" key your_key_here
sudo dhclient eth1

and got an Error!  I replaced eth1 with ra1 because I saw I had no eth1 device, but had a ra1 device.  This did not help however...

I have new problems...My ra0 disappeared![/B]

jeremiah@jeremiah-desktop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra1       Scan completed :
          Cell 01 - Address: 00:15:E9:19:FF:78
                    ESSID:"wangt"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm

jeremiah@jeremiah-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"wangt"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=68/100  Signal level:-69 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jeremiah@jeremiah-desktop:~$ sudo iwconfig ra1
ra1       RT61 Wireless  ESSID:"wangt"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=68/100  Signal level:-69 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jeremiah@jeremiah-desktop:~$ sudo ifconfig ra1
ra1       Link encap:Ethernet  HWaddr 00:1A:4D:20:B8:8D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:739452 (722.1 KiB)  TX bytes:4750 (4.6 KiB)
          Interrupt:21 

jeremiah@jeremiah-desktop:~$

---

### Post by dfreer on 2007-05-24
whoops I accidently put eth1 instead of ra0, wasn't thinking.
please don't delete your old post though, it confuses anyone new to the thread.

can you disable the security on your router, at least to troubleshoot your wireless problem? it seems like you are connected to the ESSID "wangt" but there is an encryption key enabled. Disable that and then run that:
```
sudo iwconfig ra1 essid "wangt"
sudo dhclient ra1
```

---

### Post by jbullfrog on 2007-05-24
how do I disable security on my router?

---

### Post by dfreer on 2007-05-25
what is the manufacture/model # of your router?

---

### Post by ruy_lopez on 2007-05-25
Try pointing your browser at 192.168.1.1 (using the ethernet ports, if you have to). And if that gives you the config pages, look for wireless security.

---

### Post by Barrakketh on 2007-05-25
I find that the drivers that Feisty ships with are terrible with the RT61 chipset.  I use the drivers that Ralink provides, though the version on their site [needs a modification](http://ubuntuforums.org/showpost.php?p=2537058&postcount=8) to work under Feisty.

It works perfectly fine with WPA, but I use the configuration file that is provided (and should be copied to the /etc/Wireless/RT61STA directory along with the firmware).  You could also use iwpriv commands in /etc/network/interfaces, but I don't.

---

### Post by dfreer on 2007-05-25
> **jbullfrog said:**
> how do I disable security on my router?

If you don't know how to disable the encryption, then how did you enable it? did someone else set up your router? is it even *your* router?

Also, in order to navigate to 192.168.1.1 you will need to plug your laptop into the router using an ethernet cable, you can't do it wirelessly (yet). most routers use the 192.168.1.1, although some use 192.168.2.1 and 192.168.0.1 as defaults.

---

