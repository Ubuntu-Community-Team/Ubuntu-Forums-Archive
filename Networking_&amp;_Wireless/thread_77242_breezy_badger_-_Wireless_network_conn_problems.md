---
title: "breezy badger - Wireless network conn problems"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by dayal_78 on 2005-10-16
hello,
Environment:
Dell Inspiron 6000
Ubuntu 5.10, dual boot with WinXP
Kernel - 2.6.12

I installed breezy badger on my dell laptop and I am having probs with my wireless connection.
Every time I boot I have to Deactivate and Activate my wireless network interface (eth1) for the wireless network to connect. Sometimes even when I do this, I am not being able to connect. So I reboot and do the process of deactivating and activating all over again. 

My /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

iface eth1 inet dhcp
#name Wireless LAN card
#wireless_mode managed
wireless-essid cool network
wireless-key s:mykey
#wireless_channel 6
auto eth1

Can someone please help me solve this??

Also on a related note -  whenever I boot the boot process hangs on:
configuring network interfaces
for a long time and then continues to boot.

Thanks
Dayal

---

### Post by dbott67 on 2005-10-16
I had similar issues back in Warty with my D-Link DWL-650+ card.  Basically, I had to do the following:

1. Remove network module
```
sudo rmmod acx_pci
```
2. Re-install network module
```
sudo modprobe acx_pci
```
3. Restart network services
```
sudo /etc/init.d/networking restart
```

Keep in mind that my NIC uses the module acx_pci, where as Dell typically uses Broadcom (which requires ndiswrapper, if I'm not mistaken), so you'll need to replace the acx_pci with your own NIC module.

Basically, I just wrote a script called network.sh and included the above commands:
```
#!/bin/bash
rmmod acx_pci
modprobe acx_pci
/etc/init.d/networking restart
```
Next make it executable and then run as root.
 
You could just try the last line (**sudo /etc/init.d/networking restart**) to see if it helps; if not, try the whole script.

While it's not a fix, it is a faster workaround than doing it manually.

-Dave

---

### Post by dayal_78 on 2005-10-16
Hi Dave,
Thanks for your feedback. But I am using a wireless conn and here is my lspci

dayal@Dayal-UbuntuTop:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)

So I guess I am using the Network controller on the last line above for my wireless connection. I am a newbie so I may be totally wrong. 

Dayal

---

### Post by dayal_78 on 2005-10-16
As an addition, here is my lsmod:

Module                  Size  Used by
ipv6                  217408  6 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
speedstep_centrino      7380  1 
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  2 
i915                   17920  1 
drm                    58004  2 i915
video                  16004  0 
tc1100_wmi              6916  0 
sony_acpi               5516  0 
pcc_acpi               11392  0 
hotkey                  9508  0 
dev_acpi               11396  0 
i2c_acpi_ec             5760  0 
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0 
battery                 9604  0 
container               4608  0 
ac                      4996  0 
af_packet              20232  2 
sg                     33696  0 
sr_mod                 15652  0 
cdrom                  33952  1 sr_mod
pcspkr                  3652  0 
rtc                    11832  0 
hci_usb                13192  2 
bluetooth              43012  7 rfcomm,l2cap,hci_usb
ipw2200                92680  0 
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ohci1394               30644  0 
yenta_socket           22540  1 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0 
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  1 
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
intel_agp              21276  1 
agpgart                32328  3 drm,intel_agp
ntfs                   92016  1 
nls_iso8859_1           4224  3 
nls_cp437               5888  4 
vfat                   12288  3 
fat                    46492  1 vfat
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  1 
sbp2                   21128  0 
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  0 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  2 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0 
b44                    19204  0 
mii                     5248  1 b44
ehci_hcd               29448  0 
uhci_hcd               28048  0 
usbcore               104188  4 hci_usb,ehci_hcd,uhci_hcd
sd_mod                 17424  8 
ide_generic             1664  0 
ide_core              125268  1 ide_generic
ata_piix                9476  14 
ahci                   11268  0 
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sg,sr_mod,sbp2,sd_mod,ahci,libata
unix                   24624  682 
vesafb                  8088  0 
capability              5000  0 
commoncap               6784  1 capability
vga16fb                12232  1 
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

