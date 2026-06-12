---
title: "Need help connecting wireless card to network (WPA-PSK)."
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by 80x on 2008-07-29
After spending days trying to set up a wireless connection, I'm so frustrated and ready for some help.

I've got a computer running Hardy Heron Ubuntu Server Edition (so no GUI; all CLI). The sticker on the wireless card says it is a Belkin F5D6001 (ver. 2114), and I'm trying to get it to connect to my WPA-PSK router. I had read that ndiswrapper with net8180 Windows XP driver was needed to set up the F5D6001 card, but after spending hours setting up ndiswrapper, I realized that I have a different version of the F5D6001 that works with the adm8211 driver included with Ubuntu, so I don't need ndiswrapper after all. The card works: It detects my wireless network, but I just can't get it to connect. When I try and ping my router I get "Destination Host Unreachable." Here are some settings and info:


When I type:
```

sudo ndiswrapper -l

```
I get:
```

net8180 : driver installed
        device (1317:8201) present (alternate driver: adm8211)

```
I tried adding "blacklist adm8211" to /etc/modprobe.d/blacklist but I still got the same message, and when I typed "sudo iwlist wlan0 scan" I got "wlan0 No scan results". With adm8211 not blacklisted, wlan0 is able to detect my wireless network. So I have un-blacklisted adm8211. I'm pretty sure I don't need ndiswrapper. I haven't uninstalled it yet though.



When I type:
```
lspci | grep Network
```
I get:
```
00:0e.0 Network controller: ADMtek ADM8211
```



When I type:
```
lshw
```
The wireless card shows up in the list as:
```

*-network
     description: Wireless interface
     product: ADM8211 802.11b Wireless Interface
     vendor: ADMtek
     physical id: e
     bus info: pci@0000:00:0e.0
     logical name: wmaster0
     version: 11
     serial: 00:30:bd:e0:ea:f5
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list logical ethernet physical wireless
     configuration: broadcast=yes driver=adm8211 ip=192.168.1.150 latency=64 maxlatency=128 mingnt=64 module=adm8211 multicast=yes wireless=IEEE 802.11b

```



When I type:
```
sudo iwlist wlan0 scan
```
I get:
```

wlan0 Scan completed:
      Cell 01 - Address: 00:0F:CC:6E:F8:F4
                ESSID:"Mynetworkname"
                Mode:Master
                Channel:9
                Frequency:2.452 GHz (Channel 9)
                Quality:0 Signal level:0 Noise level:0
                Encryption key:on
                IE: WPA Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (1) : TKIP
                    Authentication Suites (1) : PSK
                IE: IEEE 802.11i/WPA2 Version 1
                    Group Cipher : TKIP
                    Pairwise Ciphers (1) : CCMP
                    Authentication Suites (1) : PSK
                Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                          48 Mb/s; 54Mb/s
                Extra:tsf=0000000f7d83b192

```
*Of course where I put "Mynetworkname" it actually had the real name of my network.



When I type:
```
iwconfig
```
I get:
```

lo        no wireless extensions

wmaster0  no wireless extensions

wlan0     IEEE 802.11b ESSID:"Mynetworkname"
          Mode:Managed Frequencey:2.412GHz Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7 RTS thr:off Fragment thr=2346 B
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```
That's how it is right after I boot the computer up. I can successfully change the Frequency to 2.452GHz and the Access Point to 00:0F:CC:6E:F8:F4 (in order to match the results of "sudo iwlist wlan0 scan") by typing:
```

sudo iwconfig wlan0 channel 9
sudo iwconfig wlan0 ap 00:0F:CC:6E:F8:F4

```
Although, I already have the Access Point specified as 00:0F:CC:6E:F8:F4 in /etc/network/interfaces. I don't know why it  still changes back to Not-Associated when I reboot. The frequency also goes back to 2.412 GHz whenever I reboot. (Is there a way to specify frequency in /etc/network/interfaces?)



Here is **/etc/network/interfaces**:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-essid Mynetworkname
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.254
broadcast 192.168.1.255
network 192.168.1.0
mode Managed
ap 00:0F:CC:6E:F8:F4
pre-up wpa_supplicant -Bw -Dadm8211 -i wlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```



Here is **/etc/wpa_supplicant.conf**:
```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="Mynetworkname"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=reallylongnumberthatidontwantotype
}

