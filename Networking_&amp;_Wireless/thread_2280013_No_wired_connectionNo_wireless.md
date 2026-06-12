---
title: "No wired connection/No wireless"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by lorem_ipsum2 on 2015-05-27
Hello,

I'm fairly new to Ubunutu/Lubuntu.  When I type lsb_release -a, I get that I am using Ubuntu 15.04 vivid.  I have no wired connection and no wireless connection.  My aim with this post is to fix the wired connection.

I've read a dozen similar threads, but they all seem specific to the computer.  Also, I don't fully (or even partially) understand what some of the commands recommended are doing. I'd rather ask now than guess and have to backtrack.   All the threads direct to check ifconfig and/or lspci.  Here is what I obtain from these:

ifconfig
```

eth0      Link encap:Ethernet HWaddr 00:15:c5:1d:d6:ec          
          inet6 addr: fe80::215:c5ff:fe1d:d6ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:190350 (190.3 KB)  TX bytes:12799 (12.7 KB)
          Interrupt:17


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44228 (44.2 KB)  TX bytes:44228 (44.2 KB)

```

lspci -nn -d 14e4:
```

s02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

If you could please advise me on what to do next, I would appreciate it.

---

### Post by chili555 on 2015-05-27
You seem to have a wired ethernet interface; namely eth0. That suggests that the correct driver has associated with the hardware. Let's see if the correct driver is listed in all the modules currently loaded. At the same time, I'd like to check a few things that will help us with the wireless in a few minutes:```
lsmod | grep -e b44 -e wl
```That means, roughly: list the modules, but only show me b44 and/or wl.

Let's also see if the message log has any interesting messages about the driver b44 or the interface eth0:```
dmesg | grep -e b44 -e eth0
```Please be sure that a working ethernet cable is attached as you run these diagnostics.

Once we know the results, we'll proceed.

---

### Post by lorem_ipsum2 on 2015-05-27
Thank you for your help.  Here's what I get.

lsmod | grep -e b44 -e wl
```