Please advise.

Thanks
Dayal

---

### Post by dbott67 on 2005-10-16
I think your wireless module is ipw2200.  Try this script:
```
#!/bin/bash
rmmod ipw2200
modprobe ipw2200
/etc/init.d/networking restart
```

-Dave

---

### Post by dayal_78 on 2005-10-16
Hi,
Cant I just type those commands manually on a terminal?
dayal

---

### Post by dayal_78 on 2005-10-16
Also is this is a one time thing..
Meaning do I need set the above as part of my boot process?
thanks

---

### Post by dayal_78 on 2005-10-16
Hi,
I manually did 
modprobe -r ipw200
modprobe ipw2200
But the problem still persists.
I still dont understand why my wifi doesnt work automatically after rebooting unless I manually deactivate and then activate my wireless network interface.
thanks
Dayal

---

### Post by dayal_78 on 2005-10-16
Hi,
I manually did 
modprobe -r ipw200
modprobe ipw2200
But the problem still persists.
I still dont understand why my wifi doesnt work automatically after rebooting unless I manually deactivate and then activate my wireless network interface.
thanks
Dayal

---

### Post by dbott67 on 2005-10-16
[QUOTE=dayal_78]Hi,
Cant I just type those commands manually on a terminal?
dayal[/QUOTE]

Yes, however, by putting them in a script you can run all 3 commands (or as many commands as you want) by simply executing one file.  It just makes it easier if you have to regularly run the commands.

-Dave

---

### Post by dbott67 on 2005-10-16
[QUOTE=dayal_78]Also is this is a one time thing..
Meaning do I need set the above as part of my boot process?
thanks[/QUOTE]

It's probably not a one-time thing.  When I was having problems with my wifi in Warty, I had to run that script every couple of days and it was generally after logging in and using the internet for a few hours.  So, in my case, the script was only run when required (on demand), rather than on bootup.

-Dave

---

### Post by dbott67 on 2005-10-16
[QUOTE=dayal_78]Hi,
I manually did 
modprobe -r ipw200
modprobe ipw2200
But the problem still persists.
I still dont understand why my wifi doesnt work automatically after rebooting unless I manually deactivate and then activate my wireless network interface.
thanks
Dayal[/QUOTE]

Does your wifi work after running this command:
```
sudo /etc/init.d/networking restart
```

-Dave

---

### Post by dbott67 on 2005-10-16
Could you please post the output of the following commands:
```
ifconfig -a
``` ```
iwconfig
``` ```
iwlist eth1 scanning
``` 
(your wifi card is *eth1*, right?)

You can also try  these 3 commands that will allow you to bring down, bring up & obtain an IP address from the command line:
```
sudo ifdown eth1
sudo ifup eth1
sudo dhclient eth1
``` 
-Dave

---

### Post by dayal_78 on 2005-10-16
Hi,
No, my wifi doesnt work if I run 
/etc/init.d/networking restart

