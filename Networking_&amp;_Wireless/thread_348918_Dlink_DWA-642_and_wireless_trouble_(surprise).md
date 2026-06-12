---
title: "Dlink DWA-642 and wireless trouble (surprise)"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by littleman54321 on 2007-01-29
Yet another linux newb with some wireless troubles. I've read around some different threads and tried to figure it out on my own, but I just don't know enough about what I'm doing...and I think I know enough to be dangerous, which is never a good thing ;)  Also, the card is not showing up in the Network Settings, but is showing up in the Device Manager.

If it makes any difference: I tried repeatedly and couldn't get 6.10 to install on my laptop. The livecd worked fine, but it would always freeze at the splash loadup screen after a few pixels of the progress bar loaded. So I tired a 6.06 version, it installed beautifully, and from there I tried the alternate CD upgrade mentioned in the sticky. After the install, it did the same thing as before. So I tried one last time to just click the "Upgrade" button mentioned in the sticky (I was wary doing this because when I clicked the update button, I noticed a lot of packages randomly stopped downloading and I had to restart them).  It never would finish doing the "upgrade", so I said screw it, and am using 6.06 still.

The card is a D-Link DWA-642

Here is the lspci printout:

```
matt@matt-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV41 [Quadro FX Go1400] (rev a2)
0000:0a:00.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:0a:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:0a:02.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:0a:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:0b:00.0 Network controller: Atheros Communications, Inc.: Unknown device 0023 (rev 01)

```

and here is the iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.



```

I remember reading somewhere in another thread that I can't find now that the fact it has Atheros Communications for the controller means I should be able to get it work with an Atheros driver...or something to that effect? If you need to know any more info about my system just tell me what commands to run.

---

### Post by littleman54321 on 2007-01-30
shameless bump :)

---

### Post by fuligin on 2007-01-30
I dont know if this will be really helpful since im a newbie myself,  but i have an Atheros Communications Inc wirless card, and I was able to get it work by installing the madwifi debian stuff.

I got it to work by a comination of installing this package from madwifi

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=madwifi-tools&searchon=names&subword=1&version=testing&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=madwifi-tools&searchon=names&subword=1&version=testing&release=all)

( I think this is included in your installation source)


Then I ran this code because i couldnt connect to my secured wireless 

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

This prompted a new network panel, which i think isnt associated to the one from before that were installed.

Either way my wifi works now so why not give it a shot. BTW, the signal meter shows alot lower connectivity then when runing the same wifi device in suse or xp.  so i still need to work at this.

Hope it helps, if not im very new to this so dont complain :)

---

### Post by littleman54321 on 2007-01-30
Thanks man I appreciate it. I'll look at it when I get some time later. Damn tests require studying...don't these prof's know that's interferring with my tinkering time?!

---

### Post by littleman54321 on 2007-01-31
Ok, update (and bump).  I tired the madwifi thing. Either I'm retarded, or it was late, or some combination therein, but I couldn't get it working. I noticed though, that it said something blah blah about Edgy having it more or less built in. So, I decided to see if I could do the upgrade from the upgrade manager. It downloaded everything, installed, etc, and to my disbelief, it actually worked.

So, I clicked System, and saw a new little tag in the menu, "Windows Wireless Drivers."  So, I think to myself, "hmmm. that sounds like I should get the d-link driver to my card." So, I do just that, and when I click the add driver, navigate to the .inf file, and add the driver, back on the main menu in the "Currently installed Windows Drivers" field, it says:

net5416: Hardware Present, yes

So I think, yay, something's going right. I click the Configure Network button, and there's no wireless device listed. Also, the lights on the card itself aren't blinking. So i guess my question is, do I need to maybe get the Atheros drivers, considering my lspci printout says it's an Atheros chipset...and if that's the case, how do I know which ones to get?

Thanks in advance for the help :)

---

### Post by littleman54321 on 2007-01-31
So I decided to do some tinkering today, and was looking thru threads, and saw some stuff and ndiswrapper. I figured, why not.

So far:
The computer recognizes the card is there, and the little light is blinking. Woo!
```

matt@matt-laptop:~$ ndiswrapper -l
net5416 : driver installed
        device (168C:0023:1186:3A6A) present
        device (168C:0023) present

```
Though I have no idea why it seems to be in there twice?

System -> Administration -> Netorwking DOES show a Wireless Connection.
matt@matt-laptop:~$ iwlist wlan0 scan works =D

iwconfig now gives me:
```

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Matt"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Now, if you paid attention to any of that, you'll notice that I hit it twice, and that it gave me 2 different outputs. I entered it in qiuckly back to back, (I've done it like 10-15 times) and sometimes it associates with the "Matt" ESSID, and sometimes it does not. It seems to be very random.....

 dmesg | grep ndiswrapper gives me this:
```

matt@matt-laptop:~$ dmesg | grep ndiswrapper
[17179601.280000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.308000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.308000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.328000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.328000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.328000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.356000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.356000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.356000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.436000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.440000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.440000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.460000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.460000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.460000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179601.484000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179601.484000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179601.484000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17181647.784000] ndiswrapper version 1.35 loaded (preempt=no,smp=no)
[17181647.856000] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[17181647.856000] ndiswrapper (NdisMAllocateMapRegisters:908): Windows driver net5416 requesting too many (256) map registers
[17181648.312000] ndiswrapper: using IRQ 177
[17181648.844000] usbcore: registered new driver ndiswrapper

```
...which doesn't look anything like the....
```

  ndiswrapper version 0.11 loaded (preempt=no,smp=no)
  ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 10 (level, low) -> IRQ 10
  ndiswrapper: using irq 10
  wlan0: ndiswrapper ethernet device 00:c0:49:d7:b6:e4 using driver netwg311.sys
  ndiswrapper device wlan0 supports  WPA with TKIP cipher
  ndiswrapper: driver netwg311.sys (NETGEAR, Inc.,04/04/2004,6.0.2.23) added
```
...I'm apparently supposed to be seeing.... I'm not even sure what the errors I got are telling me, to be perfectly honest.

dhclient wlan0 gives me:
```

matt@matt-laptop:/etc/network$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 11012
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
matt@matt-laptop:/etc/network$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 11012
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:9a:2e:1d:04
Sending on   LPF/wlan0/00:17:9a:2e:1d:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Anyone have any ideas? What is all this telling me?

---

### Post by littleman54321 on 2007-02-01
Last update because I finally got it working =D

I uninstalled tall the drivers, and then reinstalled, got rid of that weird duplicate thing. I was searching thru the forums for something similar to my problem, when I came across this thread.
[http://ubuntuforums.org/showthread.php?t=348608](http://ubuntuforums.org/showthread.php?t=348608)

Post #5 there is a command....and someone else mentioned turning off the wireless security, so I did that. I ran the command, and it just started working. I haven't tried messing with the security settings yet, but I'm just happy it's working now =D

And yes, this post is being made from that wireless connection mwuhahhahaa :guitar: 

I hope this thread helps anyone else having a similar circumstance.

---

### Post by wootah on 2007-02-01
Hey,

This thread might be slightly old, but I did notice something with the dhclient command you ran. If you would have used sudo, it would have attempted to renew your ip.

If you are trying to connect to an AP with WPA, you might want to look into wpa_password and wpa_supplicant (along with adding a wpa_supplicant.conf in /etc/).

Hopefully that might help you or anyone else!

Good luck!
~Jaymes

---

