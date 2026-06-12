---
title: "Wicd and Lan"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by stoopid1 on 2007-04-20
So I installed wicd (and had to remove network manager) in order for my wireless to work. At school, the wireless worked perfect.  At home, it wouldnt connect to my wep connection.  But I can use the good old fashioned network configurator tool that was standard on edgy (which i rather not use cause as I remembered, it gave me problems when trying to connect in school)

Anyway, after installing wicd, my lan is not working and my wifi seems to be working (with wep problems).  if i go back to network manager, my wifi is no longer working.  im practicaly a linux virgin, so be gentle.

here is what iwconfig gives me
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Porno Store"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:50:86:44   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:44  Invalid misc:2890   Missed beacon:0
```


here is what ifconfig gives me:

```

eth0      Link encap:Ethernet  HWaddr 00:16:D3:08:0F:C1  
          inet6 addr: fe80::216:d3ff:fe08:fc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8388 (8.1 KiB)  TX bytes:468 (468.0 b)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:624 (624.0 b)  TX bytes:624 (624.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:BD:55:47  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:febd:5547/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1242003 (1.1 MiB)  TX bytes:226633 (221.3 KiB)
          Interrupt:19 Memory:c3000000-c3004000 

```

Anyway, help would be much appreciated.  ive spent all day on this.

P.s im using rotten ndiswrapper and i have a rotten bcm4311 (may god have mercy on my soul)

---

### Post by handaxe on 2007-04-20
When lan is clipped in try ```
sudo dhclient eth0
``` and see if that gets the interface working.

As for the WEP issue, wicd does not take the ascii passphrase but the hex key.  Make sure that the router is using key 1 as the default tansmit key and enter the key1 hex string into wicd.

I have had wireless interference problems before but that usually comes in the form of dropped /interrupted connects. Many close-by wireless APs can cause this and it is solved by changing the wireless channel. Not likely to be your problem....???

HA

PS look here for dedicated wicd help : [http://adam.blackhole.cx/wicd/phpbb/index.php](http://adam.blackhole.cx/wicd/phpbb/index.php)

---

### Post by stoopid1 on 2007-04-20
well, that got my lan working, but not with wicd but the network configurator tool (or what ever it is called.)  Im not sure what you mean about the WEP key.  I converted my wep passphrase into hex (so that the 819, for example, translates to %38%31%39) and i can't figure out what you mean by inserting into key 1 and making key 1 as the default transmit signal.

please have patience with me :)

Thank you for your help so far.

when I use *sudo dhclient eth0* my wlan0 stops working, and i can't connect to it anymore and i can get it to work if I restart or something (or what ever it is I did that made it work again).  I switch between wlan and etc sometimes at school, so this is a pain in the ***.  everything just seems so volatile.

---

### Post by handaxe on 2007-04-20
Hi,

In a huge rush....

Try posting on the Wicd forum...

I know that Network-Manager does not have wireless working with wired. It does on my laptop but your mileage may vary on this one. The point is, if you have been clipped in and you then unclip and switch to wireless, does Wicd connect you to the AP?

What is in the file /etc/networking/interfaces ?  You might try and delete everything except the lo interface (back-up the file first!!!), reboot and see wots wot.

WEP - some routers generate 4 hex keys from the ascii pass phrase and have an option to set one of the four as the default. If your router is using anything other than the first key, then Wicd may have trouble connecting. Use key one. 

It seems that you are ok with respect to how you enter the key...

The following is a good wep guide:
[http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

HA

---