```

The computer pings itself successfully ("ping 192.168.1.150").
When I try "ping google.com" I get "ping: unknown host google.com".
When I try and ping the router:
```

ping 192.168.1.254

```
I get:
```

From 192.168.1.150 icmp_seq=1 Destination Host Unreachable

```

The router is a Netopia 3347NWG-006. The address I type in my browser to access it's settings page is 192.168.1.254:8080 (it used to be just :80 but I changed it to :8080 because I want to forward port 80 to my web server). The router assigns IP addresses 192.168.1.1 through 192.168.1.253. I want to set a static IP for my server, and I randomly picked 192.168.1.150. (NOTE: I am aware that the best thing for a server is to have it plugged straight into the router through ethernet, but I want to go ahead and set up this wireless card anyway. It's just a fun personal project, and I'd like the computer to be at the back of my closet and not in the middle of the house by my router - it's going to be headless.)

I'm really really frustrated here. I've been tweaking settings for hours with no results. Is it just impossible to get this wireless card working with my router at all? The card is able to detect the network, but apparently not connect, since I can't ping the router. The box was running Windows 98 before I replaced it with Ubuntu. The card worked with our old router, but since we got the Netopia 3347NWG-006 we couldn't get it to connect with Windows 98. I thought it might be possible to do it with Ubuntu.

Anyway, somebody please please help! I've tried everything! What am I doing wrong? :mad:

EDIT: Oh, and if it's any help, I remember that when I was installing Ubuntu, it had trouble at the part where it tries to detect network hardware.

---

### Post by oni5115 on 2008-08-10
I'm having the exact same problem with a Blittz net-wave card.

I type: lspci -v | less
resulting in:
> 01:00.0 Network Controller: ADMtek ADM8211 802.11b Wireless Inferface (rev 11)
Subsystem: ADMtek SMC2635W 802.11b (11 Mbps) wireless lan pcmcia (cardbus) card
...

/etc/network/interfaces
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid NAMEHERE
wireless-key  KEYHERE
wireless-channel 6
wireless-mode managed

Naturally, the key/name are the actual values.  The channel is the same as my router.  I am actually using WEP, not WPA-PSK, with a 26 digit hex code.

Note: I've read somewhere else you might need to put in wireless-key s:XXXXXX  if you are using a string phrase instead of hex code, I tried it both ways and neither worked for me, but maybe that would work for you.

I don't have wpa_supplicant, nor do I know how to install it.  I am using 8.04 command line install, instead of server.  I was planning to install iceWM and/or fluxbox and mess with them, except they aren't on the alt install CD and I can't access the repositories. :(

At one point I did have it displaying on my routers connected devices, but it only listed the mac address of the card.  No IP, nor computer name.  Nothing I tried would actually give the laptop an IP address, at least not one recognized by the network.  Manually setting one with ifconfig did nothing for me.  Still could not ping any other computers, or the router for that matter.  So while it seemed like I was doing something right, still no connection.

On a side note, I did somehow screw something up in the process.  So I get to run rescue mode and try and fix Grub's 'error 17' that I loaded too.  *sigh*

---

### Post by oni5115 on 2008-08-12
Just thought I would add some more feedback.  After a re-install I followed a few other threads, and managed to get the thing working! :)  Then I crashed, and grub blew up, giving me error 17 again.  :mad:  I really wish the install disk simply had a "Fix Grub" option on it.   This comp is so small it can't run live cd's, and I have yet to find a command-line live-cd of ubuntu.

Regardless, I had to blacklist the adm8211 drivers, they seem to be broken (at least for WEP connections).  As mentioned previously, I had it detecting the router, and even showing up on the router as a device, but it just would not get an IP address at all.

Seems you have/had ndiswrapper installed, so I will skip that part.

sudo modprobe ndiswrapper
sudo ndiswrapper -m

cd to the path of your drivers on the driver CD
sudo ndiswrapper -i FILE_NAME.inf

If you run an iwconfig it should now have wlan0 showing (even with adm8211 driver blacklisted).

Then run whatever iwconfig commands for essid and ecnryption you need to run.  I used WEP, and never have tried WPA so I'm not really sure how to set that part up.  That said, even though ndiswrapper -m is supposed to make it run again after reboot, it never did for me.

For more in-depth guides you can check:
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
[http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa](http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa)

---