Please find under the output for ifconfig before and after deactivating-activating my wireless interface
Before deactivating-activating (no wifi)
-----------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:14:22:DA:83:AA  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:36:B3:D1  
          inet6 addr: fe80::213:ceff:fe36:b3d1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:133171 (130.0 KiB)  TX bytes:133171 (130.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

After deactivating-activating (wifi up and running)
-------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:14:22:DA:83:AA  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:36:B3:D1  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe36:b3d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32314 (31.5 KiB)  TX bytes:10864 (10.6 KiB)
          Interrupt:17 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2701 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:245001 (239.2 KiB)  TX bytes:245001 (239.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig
---------
dayal@Dayal-UbuntuTop:~/temp$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"kawaii"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:52:5C:C0
          Bit Rate=2 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/100  Signal level=-72 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:11

sit0      no wireless extensions.


SURPRISINGLY IN THE ABOVE essid is displayed as kawaii, my essid is not kawaii !!!

Any ideas??

Thanks
Dayal

---

### Post by dayal_78 on 2005-10-16
Also,
during booting..
why does it take forever for the step - "configuring network interfaces" to complete
why does it take forever to activate my wireless interface when I deactivate it and try to activate it again from the gui.
thanks
Dayal

---

### Post by dayal_78 on 2005-10-16
hi,
I logged into recovery mode and did:
chattr -i /etc/resolv.conf
and then logged back onto regular mode.
but still ubuntu is hanging on configuring-interfaces
you can take a look at my other thread:
hi,
I logged into recovery mode and did:
chattr -i /etc/resolv.conf
and then logged back onto regular mode.
but still ubuntu is hanging on configuring-interfaces
you can take a look at my other thread:
[http://ubuntuforums.org/showthread.php?t=77242&page=2](http://ubuntuforums.org/showthread.php?t=77242&page=2)
for any pointers towards this problem.

thanks
Dayal

---

### Post by dayal_78 on 2005-10-16
dbott67,
Please ignore the above post. It was wrongly pasted.
One really wierd thing I observed just now:
how come my ip address is: 192.68.0.11 !!!!
My DHCP server (D-Link Router) is configured to assign Dynamic IP's in the range
192.168.0.100/199
So my wireless is not connecting to my router ?????
Please advise
-Dayal

---

### Post by dbott67 on 2005-10-16
[QUOTE=dayal_78]...One really wierd thing I observed just now:
how come my ip address is: 192.68.0.11 !!!!
My DHCP server (D-Link Router) is configured to assign Dynamic IP's in the range
192.168.0.100/199
-Dayal[/QUOTE]

It appears as though someone else has a wireless access point in your vicinity (named 'kawaii') and for some reason your wifi card keeps connecting to it.

If you run the command:
```
iwlist eth1 scanning
```
you should see both your AP as well as 'kawaii' (and perhaps a few others).  A few posts back I incorrectly told you to use the wrong command.

The next step is to get your wifi card to connect to your ESSID, not 'kawaii'.  From the comand line type:
```
iwconfig eth1 essid "Your ESSID"
```

If this works, then the next step is to "force" your computer to connect to your preferred AP, not 'kawaii'.  It may require starting another thread with just this question.

-Dave

---

### Post by dayal_78 on 2005-10-17
Hi Dave,
iwlist eth1 scanning gave me a bunch of Access points and yes kawaii was one of them. In the mean time I changed the ESSID on my router and now I cant connect at all. I am able to connect alright from my windows partition, but the linux side is not working.
if I do:
sudo dhclient eth1
the output is:
DHCP discover on eth1 to 255.255.255.255 port 67....
and the above keeps on going forever.
Please help
-Dayal

---

### Post by dayal_78 on 2005-10-17
It finally ended by saying
No working leases in persistent database .....
the boggling thing is I am able to access wifi alright from my win partition and not from ubuntu..
any ideas?
Dayal

---

### Post by Manny C on 2005-10-17
[quote=dayal_78]hello,
Environment:
I installed breezy badger on my dell laptop and I am having probs with my wireless connection.
Every time I boot I have to Deactivate and Activate my wireless network interface (eth1) for the wireless network to connect. Sometimes even when I do this, I am not being able to connect. So I reboot and do the process of deactivating and activating all over again. 
[/quote] 

Do you need to Deactivate and then reactivate because your computer is auto connecting to another network? Not sure I can help much here. Not an expert. My wireless worked out of the box.

[quote=dayal_78]
Also on a related note -  whenever I boot the boot process hangs on:
configuring network interfaces
for a long time and then continues to boot.
[/quote]

Hit Ctrl+c when this line comes up. It kills the process.

---

### Post by ming0 on 2005-10-17
I think you might have luck with this solution: [http://ubuntuforums.org/showthread.php?t=75612](http://ubuntuforums.org/showthread.php?t=75612)

---

### Post by malaprohibita on 2005-10-28
I am having the same two problems.  What's really odd is that I can see the wireless network, but I cannot connect unless I turn encryption off.  This kind of defeats the purpose of encryption, doesn't it?

I'm also having the "configuring network interfaces" hang that lasts at least 30 seconds (feels longer).  If I could work these two problems out, I would be home free.

---

