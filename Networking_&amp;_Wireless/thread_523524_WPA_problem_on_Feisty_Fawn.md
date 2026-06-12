---
title: "WPA problem on Feisty Fawn"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by CrowBoy1960 on 2007-08-12
Hi all,

I'm just installing 7.04 and am very impressed with how far it's come. Everything went well (even dual monitor setup, very easy with nvidia setup program :) but Wireless connection is proving to be painful. I followed the excellent HOWTO at [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) and did what it said but am still having problems.

Thanks in advance,
Martin.

When I go "sudo /etc/init.d/networking restart" I get:

 * Reconfiguring network interfaces...                                                      RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

 iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"myid"  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:33481  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here is my interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.254

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 192.168.1.20
netmask 255.255.255.0
dns-nameservers 192.168.1.254
gateway 192.168.1.254
       wpa-ssid myid
       wpa-ap-scan 2
       wpa-proto WPA # RSN
       wpa-key_mgmt WPA-PSK
       wpa-pairwise TKIP # CCMP 
       wpa-group TKIP #CCMP
 wpa-psk <myhexkey>

pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

#auto wlan0
#iface wlan0 inet dhcp


and /etc/wpa_supplicant.conf:

# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/examples/README.wpa_supplicant.conf.gz
#  for more complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
#  specific configuration examples.

# path to UNIX socket control interface
ctrl_interface=/var/run/wpa_supplicant

### Example of basic WPA-PSK secured AP
#network={
#    ssid="ournet"
#    psk="w243sd5f324asdf5123sadf54324"
#}

          ctrl_interface=/var/run/wpa_supplicant
          ctrl_interface_group=wheel

network={
       ssid="myid"
       scan_ssid=2
       proto=WPA # RSN
       key_mgmt=WPA-PSK
       pairwise=TKIP # CCMP 
       group=TKIP #CCMP
        psk=<my hex key>
}


ifconfig output:

ath0      Link encap:Ethernet  HWaddr 00:09:5B:E7:FD:B3  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fee7:fdb3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:50:8D:9F:1A:CA  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe9f:1aca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3086604 (2.9 MiB)  TX bytes:995872 (972.5 KiB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17085 (16.6 KiB)  TX bytes:17085 (16.6 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-E7-FD-B3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35166 errors:0 dropped:0 overruns:0 frame:3
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3305652 (3.1 MiB)  TX bytes:15346 (14.9 KiB)
          Interrupt:18

---

### Post by bwtranch on 2007-08-12
Looks like the wireless extensions didn't load. 

dmesg | less

this will give us the mods that loaded at boot. The option less just makes it easier to page. I can tell you are smart so I don't have to spell everything out.

---

### Post by bwtranch on 2007-08-12
:lolflag:

---

### Post by CrowBoy1960 on 2007-08-12
Thanks for the tip and the compliment :). I found this using dmesg:

[   46.423473] wpa_supplicant[4083]: segfault at 0000000000000048 rip 0000000000421acf rsp 0
0007fffc9fed2d0 error 4

and ps tells me that wpa_suplicant is running like this:

/sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.ath0.pid -i ath0 -D wext -C /var/run/wpa_supplicant

so I'm guessing that the -D wext is causing the crash as it should be madwifi. Presumably  wpa_supplicant is getting called from somewhere else and it's not using the line from the interfaces file:

pre-up /sbin/wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

Would anyone have any idea where this would be?

Thanks again,
Martin.

---

### Post by kevdog on 2007-08-12
I see your problem, and not sure if I can explain it.  

Do you really need 

pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

Included in the interfaces file??  Is this just referencing a wpa_supplicant.conf file -- the information that is redundant to your information in the interfaces file?

---

### Post by CrowBoy1960 on 2007-08-12
Just a bit more info, when I copy and paste the string to run wpa_supplicant into a terminal it works fine and iwconfig shows it has connected OK:

```
>wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf 
```

but when I try and restart the networking I get this

```
>sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...         
SIOCDELRT: No such process
[COLOR="Red"]bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it[/COLOR] Maybe this is a/the problem? Any thoughts?
Delete '/var/run/wpa_supplicant/ath0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Segmentation fault (core dumped)
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

and once again the last part of the interfaces is:
```

pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

---

### Post by kevdog on 2007-08-12
Forget the interfaces file for a moment, does WPA work if you try to configure and make the connection all at the command line??  I usually try something like this, although your config file should work:

Manual WPA setup -- some tips:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
       ssid="<your networks essid>"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=<really long string of hex characters>
}

