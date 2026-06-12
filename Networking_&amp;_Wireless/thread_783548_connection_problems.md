---
title: "connection problems"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by whatiam on 2008-05-05
I have GNOME network manager or whatever its called, ndiswrapper, and wpa supplicant. My ubuntu detects my wireless card, I can see the networks, and I can try to connect to them, and I get the bars or w/e, it says 84% connected or something, but I still cant browse the internet, anyone got help?

---

### Post by superprash2003 on 2008-05-06
could your post your ifconfig output.. and also let us know if you are able to ping your router

---

### Post by Kevbert on 2008-05-06
It may be that you have interference problems.  Microwave ovens and cordless phones use the same frequencies (approx 2.4GHz).  Other wireless nearby may be using the same frequency as you, hence a large signal.
Try changing wireless channels.  If you know that you're connected open a network browser and enter something like [http://192.168.0.1](http://192.168.0.1) (it should be in your router manual, if not what's the model/make of router ?)  It will then ask for you're user ID and password (again if you can't find this it can found via the model, defaults normally are admin and password).  Next go to wireless settings and change the channel number (channels overlap, so if you use CH 01 go to say CH 06).

---

### Post by whatiam on 2008-05-06
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:30:f9:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72300 (70.6 KB)  TX bytes:72300 (70.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:bf:11:ac:4b  
          inet6 addr: fe80::212:bfff:fe11:ac4b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048 (1.0 KB)  TX bytes:1350 (1.3 KB)

cant ping router

oh btw not connected to internet on my desktop with ubuntu so i cant do that

---

### Post by superprash2003 on 2008-05-06
your wlan0 aint getting an ip , which is why you cannot connect to the internet nor access your router.. go to system->administration->network and go to wlan0 properties.. and try setting a static ip there.. if your router ip is 192.168.1.1 then set your computer ip as 192.168.1.10 (example).. accordingly...and also set gateway ip as router ip.. try this ..

---

### Post by whatiam on 2008-05-06
yes, i am trying that right now but it is still not connecting. DOes it connect automatically or do i have to do something?
Also how would i set my ip accordingly to the network ip?

---

### Post by ComputerRick on 2008-05-06
> **whatiam said:**
> 
wlan0     Link encap:Ethernet  HWaddr 00:12:bf:11:ac:4b  
          inet6 addr: fe80::212:bfff:fe11:ac4b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1048 (1.0 KB)  TX bytes:1350 (1.3 KB)


I'm not surprised that you don't have Internet access.  The number of RX & TX packets is too low.  

It seems that the wireless network has security enabled and you are not authenticating.  [Here is a great link]("http://ubuntuforums.org/showthread.php?t=684495") to work thru your wireless configuration, but it's most likely the security settings (Auth/Encrypt/Key) that you need to fix.

I would not suggest setting a static address for your wireless, it will probably only add to your problem, not fix it.

---

### Post by whatiam on 2008-05-07
i followed the instructions exactly, but when i type in
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf it says
line 8:unkown networkd field 'key mgmt'
line 12: failed to parse network block
Failed to read or parse configuration 'etc/wpa_supplicant.conf

whats the problem?

---

### Post by jtrindle on 2008-05-07
Did you include the underscore in "key_mgmt"?

key_mgmt=WPA-PSK

---

### Post by whatiam on 2008-05-07
yea i i found out i forgot the underscore, but i am still having problems.
when i type the command now, it says
c/etc/wpa_supplicant.conf
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

any clue now?

---

### Post by whatiam on 2008-05-07
help please.........

---

### Post by ComputerRick on 2008-05-08
**First,** the error you're getting may be caused by running the wpa_supplicant multiple times.  First, make sure that it's the latest version (I believe it's 0.5.10).  Try sudo apt-get wpasupplicant.

**Second,** we need to be sure that it's only running once.  So after you make an attempt at starting it, if it fails, kill it to save you some grief.

try that.  If it doesn't work again, post your wpa_supplicant.conf (hide your ssid & key)

---

### Post by whatiam on 2008-05-08
excuse me for being a complete noob, but how do i kill wpa supplicant?

---

### Post by whatiam on 2008-05-08
please help

---

### Post by whatiam on 2008-05-09
my /etc/wpa_supplicant.conf

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="my network name"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="really long hexadecimal code"
        pairwise=TKIP
        group=TKIP
}

I honestly dont know whats going on, I've been trying everything.

---

### Post by kevdog on 2008-05-09
Ok

Killing wpa_supplicant

sudo killall -q wpa_supplicant

Next - For your hex key you don't need quotes!

---

### Post by whatiam on 2008-05-09
Oh ok fixed that, now heres the response to the command
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

it says associated with 00:le:c7:el:28:fq over and over and over and over again. Anyone got any ideas what that means?

---

### Post by kevdog on 2008-05-09
Hmm, did you or can you type:

sudo dhclient wlan0

If not try this:
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

The B puts the process in the background.  If that doesn't work, post a snippet of the following:

sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

The -dd flag gives debugging messages.

---

### Post by whatiam on 2008-05-09
sorry for taking to long, my mouse freezes after 2 minutes 
this is sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:bf:11:ac:4b
Sending on   LPF/wlan0/00:12:bf:11:ac:4b
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.65
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

THis is sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd:
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=17
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again

well thats like half a page of it, dunno what you meant by a snippet, because the whole thing is like 10 pages long.
Tell me if you need more info.

---

### Post by whatiam on 2008-05-10
this is sudo dhclient -r wlan0 by the way:
listening on LPF/wlan0/00:12:bf:11:ac:4b
sending on LPF/wlan0/00:12:bf:11:ac:4b
PHCPREALEASE on wlan0 to 192.168.1.254
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

---

### Post by knarf on 2008-05-10
It is clear that your wireless card is not associating with your access point - it does not even seem to find it. What (brand, type) of card is it, and which driver are you using with ndiswrapper? Your MAC address maps to 'Arcadyan Technology Corporation' but that does not tell much about the chipset or needed driver...

Signal strength reporting with ndiswrapper is sketchy at best btw so I'd not put to much faith in those 84%.

---

### Post by whatiam on 2008-05-10
My wireless card is SMC EZ connect 2862W, and I am sure I have the right driver for it because I got it off the installation cd, and Ubuntu does recognize it, I can see all the networks and stuff from network manager. The only problem is that it will not connect to my WPA protected network.

---

### Post by knarf on 2008-05-10
Your card is based on a recent Prism chipset and as such most likely supported by the p54usb driver which comes standard with Ubuntu. This driver also supports WPA. This should be your first try I'd say. It this does not work or the speed if not satisfactory you can try another Windows driver. The mere fact that the driver came with the card and that ndiswrapper recognizes it does not mean anything.

What is the USB ID of your card (find out using lsusb)? It should look something like XXXX:XXXX (VendorId:ProductId).

Searching for your card on the ndiswrapper compatibility list shows no positive reponsed to WPA compatibility, only "WPA not tested":

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

This does not mean it does not work, but it might mean that the vendor-supplied driver in combination with ndiswrapper does not work for WPA networks. Try another driver instead, search for cards with a similar chipset (ISL3890?) which have positive responsed to WPA compatibility.

---

### Post by knarf on 2008-05-10
BTW... are you sure that ndiswrapper is the only driver loaded for your card? If p54usb and ndiswrapper are fighting for access to the card it is not going to work...

lsmod|grep p54 should tell the story...

---

### Post by whatiam on 2008-05-10
couldnt find the symbol you used after lsmod, so i just typed lsmod.
odule                  Size  Used by
af_packet              23812  0 
ipv6                  267780  8 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
powernow_k8            16704  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_stats           7104  0 
freq_table              5536  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
evdev                  13056  4 
ndiswrapper           192920  0 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
dcdbas                  9504  0 
snd_seq_dummy           4868  0 
pcspkr                  4224  0 
snd_seq_oss            35584  0 
k8temp                  6656  0 
snd_seq_midi            9376  0 
button                  9232  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_nforce2             7680  0 
agpgart                34760  0 
i2c_core               24832  1 i2c_nforce2
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 31872  0 
hid                    38784  1 usbhid
sata_nv                27528  2 
pata_acpi               8320  0 
b44                    28432  0 
ata_generic             8324  0 
ssb                    32260  1 b44
mii                     6400  1 b44
ehci_hcd               37900  0 
ohci_hcd               25348  0 
libata                159344  3 sata_nv,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
usbcore               146028  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              36872  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

and heres lsusb:
Bus 002 Device 005: ID 0930:6545 Toshiba Corp. 
Bus 002 Device 004: ID 1260:ee22  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:2105 Dell Computer Corp. 
Bus 001 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by knarf on 2008-05-10
No p54 there... not that strange as this adapter does not seem to be supported by it yet:

[http://prism54.org/punbb/viewtopic.php?id=1655](http://prism54.org/punbb/viewtopic.php?id=1655)

That report does state that it works with ndiswrapper though... It also points at a similar US Robotics device (5422).

These are the latest drivers from SMC:

[http://www.smc.com/files/AV/2862wV.2_V.3DR_UT_WW.zip](http://www.smc.com/files/AV/2862wV.2_V.3DR_UT_WW.zip)

These are the latest from US Robotics:

[http://www.usr.com/support/5422/5422-files/USR5422-v3.3.36.0.exe](http://www.usr.com/support/5422/5422-files/USR5422-v3.3.36.0.exe) (a self-extracting ZIP file, unzip it with the normal unzip command (mkdir blah && cd blah && unzip /wherever/you/downloaded/USR5422-v3.3.36.0.exe))

The US Robotics driver contains version 2.13.17.0 of the Conexant/ISL prism driver while the SMC one is older (2.13.10.0). Try US Robotics first:

 - remove the current driver (ndiswrapper -r driver)
 - unzip the driver as stated above
 - point ndiswrapper at the INF file (ndiswrapper -i RSC4USB.inf)

Does it state that the hardware is present? If so it might work. If this driver does not work try the one from SMC instead (same procedure, just point it at SMC2862E.inf instead)

---

### Post by knarf on 2008-05-10
BTW, show us the output from ```
ndiswrapper -l
``` to give some idea of what ndiswrapper sees...

---

### Post by whatiam on 2008-05-10
auto run : invalid driver
smc2862w: diver installed
device (1260:EE22) present

---

### Post by whatiam on 2008-05-10
The driver from the installation cd says hardware present, but the ones downloaded on the internet and moved to my computer with a flash drive does not work. Ndiswrapper just says invalid driver.

---

### Post by knarf on 2008-05-10
First of all remove that 'autorun' thing - did you try to add the 'autorun.inf' to ndiswrapper? That will not work...

Try ```
sudo ndiswrapper -r autorun
``` to get rid of it.

How did you try to install the drivers from the net? The right way to do it is to:

 - remove current driver for your adapter: sudo ndiswrapper -r smc2862w
 - unpack the archive files (unzip, cabextract, untar, whatever it takes)
 - change directory to where the driver (usually *.SYS) and driver information file (*.INF) lives
 - sudo ndiswrapper -i name_of_inf_file.inf

In the case of the US Robotics driver it would look like this:

```

cd
mkdir windows_driver_usr
cd windows_driver_usr
ndiswrapper -l
wget http://www.usr.com/support/5422/5422-files/USR5422-v3.3.36.0.exe
unzip USR5422-v3.3.36.0.exe
cd Driver
sudo ndiswrapper -i RSC4USB.inf
ndiswrapper -l
cd

```

You can cut and paste this whole section into a terminal if you like. I do not have your adapter (nor do I use ndiswrapper...) but when I tried this sequence the result looked like this:

> 
frank@ostrogoth:~$ cd
frank@ostrogoth:~$ mkdir windows_driver_usr
frank@ostrogoth:~$ cd windows_driver_usr
frank@ostrogoth:~/windows_driver_usr$ ndiswrapper -l    ***<<<<< NO DRIVER INSTALLED....***
frank@ostrogoth:~/windows_driver_usr$ wget [http://www.usr.com/support/5422/5422-files/USR5422-v3.3.36.0.exe](http://www.usr.com/support/5422/5422-files/USR5422-v3.3.36.0.exe)
  ***...wget guff...***
frank@ostrogoth:~/windows_driver_usr$ unzip USR5422-v3.3.36.0.exe
   ***...unzip guff...***  
frank@ostrogoth:~/windows_driver_usr$ cd Driver
frank@ostrogoth:~/windows_driver_usr/Driver$ sudo ndiswrapper -i RSC4USB.inf
installing rsc4usb ...
forcing parameter EnableRadio from 0 to 1
frank@ostrogoth:~/windows_driver_usr/Driver$ ndiswrapper -l
rsc4usb : driver installed   ***<<<<< THE DRIVER IS VALID AND INSTALLED.....***
frank@ostrogoth:~/windows_driver_usr/Driver$ cd
frank@ostrogoth:~$ 


The same for the SMC driver:

```

cd
mkdir windows_driver_smc
cd windows_driver_smc
ndiswrapper -l
wget http://www.smc.com/files/AV/2862wV.2_V.3DR_UT_WW.zip
unzip 2862wV.2_V.3DR_UT_WW.zip
cd Driver/WinXP
sudo ndiswrapper -i SMC2862W.inf
ndiswrapper -l
cd

```

Results are:

> 
frank@ostrogoth:~$ mkdir windows_driver_smc
frank@ostrogoth:~$ cd windows_driver_smc
frank@ostrogoth:~/windows_driver_smc$ ndiswrapper -l
frank@ostrogoth:~/windows_driver_smc$ wget [http://www.smc.com/files/AV/2862wV.2_V.3DR_UT_WW.zip](http://www.smc.com/files/AV/2862wV.2_V.3DR_UT_WW.zip)
   ***...wget guff...***  
frank@ostrogoth:~/windows_driver_smc$ unzip 2862wV.2_V.3DR_UT_WW.zip
   ***...unzip guff...***  
frank@ostrogoth:~/windows_driver_smc$ cd Driver/WinXP
frank@ostrogoth:~/windows_driver_smc/Driver/WinXP$ sudo ndiswrapper -i SMC2862W.inf
installing smc2862w ...
frank@ostrogoth:~/windows_driver_smc/Driver/WinXP$ ndiswrapper -l
smc2862w : driver installed
frank@ostrogoth:~/windows_driver_smc/Driver/WinXP$ cd
frank@ostrogoth:~$ 


Again, driver recognized and installed...

So either you were doing something wrong or there is something amiss with your ndiswrapper installation...

If these new drivers don't give any improvement you might as well reinstall the original from your CD.

---

### Post by whatiam on 2008-05-10
I know the driver from my cd works, because an week ago after playing around with network manager, I managed to get on the internet for like 5 minutes, until my usb mouse froze like it always does. I just cant remember how I did that, so im trying to find another solution.

---

### Post by knarf on 2008-05-10
May I suggest that this is not exactly shining evidence of a 'working driver'? May I also suggest removing that freezing USB mouse + driver from the system while testing your USB network adapter? It might well make a difference - or it might not, but why add another variable to the mix?

Try those drivers. If they don't work, no harm done. If they do, problem solved. Also reset (unplug power, wait 10 seconds, plug in power) your access point, this sometimes works wonders...

---

### Post by whatiam on 2008-05-11
Ok I have unplugged the usb mouse, and now am using mousekeys.
I tried to add the .inf file from the smc one in the windows XP folder, not that autorun thing. It said something like smc2862w.inf. Ndiswrapper says invalid driver. Also I dont have internet access on the computer with ubuntu, so I have no idea how to get the US robotics driver in my computer.

---

### Post by whatiam on 2008-05-11
bump help please

---

### Post by knarf on 2008-05-12
Just download those drivers on another machine, put them on a USB stick/CD/mp3-player/phone or anything else that can be mounted in Linux and follow the instructions I gave in the previous posting. That should give you the drivers. As to whether that will solve your problem only experience can tell - I do not have your wifi-adapter nor do I use ndiswrapper...

I assume you're using Ubuntu 7.10 (aka 'Gutsy Gibbon')?

---

### Post by whatiam on 2008-05-12
No I am using Hardy, I tried the U.S robotics one and says invalid driver like the one from SMC. The installation cd is the only one that appears to work.

---

### Post by knarf on 2008-05-12
Hmmm that's odd... On the Hardy I used for the above tests the driver was recognized and loaded without any problems. How did you install Hardy? Upgrade or from CD? Which ndiswrapper are you using? Try:
```
dpkg -l|grep ndiswrapper
```
It should show all installed packages with 'ndiswrapper' in the name.

As it is not yet clear whether your problems are caused by a faulty driver, fauly ndiswrapper, problem with network-manager, bad password or something else it might be worth seeing if you can get a connection without network-manager.
Do you think you can try to test the connection without network-manager? You'd need to handle wpa_supplicant through wpa_cli, wpagui (sudo apt-get install wpagui) or any of the other frontends.

---

### Post by whatiam on 2008-05-12
I tried getting it with network manager, thats how I got it to work those 2 times, although I dont know, whether it was luck or boot options or something else.
Btw can you tell me where that symbol after -l is on the keyboard, i am such a noob.

---

### Post by ComputerRick on 2008-05-13
> **whatiam said:**
> Btw can you tell me where that symbol after -l is on the keyboard, i am such a noob.

It is the | (often shows as two vertical dashes on a US keyboard, it's SHIFT + \)

Everyone was a noob once.

---

### Post by knarf on 2008-05-13
That **|** is called the 'pipe symbol' (or just 'pipe'). On US keyboards it is generally to be found on the same key as **\**, above the **Enter** key, produced by pressing **Shift-|**. It is used to connect the output of the program on the left hand side to the input of the program on the right hand side. Like so:

*dpkg -l* produces a list of installed/configured/partly-present/etc packages on your system. It does this by going through the package database files (in /var/lib/dpkg/) and copying the results to its 'standard output' (also known als 'stdout' in the typical abbreviated unix lingo). When you just run that single command the results are printed on the terminal-screen, -window or -paper. This is a long list (how long? *dpkg -l|wc* and you have the answer, more on that later).

Since you're only interested in packages with 'ndiswrapper' in the name you want to filter out the rest. That is what *grep* does. Here *grep* is called with a single parameter, the word you want to look for. When called with only a search expression *grep* will look for that expression in its 'standard input', also known as 'stdin' in unix-lingo. And that is where the 'pipe' symbol comes in handy. By placing it between the former and the latter command you connect the output from *dpkg -l* to the input of *grep ndiswrapper*, giving you just what you wanted... You can read piped commands sequentially, left to right: ```
*produce a list | search for something in this list ( | and do something else with the search results | and possibly something else still* )
```

And the number of packages? The output of *dpkg -l* gets connected to the input of *wc*. To see what *wc* does you can read its manual page: *man wc*

By the way, on my Hardy system the output of *dpkg -l|grep ndiswrapper* looks like this:
> 
ii  ndiswrapper-common               1.50-1ubuntu1     Common scripts required to use the utilities
ii  ndiswrapper-utils-1.9            1.50-1ubuntu1     Userspace utilities for the ndiswrapper Linu


Meaning I have version 1.50-1ubuntu1 of both packages installed (the leading 'ii' means that the package is meant to be installed (first i) and is actually installed (second i). To see a list of all installed packages use:

```
dpkg -l|less
```

*less* is a 'pager', it takes its stdin and feeds it page-wise to stdout. Use the spacebar or cursor keys to scroll the list. Its name is a pun on the *more* command which it replaces (less is more...). As usual *less* also has a manual page: *man less* to read it.

---

### Post by knarf on 2008-05-13
By the way:
> [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/194714](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/194714)
This bug report shows many others with similar problems, so it is quite possible that there is some bug crawling around here. One of the workarounds I saw mentioned is to use an older kernel, eg. from Gutsy. Do you have an older kernel (2.6.22?) installed which you can try? If not you can get one from the repositories. The easiest way is probably to (temporarily) add the gutsy repository to /etc/apt/sources.list.

---

### Post by whatiam on 2008-05-13
Thanks for all the help, I am finally on the internet again, although I have no idea how. I guess I will just try not to turn off this computer to keep the internet on. I found out that using boot options irqpoll and pci=noacpi may help, cause thats what I did this time. I will try to test it again after my computer turns off by some reason. (using mousekeys all the time is getting really annoying though)

---

### Post by whatiam on 2008-05-14
spoke too soon, at restart I cant get the internet to work.

---

### Post by Felivel on 2008-07-26
i need some help with my smc adapter, im geting...

```
smc2862w : driver installed
	device (1260:EE22) present
```

i installed the ndiswrapper from source.

ndiswrapper -v
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 
```

my wireless usb is an SMC 2862W - G

im noob in this area, please help me, i have tried almost all things.

---

### Post by Felivel on 2008-07-26
ok i have been chequing an this is my usb card

[IMG]http://www.freeweb.hu/vlsoft/smc/SMC2862W-G_EU_package.jpg[/IMG]
[IMG]http://www.freeweb.hu/vlsoft/smc/SMC2862W-G_EU_front_lo.jpg[/IMG]
[IMG]http://www.freeweb.hu/vlsoft/smc/SMC2862W-G_EU_back_lo.jpg[/IMG]

and im using ubuntu 8.04 amd 64

still showing the same error.
```
smc2862w : driver installed
	device (1260:EE22) present
```

---

