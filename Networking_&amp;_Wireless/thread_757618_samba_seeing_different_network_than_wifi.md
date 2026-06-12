---
title: "samba seeing different network than wifi"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by gedden on 2008-04-17
so this is interesting. I am connected to my wireless router, however i seem to be seeing a different network in my samba browsing. I am using a compaq armada m300 with a cisco aironet 350. My network is called apartment.

```
eth1      Scan completed :
          Cell 01 - Address: 00:18:39:7E:4B:17
                    ESSID:"apartment"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-43 dBm  Noise level:-89 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1B:5B:DB:1F:E9
                    ESSID:"2WIRE491"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/100  Signal level=-61 dBm  Noise level:-89 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:1C:10:14:F0:C3
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level=-70 dBm  Noise level:-89 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
```

earlier today I tried to access my windows shares for the first time since I switched from mac filtering to wpa personal. Before I was able to see my shares and access them. After the switchover, I was seeing a share that made me think that I was seeing computers that were not mine and had names similar to the 2wire thing in the output above. At the time of this posting I cannot see anything in my windows share folder. I changed the workgroup name to a non default and still did not see anything.
 Any thoughts?

---

### Post by fsmithred on 2008-04-20
Do iwconfig to see if your wireless card is on the same channel as your router. Maybe pick a different channel for both. Check that your encryption key is set up right, too, or turn off encryption to test the connection. 

Do ifconfig on two computers to make sure they both have numbers that exist in your local network. (This was the big tipoff for me when I first got my wireless connected but couldn't ping my local machines.)

Surf to grc.com to see what your public IP number is and if it matches with what you get on your other machines. That'll tell you if all your computers are surfing from your apartment or not.

---

### Post by dmizer on 2008-04-20
looks like you're probably connected to cell 03 which does not have encryption enabled.

so yes, you're probably right.  you're looking at computers that are not yours.

a quick look at the essid (probably "linksys") in the output of:
```
sudo iwconfig
```
should confirm this.

---

### Post by gedden on 2008-04-22
You are correct dmizer and fsmithred, Thank you!
So I see from my iwconfig that I am on a different network than I thought I was. I have been confused by an error I had at the initial configuration of this laptop. This is apparent in the output of iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:14:F0:C3   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-91 dBm
          Rx invalid nwid:462  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:251775   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:14:F0:C3   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-91 dBm
          Rx invalid nwid:462  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:251775   Missed beacon:0

```

I was always wondering how to get the name of my wifi card to wifi0 instead of it liking to use the eth1 name. I was having trouble using any other device in the default network manager other than eth1. I also need to delete the duplication. I am surprised that I am connecting to a different network when I have the network on manual configuration and it should only connect to the network named 'apartment.'

so it appears i might need to research this a little more and post a new thread! 
If there are any outputs you would like to see I can post them ASAP.
thanks again!
andy

---

### Post by fsmithred on 2008-04-22
It might help to see /etc/network/interfaces. If you're using wpa, you can find examples for the interfaces file in /usr/share/doc/wpasupplicant.

I don't know what to tell you about the duplicate entries.

---

### Post by gedden on 2008-04-22
This is my interfaces file. It seams clear to me after taking a glance over it, that this is the one of the sources of the problem. As far as I can tell all the settings in the manual configuration are not in this file. Is there a place where the settings I specified would be stored for a quick cut and paste?  I haven't had time to look at the wpa stuff so I'll check it out tomorrow, with some reading on networks interfaces its self. Thanks for the help. Here is a odd thing that I found. After some tinkering with workgroup names a couple of days ago, I had a samba share folder appear on my desktop. It has the proper name of the computer that I want to share with, but I have been unable to get any files to appear in the browser. My guess is, at some point I was connected to the proper router. The samba share is created automatically and doesn't update depending on the status of the connection.
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp




iface wifi0 inet dhcp
wireless-essid apartment

```

---

### Post by fsmithred on 2008-04-22
For comparison, my interfaces file looks something like this:

iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid linksys
wpa-psk <passphrase>


I've heard that network manager stores its settings in /etc/network/interfaces, and I've seen it do that. I've also seen it not do that.

---

