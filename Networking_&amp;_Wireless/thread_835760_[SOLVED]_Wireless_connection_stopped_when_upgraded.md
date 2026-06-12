---
title: "[SOLVED] Wireless connection stopped when upgraded to Gutsy"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2008-06-20
I updated our family computer to Gutsy so that we could get my wife's new iPod Nano working with Amarok and now the wireless network is a wireless notwork. 
It was working fine right up until I rebooted into Gutsy. No changes were made to the settings from before that. I have tried all of the How Tos and troubleshooting guides I have been able to find (including the stickys at the top of the Networking & Wireless forum) to no avail.](*,) Can anyone help me?  

We have a Linksys WRT54G router with the latest firmware installed. Normally the MAC filter is running and the ESSID is not broadcasting but for the purpose of trying to get it working again I have dropped the MAC filter and started broadcasting the ESSID. The card is a Linksys WMP54G. As far as I can figure the card is recognised and the network signal can be picked up but there is no connection between the two. This is pretty obviously not my area of expertise so if I've left out any information that might be useful in diagnosing the problem please let me know.    


The output of *iwconfig* looks like this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

ra0       IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

My */etc/network/interfacesfile* looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#auto ra0
#pre-up ifconfig ra0 up
iface ra0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.106.0.1
        pre-up ifconfig ra0 up
        pre-up iwconfig ra0 essid romeo
        pre-up iwconfig ra0 mode Managed
```

Scanning for a newtwork using *iwlist rao scanning* gets:

```
ra0       Scan completed :
          Cell 01 - Address: 00:16:B6:A5:DC:7E
                    ESSID:"romeo"
                    Mode:Master
                    Channel:11
                    Frequency:2.412 GHz
                    Signal level=-30 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000001a001974
```

Any suggestions would be much appreciated.

---

### Post by Pjotr123 on 2008-06-20
Try Hardy 8.04. And avoid upgrading: a clean installation is always best:
[http://ubuntutip.googlepages.com/upgrading](http://ubuntutip.googlepages.com/upgrading)

---

### Post by greymoose58 on 2008-06-20
Cheers,

If I can't work out the problem shortly I think I'll take your advice. I'd like to learn a bit more about wireless networking though so I'll see if anyone has any other ideas before I do that.

I read the page you linked to and I won't be using the upgrade button again.

---

### Post by greymoose58 on 2008-06-21
Ok. I swallowed my pride/ignorance and downloaded the Hardy CD. Unfortunately the family computer this is all about doesn't have enough RAM to install it. So I'm back to  trying to fix the wireless setup. Do you think a clean install of Gutsy might resolve it?

Cheers.

---

### Post by greymoose58 on 2008-07-26
Finally sorted! :biggrin:

For any who follow in my footsteps here are links to the threads I found useful. 
After doing a clean install of Hardy Heron as suggested by Pjotr123 I got the wireless working but it dropped out on reboot. It seems that this is a bug in Hardy so I used the following to get it working again:

I got the driver suggested in _[this posting]("http://ubuntuforums.org/showthread.php?t=626246")_ and installed it as instructed. (The thread is for Gutsy but it seems to have worked on Hardy.)

Then I edited the interfaces file as suggested in _[this thread]("http://ubuntuforums.org/showthread.php?t=777036")_. I had to tweak it a bit for my system but it did the trick. 

Thanks to all for your help.

---

