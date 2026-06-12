---
title: "How do I remove duplicate entries in the iwlist scan?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-01
Hi, Im having a problem with my network card randomly disconnecting -- sometimes every few hours, sometimes every few days.  I notice that after disconnecting I am unsuccessul in being able to reconnect, despite do a /etc/init.d/networking restart or /etc/init.d/dbus restart.  The only way to gain a connection back is to reboot.

System specs:
linksys wpc54gs card, ndiswrapper svn, bcmwl5.sys win xp driver, ubuntu feisty, broadcom 4306 rev 03 chipset

Here however is where I think the problem lies.  Under normal conditions where everything is working correctly the results of ***iwlist scan*** are the following:

> 
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:8E:94:E9
                    ESSID:"GoHilton.com"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=1000
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


However when I drop the connection and am unable to connect I get the following:
> Cell 01 - Address: 00:13:10:8E:94:E9
                    ESSID:"GoHilton.com"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=1000
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


          Cell 02 - Address: 00:00:00:00:00:00
                    ESSID:"GoHilton.com"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=1000
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


Basically my router is listed twice, the second time with no Address.  Is there someway to reconfiigure the scan to remove Cell 02, or is there some way within the /etc/network/interfaces file to force to associate to a specific address.

Here is what I have tried, and it hasn't worked:
auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146 192.168.1.1
**pre-up iwconfig wlan0 ap 00:13:10:8E:94:E9**
wpa-driver wext
wpa-ssid GoHilton.com
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk [I]KEY
[/I]

This behaivor will occur if I am using this setup with a static IP address, or using network manager to configure WPA for me with a dynamic address.

Hopefuly someone can provide some insight.  Im out of ideas.

---

### Post by noob12 on 2007-08-01
Weird.  

By any chance is your wireless interface in mode "Auto"?  Does explicitly setting the mode Managed on your interface help?  Just a hunch.

---

### Post by kevdog on 2007-08-01
How do I do that???

By adding
preup iwconfig wlan0 mode managed
to the interfaces file??

I am correct in try to connect to specific Access Point with MAC address by using this statement??:
pre-up iwconfig wlan0 ap 00:13:10:8E:94:E9

I cant find anything on the web or in the man files that addresses using these commands with the ndiswrapper driver in combination with wpasupplicant.  I suppose they would work, but have no verification.

---

### Post by noob12 on 2007-08-01
You might want to file a bug with the ndiswrapper folks.  

I was hoping you might workaround the issue by putting the driver into Managed mode.  According to  [_this doc_]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/") **iwconfig wlan0 mode Managed** is *supposed*  to work, but I do notice on mine that the mode stays "Auto" even if I do this.  I'm running driver version 1.37 of ndiswrapper though and the laptop I'm currently on is using net8185  ndis drivers; don't currently have a laptop that uses the bcmwl5  drivers handy.

---

### Post by kevdog on 2007-08-02
Never too bored, I think it has to be a driver issue.  I totally removed network-manager, and basically was connecting to the router using wpa supplicant and down,up,dhclient commands.  Later the connection was  dropped, I tried reconnecting but couldnt.  I noticed in the iwlist scan results that the router was again listed twice. 

I hate it when this does this, because basically I have to do the following 

#1 Reboot
#2 sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/dbus restart

Then use whatever method to re-connect

Maybe its a ndiswrapper issue or possibly the driver.  How would I find out??

For the record: 
I brought up the interface with
sudo iwconfig wlan0 mode Managed
It lists this mode under iwlist scan
Ill have to wait however and see if this corrects the problem.

---

### Post by kevdog on 2007-08-02
No duplicate error after 12 hours and counting with the 
iwconfig wlan0 mode Managed
statement.  Too early to call this a success yet!

---

