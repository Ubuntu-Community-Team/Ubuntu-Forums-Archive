---
title: "Can't connect WPA Networks?"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by alien21010 on 2008-03-14
Hello... I need some help pretty badly...

I just migrated my laptop from Win XP to Gutsy again (I seem to go back and forth for a number of reasons), and am unable to get my wifi to connect to secured networks... I can connect to any unsecured network, but I would really like to have my network secured when I connect to it.   

I have the AirForce 54g BCM4318 chipset.  I installed the drivers using ndiswrapper, and so far it seems to work, except for this.  I installed the same thing on Feisty Fawn and it worked just fine, but when I do a clean install for Gutsy, all hell breaks loose.  Does anyone know what's causing this?

---

### Post by ittiam on 2008-03-14
How are you trying to connect to the secure network? My suggestion would be to use wpa_supplicant/knetworkmanager. For me the nm-applet always gives problems trying to connect to a WPA network. 

And just to make sure you have the WPA installed and enabled (it is enabled by default in ubuntu), can you post the output of the following

```
sudo cat /proc/net/ndiswrapper/eth1/hw
```

---

### Post by alien21010 on 2008-03-14
That command produced the following output:

cat: /proc/net/ndiswrapper/eth1/hw: No such file or directory

I thought this might have something to do with my /etc/network/interfaces file, but I haven't been able to find anything about it on the forums.  