[COLOR=#ff0000]b44                    [/COLOR]36864  0 
mii                    16384  1 [COLOR=#ff0000]b44[/COLOR]
ssb                    57344  3 b43,[COLOR=#ff0000]b44[/COLOR],ssb_hcd

```

dmesg | grep -e b44 -e eth0
```

[    1.476298] [COLOR=#ff0000]b44[/COLOR]: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.496713] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:15:c5:1d:d6:ec
[   13.050052] Modules linked in: snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   13.858192] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   14.023892] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   15.186881] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   15.343910] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   26.206347] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[   26.356129] Modules linked in: snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[  887.988336] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Link is up at 100 Mbps, full duplex
[  887.988348] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Flow control is off for TX and off for RX
[ 1081.988245] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Link is down
[ 1140.174017] Modules linked in: nls_iso8859_1 uas usb_storage snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[ 2066.778039] Modules linked in: nls_iso8859_1 uas usb_storage snd_hda_codec_idt b43 snd_hda_codec_generic snd_hda_intel gpio_ich snd_hda_controller snd_hda_codec snd_hwdep bcma dell_laptop mac80211 pcmcia snd_pcm dcdbas snd_seq_midi yenta_socket snd_seq_midi_event coretemp pcmcia_rsrc i8k snd_rawmidi joydev i915 cfg80211 pcmcia_core snd_seq serio_raw lpc_ich ssb_hcd snd_seq_device snd_timer irda drm_kms_helper snd crc_ccitt drm soundcore i2c_algo_bit mac_hid shpchp 8250_fintek video parport_pc ppdev lp parport autofs4 [COLOR=#ff0000]b44 [/COLOR]psmouse firewire_ohci firewire_core mii pata_acpi crc_itu_t ssb
[ 5359.988334] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Link is up at 100 Mbps, full duplex
[ 5359.988345] [COLOR=#ff0000]b44 [/COLOR]ssb1:0 [COLOR=#ff0000]eth0[/COLOR]: Flow control is off for TX and off for RX

```

---

### Post by chili555 on 2015-05-27
With regard to the driver b44, everything looks pretty normal. However, when we see this line:```
Modules linked in: snd_hwdep bcma dell_laptop mac80211 pcmcia <snip>
```...it is usually symptomatic of a problem, sometimes minor, where a process crashed and is most often restarted. Just because b44 was one of many modules that were running at the time doesn't necessarily mean it is the problem. Let's look at that a bit later.

Let's now try to see why Network Manager isn't connecting the usually reliable b44; we'll check the more comprehensive system log:```
cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
cat /etc/network/interfaces
```

---

### Post by lorem_ipsum2 on 2015-05-27
cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```

May 27 06:45:28 NaturalFlavors NetworkManager[556]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 27 06:45:28 NaturalFlavors NetworkManager[556]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 27 06:45:28 NaturalFlavors NetworkManager[556]: <info> dhclient started with pid 2166
May 27 06:45:28 NaturalFlavors NetworkManager[556]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 27 06:45:28 NaturalFlavors NetworkManager[556]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 27 06:45:28 NaturalFlavors dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x74ec9a0b)
May 27 06:45:30 NaturalFlavors ntpd[531]: Deleting interface #9 eth0, fe80::215:c5ff:fe1d:d6ec#123, interface stats: received=0, sent=0, dropped=0, active_time=47 secs
May 27 06:45:30 NaturalFlavors avahi-daemon[563]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::215:c5ff:fe1d:d6ec.
May 27 06:45:30 NaturalFlavors avahi-daemon[563]: New relevant interface eth0.IPv6 for mDNS.
May 27 06:45:30 NaturalFlavors avahi-daemon[563]: Registering new address record for fe80::215:c5ff:fe1d:d6ec on eth0.*.
May 27 06:45:31 NaturalFlavors dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 (xid=0x74ec9a0b)
May 27 06:45:32 NaturalFlavors NetworkManager[556]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
May 27 06:45:32 NaturalFlavors NetworkManager[556]: <info> Activation (eth0) Beginning DHCPv6 transaction (timeout in 45 seconds)
May 27 06:45:32 NaturalFlavors NetworkManager[556]: <info> dhclient started with pid 2172
May 27 06:45:32 NaturalFlavors NetworkManager[556]: <info> (eth0): DHCPv6 state changed nbi -> preinit6
May 27 06:45:33 NaturalFlavors dhclient: XMT: Solicit on eth0, interval 1040ms.
May 27 06:45:34 NaturalFlavors dhclient: XMT: Solicit on eth0, interval 2040ms.
May 27 06:45:34 NaturalFlavors ntpd[531]: Listen normally on 10 eth0 fe80::215:c5ff:fe1d:d6ec UDP 123
May 27 06:45:35 NaturalFlavors dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0x74ec9a0b)
May 27 06:45:36 NaturalFlavors dhclient: XMT: Solicit on eth0, interval 4120ms.

```

cat /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2015-05-27
Please open a terminal and do:```
gksudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit. Add the # symbol as I've indicated:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


[COLOR="#FF0000"]#[/COLOR]source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Restart NM:```
sudo service network-manager restart
```Any improvement? It may take a reboot.

---

### Post by lorem_ipsum2 on 2015-05-27
I updated [COLOR=#000000][FONT=Ubuntu Mono]/etc/network/interfaces[/FONT][/COLOR] as directed.  It was just the single # before source, correct?  To comment it out?

I found your next direction ambiguous.  I thought we were getting the wired connection working first and disregarding the wireless for the moment?  Regardless, I have no wi-fi connection in the network manager and I cannot create one without entering in specifics.  I updated the wired connection's IPv6 Method to "Ignore," restarted the NM, and then rebooted.  Still no connection.

---

### Post by chili555 on 2015-05-28
> It was just the single # before source, correct? To comment it out?Yes, exactly.> I found your next direction ambiguous. Ouch! Sorry about my mis-step. I meant ethernet and said wireless. I'm glad you caught and corrected it.> Still no connection.Let's check the log again:```
cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```> I have no wi-fi connection in the network manager and I cannot create one without entering in specifics.Even if you entered some specifics, which is generally unnecessary, your wireless won't work without installing firmware. It can be done without an internet connection but is a whole lot easier with one! That's why I suggest, for the moment, to concentrate on ethernet.

---

### Post by lorem_ipsum2 on 2015-05-28
The wired connection is working.  I was plugging directly into my modem.  When I plug into my wireless router (which is of course connected to my modem), I am able to connect to the internet.  I'm guessing this is because the modem is configured for another device, probably my desktop.  I went back to /etc/network/interfaces and removed the # so that it reads

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

```
like it did originally.  The wired connection continues to work just fine.

