---
title: "wpa_supplicant with Netgear WG311v3"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by teumima on 2006-11-02
Hi guys

I just installed WG311v3 on my Dapper. I used this howto:

[http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI](http://www.jimbo7.com/wiki/index.php?title=WG311v3_LINUX_WIKI)

It doesn't completely work.

Here is something info that should be useful:

# ndiswrapper -l

wg311v3         driver present, hardware present

# modinfo ndiswrapper

 filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
 author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
 version:        1.8
 license:        GPL
 vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
 depends:        usbcore
 srcversion:     40DD0BF42F95DD26FA6A8B5
 parm:           debug:debug level (int)
 parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
 parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
 parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
 parm:           if_name:Network interface name or tem
 
 # modinfo usbcore
 
 Filename:       /lib/modules/2.6.15-27-386/kernel/drivers/usb/core/usbcore.ko
 license:        GPL
 vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
 depends:
 alias:          usb:v*p*d*dc09dsc*dp*ic*isc*ip*
 alias:          usb:v*p*d*dc*dsc*dp*ic09isc*ip*
 srcversion:     6EADB132C67746CD35F8FA4
 parm:           usbfs_snoop:true to log all usbfs traffic (bool)
 parm:           use_both_schemes:try the other device initialization scheme if the first one fails (bool)
 parm:           old_scheme_first:start with the old device initialization scheme (bool)
 parm:           blinkenlights:true to cycle leds on hubs (bool)
 
 # iwconfig
 
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
 sit0      no wireless extensions.
 
 wlan0     IEEE 802.11g  ESSID:"tower_of_david"
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:E3:37:FA:FE
           Bit Rate:36 Mb/s   Sensitivity=-200 dBm
           RTS thr:2346 B   Fragment thr:2346 B
Power Management:off
           Link Quality:100/100  Signal level:-65 dBm  Noise level:-256 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwlist wlan0 scan

Cell 02 - Address: 00:16:E3:37:FA:FE
                     ESSID:"tower_of_david"
                     Protocol:IEEE 802.11g
                     Mode:Managed
                     Frequency:2.437 GHz (Channel 6)
                     Quality:0/100  Signal level:-61 dBm  Noise level:-256 dBm
                     Encryption key:on
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                               24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                               12 Mb/s; 48 Mb/s
                     Extra:bcn_int=100
                     Extra:atim=0
                     Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000
So then I do this:

# wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -Dwext

and get this:

octl[SIOCSIWSCAN]: Operation not supported
 Failed to initiate AP scan.
 Trying to associate with 00:16:e3:37:fa:fe (SSID='tower_of_david' freq=2437 MHz)WPA: 4-Way Handshake failed - pre-shared key may be incorrect
 CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
 Associated with 00:16:e3:37:fa:fe
 WPA: Key negotiation completed with 00:16:e3:37:fa:fe [PTK=TKIP GTK=TKIP]
 CTRL-EVENT-CONNECTED - Connection to 00:16:e3:37:fa:fe completed (auth)
 CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

This is what my /etc/wpa_supplicant.conf looks like:

network={
  ssid="tower_of_david"
  psk="kitty50"
  priority=5
  key_mgmt=WPA-PSK
  proto=WPA
}


Sometimes it stays like this:

 CTRL-EVENT-CONNECTED - Connection to 00:16:e3:37:fa:fe completed (auth)

The terminal won't close, so I'm just leaving a root process running open in my terminal. Doesn't seem right.

But then when I open a new terminal tab and type: [B]dhclient wlan0 

I get an IP from my routert dynamically. I get the ip 192.168.180.04 and my router is 192.168.180.1.

But I can't ping the router, and obvsiously I can't see any sites or do anything online.
[/B]
Any help would be greatly appreciated!

Thanks

a.t.

---

### Post by rrwo on 2006-11-02
I've gotten wpa_supplicant to work with the Netgear WG311v3 on Dapper and Edgy.

In my /etc/wpa_supplicant.conf file, I have 

```

network={
  ssid="Network.Name"
  key_mgmt=WPA-PSK
  psk=0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef
}

```

substituting the "ssid" and "psk" appropriately. If I recall, putting the plain password didn't work but putting in the hexidecimal form of the key does work.

In my /etc/network/interfaces file I have 

```

iface eth1 inet dhcp
pre-up /sbin/wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext
post-down killall -q wpa_supplicant

```

---

### Post by teumima on 2006-11-02
Thanx for the prompt reply man.

I'll try it tonight. Makes perfect sense. Netgear devices in many cases only work with hexadecimal. I know that routers that don't use hexadecimal cause problems for the WG111v2 and the WG311v3. 

I just thought wpa-psk wasn different.

So I'll try and let you know. Hopefully it will work.

			 				iface eth1 inet dhcp
pre-up /sbin/wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext
post-down killall -q wpa_supplicant

Your WG311v3 is recognised as a eth1? not wlan0? or you wanted it that way?

---

### Post by rrwo on 2006-11-02
Mine is recognised as eth1.

By the way, I've found it helpful to modify the hibernation script so that it shuts down the wireless network (since the next time I start up, I might be in a different network).  In the file /etc/hibernate/common.conf I change the DownInterfaces line to include the adapter, e.g.
```
DownInterfaces eth0 eth1
```
(The hibernate scripts might need to be installed using apt.)

---

### Post by teumima on 2006-11-02
So tell me man,

When I type in root

wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -Dwext

What is meant to happen?

Cos I get:

 CTRL-EVENT-CONNECTED - Connection to 00:16:e3:37:fa:fe completed (auth)

But it doesn't end until I press ctrl + c

Once it connects properly it exits?

---

### Post by rrwo on 2006-11-02
wpa_supplicant will not run in the background unless you specify the -B option.

It doesn't hurt to add the -w option as well (to wait for the interface to be added).

---

### Post by teumima on 2006-11-02
I want it to start on bootup and work in the background, how do i do that?

i'm always connected to the same router.

---

### Post by rrwo on 2006-11-02
> **teumima said:**
> I want it to start on bootup and work in the background, how do i do that?


Look at /etc/network/interfaces. Add the following:
```

auto eth1
iface eth1 inet dhcp

```
changing "eth1" to your wireless interface.

You may also need to add symbolic links for wpasupplicant in /etc/network/if-pre-up.d and /etc/network/if-post-down.d to /etc/wpa_supplicant/ifupdown.sh.

---

### Post by teumima on 2006-11-06
well I just upgraded to Edgy and now it doesnät work at all. Doesn't even recognize the card. 

Apparently others are having this issue too, did you upgrade?

a.t.

---

### Post by rrwo on 2006-11-06
I did upgrade, and of the *many* problems I had, wireless networking was not one of them.

---

### Post by teumima on 2006-11-07
well thats's comforting.

Can you share with me all your settings for the WG311v3?

all the areas where you put something.

I get driver present, hardware present

and that's as good as it gets!

a.t.

---

### Post by rrwo on 2006-11-11
I assume you want to know my wireless settings.

I have the Network Name (SSID) changed to a unique name (instead of the default, or something common like "Home" as I live in a flat and several neighbours have their own wireless networks).

The region is set to Europe (since that's where I live).

Channel is changed from the default to 7. (Sometimes when I have a spate of wireless problems, I change the channel in case a neighbour is using the same channel.)

I'm using WPA-PSK [TKIP] encryption.

For Advanced wireless settings, Enable Wireless Router Radio
Enable SSID Broadcast are both checked.  I also have a wireless card access list set up.

---