> 
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:16:36:F3:DA:B9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fef3:dab9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:698551 (682.1 KB)  TX bytes:157039 (153.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


> 
ghost@froobles:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


It seems as though there should be more interfaces there?  But when I add additional interfaces, then I can no longer even see that I have wireless working...

---

### Post by ittiam on 2008-03-14
From your ifconfig it is clear that you have obtained the ip address from the router. Just to make sure eth1 is your wireless interface right (and you have got ndiswrapper installed), because if not for that I am confused why you did not get the output for that. Did you use sudo preceding the command or were you already as a root user?

Yes there should be more interfaces in the /etc/network/interfaces file. Could you just see what happens when you do 
```
iwconfig
```

---

### Post by alien21010 on 2008-03-14
Sorry, eth1 is my wired interface.  I have it plugged in right now so that I can access the internet to provide you with this information.

>  iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"BeefyBurrito"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:48:E9:93   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by kevdog on 2008-03-14
You shouldn't have any problems with WPA on Gutsy with ndiswrapper/bcmwl5 driver combo.  The problem may lie with network manager (even though I know others including me have gotten it to work).  I would first make sure you have the wpasupplicant package installed:
sudo aptitude wpasupplicant

Try again with network manager.  If no luck we can manually troubleshoot trying to bring the network interface and wpa connection up manually using a command line method.  Possibly this would give some insight into what is not working?

Can you post the following just to give us some background:
lshw -C network
iwlist scan

---

### Post by ittiam on 2008-03-14
Yes I was about to get to the point that kevdog had mentioned. Please make sure wpa_supplicant is easy and kevdog himself has a good tutorial as how to set it up from the command line. Well as I have mentioned in quite a number of posts...knetworkmanager is always better, try using that!

---

### Post by alien21010 on 2008-03-14
>  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:16:36:f3:da:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: eth0
       version: 02
       serial: 00:17:c4:01:81:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,11/02/2005, 4.10.4 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


>  iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:18:39:48:E9:93
                    ESSID:"BeefyBurrito"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:14:A5:07:9F:CD
                    ESSID:"MentalOsmosis"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:09:5B:33:50:44
                    ESSID:"Wireless"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:13:46:F1:71:9C
                    ESSID:"JamieWireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=20
                    Extra:atim=0
          Cell 05 - Address: 00:18:F8:FD:A4:57
                    ESSID:"Chazz666"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0



Wpasupplicant is installed and working properly according to aptitude...

---

### Post by ittiam on 2008-03-14
Did you try installing knetworkmanager? Try connecting using that. It might work.

---

### Post by alien21010 on 2008-03-14
knetworkmanager can't see the wireless connection... It sees the wired connection just fine though...

Nevermind, it can see the connection, both wired and wireless, but it still won't connect to anything that is using any encryption...  Do you know how to force it to allow me to input a key?  I can't seem to get it to allow me to enter my wifi key...

---

### Post by ittiam on 2008-03-14
Dumb it may sound but have to ask, "You have the wireless enabled when you checked it out with knetworkmanager right?"

Also please do the following, after enabling wireless in your laptop.

```
modprobe -r ndiswrapper
modprobe ndiswrapper

```

Once done check knetworkmanager.

---

### Post by ittiam on 2008-03-14
ok saw your updated reply, now can you post

```
sudo cat /proc/net/ndiswrapper/eth0/hw
```

assuming eth0 is your wireless interface!

---

### Post by ittiam on 2008-03-14
Also wanted to ask one more thing,

what exactly happens when you click on your network from knetworkmanager? 

Doesn't it pop up a window asking you for the password for your connection?

---

### Post by ittiam on 2008-03-14
And one more thing, if you trying to having a wireless connection when you are having a wired connection to the same router, knetworkmanager will support only one active interface and it will prefer wired over wireless connection. hence disconnect your wired connection and then try the wireless connection with knetworkmanager.

---

### Post by alien21010 on 2008-03-14
> ghost@froobles:~$ sudo cat /proc/net/ndiswrapper/eth0/hw
[sudo] password for ghost:
status=ready
mac: 00:17:c4:01:81:c9
beacon_period=0 msec
atim_window=0 msec
frequency=2462000 kHZ
hop_pattern=0
hop_set=0
dwell_time=0 msec
tx_power=1496 mW
bit_rate=54000 kBps
rts_threshold=2347 bytes
frag_threshold=2346 bytes
power_mode=always_on
encryption_modes=WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


It doesnt prompt me to enter a password...  Which I find kind of odd.  It defaults to the unsecured networks in the area, which is not exactly comforting...

---

### Post by ittiam on 2008-03-14
Again just wanted to confirm, did you disable your wired connection before trying to connect to the wireless network? When you right click on knetworkmanager and select your network it defaults to some other network without prompting for a password?

---

### Post by kevdog on 2008-03-14
Which one of those wireless networks is yours curiously on the output of the iwlist scan statement?

---

### Post by alien21010 on 2008-03-14
Mine is BeefyBurrito.

---

### Post by kevdog on 2008-03-14
Cell 01 - Address: 00:18:39:48:E9:93
ESSID:"BeefyBurrito"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:78/100 Signal level:-46 dBm Noise level:-96 dBm
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0
IE: WPA Version 1
Group Cipher : WEP-40
Pairwise Ciphers (1) : WEP-40
Authentication Suites (1) : PSK

I never understood why the cipher was listed as WEP-40.  Can you just confirm the settings on your router for the group and pairwise cipher type.  Usually it is TKIP with WPA1.  Just want to confirm a few things before plowing ahead.

---

### Post by kevdog on 2008-03-14
ittiam -- good to see you've sticked with ubuntu -- We've met before in a previous post:
[http://ubuntuforums.org/showthread.php?t=715391](http://ubuntuforums.org/showthread.php?t=715391)

---

### Post by ittiam on 2008-03-14
yea, kevdog, i remember you. It was just not that one post alone, i remember you answering my other doubts as well. 

Well regarding this WEP-40, it is a bug and i guess it has already been filed. But this should not be a problem when using knetworkmanager as I had mentioned during our discussion.

---

### Post by alien21010 on 2008-03-14
The router shows it as being WPA1 with TKIP...  I'm not sure why it shows WEP-40 either.

---

### Post by kevdog on 2008-03-14
Try just following the WPA(1) steps specific in this thread as a means of testing:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by ittiam on 2008-03-14
Okay i understand that knetworkmanager for some reason is not working for you.

So lets try the command line configuration

1. Make sure your wired connection is disabled and unplugged.
2. Close whatever network manager you were using (knetworkmanager/nm-applet)
3. Create a file  /etc/wpa_supplicant.conf with the following contents 

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="ESSID_IN_QUOTES"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="ASCII PSK Password in Quotes" or generated_key_without_quotes
pairwise=TKIP
group=TKIP
}

```

After this execute the following commands

```


sudo pkill wpa_supplicant
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo wpa_supplicant -ieth0 -Dwext -c/etc/wpa_supplicant.conf -Bw


```

After executing the last command wait for some 15-20 seconds

then do

```

iwconfig

```

now you should see yourself attached to the AP. Then run,

```

sudo dhclient eth0

```

---

### Post by alien21010 on 2008-03-14
I tried that... It defaults to the unsecured network in my area again.  That doesn't make any sense...

---

### Post by ittiam on 2008-03-14
Are you sure that you don't have anything else running in the background or some other application running which is trying to connect to a default wireless network? Unless you have set that network as default by yourself, I do not see how can this happen.

---

### Post by kevdog on 2008-03-14
alien

Can you post your /etc/wpa_supplicant.conf file

Also can you post your terminal output?

---

### Post by alien21010 on 2008-03-14
I used the exact same wpa_supplicant.conf file that ittiam suggested.  I checked it again, and there is no difference between it and the other one.

---

### Post by alien21010 on 2008-03-14
At this point I'm thinking that I might just reinstall Feisty Fawn, and then upgrade to Gutsy Gibbon... I seem to remember that that worked.  All I know for sure is that something changed between Feisty and Gutsy, because it works great with an out of the box install of Feisty, and does not work at all with a fresh install of Gutsy.  Which is kind of depressing...

---

### Post by kevdog on 2008-03-14
You shouldn't need to do this.  Ok, so if the supplicant.conf file is the same, what are you typing at the command line?

---

### Post by ittiam on 2008-03-15
Ok alien the wpa_supplicant method I told it should work just fine. It does with me and so many others.

After the series of commands I told you, what happened when you did iwconfig? Could you post the output of it please.

 Also please double check the contents of wpa_supplicant.conf file, 
[LIST]
[*]whether you have entered in the correct essid (within quotations), it is case sensitive. 

[*]Also if you are using the password as ascii text, then it should be enclosed in quotations else if you have the password generated using wpa_passphrase, you shouldn't use the quotes.
[/LIST]

As kevdog suggested reinstalling feisty to get internet working should not be the case.

---

### Post by alphacrux on 2008-03-18
I haven't had any experience with WPA or ndiswrapper but I have had quite a bit of experience configuring wpa_supplicant to get my university's peap connection to work. I noticed you're calling wpa_supplicant with:
```
sudo wpa_supplicant -ieth0 -Dwext -c/etc/wpa_supplicant.conf -Bw
```

the -D option has to do with the driver you're using so I would think it should be:
```
sudo wpa_supplicant -ieth0 -Dndiswrapper -c/etc/wpa_supplicant.conf -Bw
```

also the -B option daemonizes the process which isn't good when your trying to debug, get rid of it and add the -dd option to the end which prints out all the debugging info, your command line entry should now look more like this:
```
sudo wpa_supplicant -w -ieth0 -Dndiswrapper -c/etc/wpa_supplicant.conf -dd
```

I hope this helps :)

---

### Post by kevdog on 2008-03-19
No do not use ndiswrapper for the -D option that is deprecated.  Its now wext -- if you read the documentation carefully.

---

### Post by alphacrux on 2008-03-25
I found an ubuntu how-to based on your wireless card and it is recommended that you reinstall the latest ndiswrapper version from source (actually not that hard the how-to breaks it down real nice.) 

Here's the  [[COLOR="Blue"]link[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D")

Also WPA, although generally more secure, is much more notorious for causing problems, maybe you should try using WEP to secure your network.

---

### Post by kup3rt1n0 on 2008-03-31
kevdog,

If memory serves (read don't quote me on this), 64-bit WEP is listed as 40-bit from time to time because the key itself is only 40 bits in length and the other 24 bits are overhead (the IV). This is the same reason that 128-bit WEP is sometimes listed as 104-bit. So, the larger numbers ( 64,128 ) are really misnomers.

---

### Post by kevdog on 2008-03-31
I didnt know that -- thanks for the input.

---