Now, concerning the wireless, I worked through the troubleshooting guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
and established that the wireless card is recognized and that the driver is installed.  When I go to "Additional Drivers" in "Software & Updates", I see the driver for BCM4311 802.11b/g WLAN (Wireless 1390 WLAN Mini-Card) as I would expect, but "Do not use the device" is selected.  The other option is "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)".  Upon selecting that option, it is automatically deselected and "Do not use the device" is instead selected.  Googling a solution to this brought me, inevitably, to your sticky: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

I was not sure whether or not I had installed any packages concerning this yet, since I had confirmed above that the driver was already installed.  So, I first ran
```

sudo apt-get purge bcmwl-kernel-source

```
to which I received the message "Package 'bcmwl-kernel-source' is not installed, so not removed".  This seemed strange since the "Additional Drivers" lists the Broadcom as having that very same source.

Since bcmwl-kernel-source was apparently not installed, and I had just installed lubuntu, I figured I would run the update
```

sudo apt-get update

```
which ran and seemed to do its thing just fine.  I did your next step to install the proper driver.  I repost my wireless card here:

lspci -nn -d 14e4:
```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```
which corresponds to package 
```
[COLOR=#000000][FONT=Ubuntu Mono]14e4:4311                  firmware-b43-installer                firmware-b43-installer[/FONT][/COLOR]
```

I then ran 
```

sudo apt-get install firmware-b43-installer

```
which ran just fine.  I rebooted.  Right-clicking on the connection icon, I now see a faded "Enable Wi-Fi" which was absent before, but I cannot select it.  I tried going back into "Additional Drivers" but had the same problem as before.  It doesn't allow me to select anything.

I'm confused why "Additional Drivers" lists bcmwl-kernal-source instead of something related to firmware-b43.  From your list of packages, it seems like bcmwl-kernal-source is something different than firmware-b43-installer.  And just for prosperity, my phone is connected to my wi-fi, so I know that the wi-fi is functional (no more gaffs like with the wired connection!).  Where do I go from here?

---

### Post by chili555 on 2015-05-28
```
it seems like bcmwl-kernal-source is something different than firmware-b43-installer.
```That is correct.> I'm confused why "Additional Drivers" lists bcmwl-kernal-source instead of something related to firmware-b43. Me, too. The Additional Drivers tool is just plain wrong in several instances. It wants to install bcmwl-kernel-source for several devices for which it is wrong. The most glaring example is yours:> Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="#FF0000"]14e4:4311[/COLOR]] (rev 01)Even Broadcom's own documentation is wrong in this case.

Let's troubleshoot what's going on with your wireless:```
rfkill list all
dmesg | grep b43
iwconfig
```Congratulations on actually reading and following the stickie! Good work.

---

### Post by lorem_ipsum2 on 2015-05-29
No problem.  It's the least I could do, especially when someone like yourself is taking time help me out.  Here's what the following produced:

rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

dmesg | grep b43

```

[   15.384816] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.416164] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   15.416186] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   33.768104] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   33.908132] b43-phy0: Radio hardware status changed to DISABLED

```

iwconfig
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

---

### Post by chili555 on 2015-05-29
> Hard blocked: yesThis says the wireless switch or key combination is turned off. Can you find it and switch it? What brand and model laptop is this?

---

### Post by lorem_ipsum2 on 2015-05-29
I'm glad to say, this post is being made from wireless.  For prosperity, I have a Dell Latitude D520.  I can't believe it was as simple as a hard on/off switch!  But that's what a fool believes.

Thank you very much for your help.  Please accept this video in thanks: [https://youtu.be/vX2J6mceWic](https://youtu.be/vX2J6mceWic)

---

### Post by chili555 on 2015-05-29
Thank you very much! I am always happy to see that big ole Solved no matter what the means. Usually, it means that the user can now upload, download, apt-get install, email, etc. and that the hard part is done and the fun part can now begin.

Have fun, my friend!

---