```

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

```

---

### Post by CrowBoy1960 on 2007-08-13
Followed the steps in kevdogs' post and it all worked OK, brought eth0 down, ripped out the ethernet cable and I'm now going through wireless link, the trouble is how to get it to start up automatically. If not via the interfaces pre-up, is there another way of doing it?

The problem still seems to be that when wpa_supplicant starts it has -Dwext instead of -Dmadwifi and I have no idea where it is getting that from, as in the interfaces file I have -Dmadwifi.

Thanks to everyone for their help, it seems that I'm dangerously close to getting it sorted. Hopefully....

Ta,
CB.

---

### Post by wirelessmonkey on 2007-08-13
It's entirely possible that you have configured wpa in network-manager, which saves a startup command in its own configuration, hence the -Dwext.

---

### Post by CrowBoy1960 on 2007-08-14
No, network-manager got un-installed when I installed one of the Wifi utilities. Seem to have have run into a bit of a brick wall.

Thanks anyway,

CB

---

### Post by kevdog on 2007-08-14
Havent seen your post from in a while.  Just one last question -- when you typed the commands at the command line and got them to work for you -- did you use -Dwext or -Dmadwifi???

Makes a difference in how the /etc/network/interfaces file will be configured.  As an alternative, if network manager doesnt work for you (that is what you are using), its always possible to switch to WICD, which basically is a GUI similar to network manager, but basically uses the exact same commands (as the command line), but automates them so you dont have to type them.  I think network manager doesnt something similar however I can not confirm this fact.

---

### Post by CrowBoy1960 on 2007-08-14
Thanks for your reply.

When it worked on the command line I had -Dmadwifi as I have an Athenos card. The problem is when it is running automatically it is picking up the -Dwext from somewhere. I haven't come across WICD so I'l try that.

Regards,
CB

---

### Post by CrowBoy1960 on 2007-08-22
Installed WICD and it's a pretty cool tool. It got rid of the problem with the -Dwext as now wpa_supplicant runs like this:

root     24961     1  3 20:49 ?        00:00:00 wpa_supplicant -B -i ath0 -c encryption/configurations/0013d37813bb -D madwifi

encryption/configurations/0013d37813bb looks OK, has all the right stuff

Get this output:

 >iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:11870  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 >ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:09:5B:E7:FD:B3  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:13 dropped:13 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3164 (3.0 KiB)  TX bytes:6242 (6.0 KiB)

and from dmesg:

[   49.072153] ath_rate_sample: 1.2 (0.9.3.1)
[   49.072482] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   49.072488] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 1
8Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   49.072496] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54M
bps
[   49.072501] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   49.072505] wifi0: mac 5.6 phy 4.1 radio 1.7
[   49.072509] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   49.072511] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   49.072513] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   49.072515] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   49.072516] wifi0: Use hw queue 8 for CAB traffic
[   49.072518] wifi0: Use hw queue 9 for beacons
[   49.094314] wifi0: Atheros 5212: mem=0xfd0f0000, irq=18
[   49.322812] NET: Registered protocol family 17
[   49.347053] wpa_supplicant[4273]: segfault at 0000000000000048 rip 0000000000
421acf rsp 00007fff01d655a0 error 4  --- Mmmm, still seg faulting :(

[  126.724833] ADDRCONF(NETDEV_UP): ath0: link is not ready - Lots of these ---

So not really getting any closer.

Anyone got any suggestions of other things to try?

Thanks,
CB

---

### Post by wieman01 on 2007-08-22
First of all, can you connect to unsecured networks? That's a crucial step as it will tell us if your adapter works at all.

Second, you don't need this line:
> wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
...if you do all the configuration in "/etc/network/interfaces". 

Also make sure the Ethernet cabled it pulled when you restart the network. Please also post the output of:
> sudo iwlist scan

---

### Post by CrowBoy1960 on 2007-08-22
I managed to get it working by selecting the "Hidden Network" option, put the ESSID in and then got it to connect OK. Just looks like it won't start automatically, because it wasn't up when I re-booted. But I can live with manually starting it :)

Thanks to everyone for their help,

Martin.

---

### Post by imdano on 2007-08-22
Right now connecting at boot to hidden networks isn't supported, but I've been working on adding it the last couple of days, so there will probably be a patch for it soon.  It's odd that the essid isn't getting set if you don't specify it by making the network hidden.  I wonder if the interface isn't getting up in time during the connection process or something.

---

