---
title: "Dell Mini 9 Wireless Network problems"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Shadefly on 2009-05-10
Ok I got this thing working once on my wireless network with WEP. Then we took it to a relatives house for the weekend. I got it connected to their wireless network (with no security)by setting up a new wireless connection. Now when I try to connect to my network (no changes made from when it was working) it come back and asks for correct authentication credentials. I toggle the wireless off and on per some other posts without success. I also disabled and re-enabled the broadcom driver.

I've spent hours looking at this forum and others, nothing seems to work. I tried what I did last time to get it to work. No go.
This is extrmely frustrating. When I edit network connections from Network manager, nothing has changed that I can tell. I do  not broadcast my network SSID, use WEP (I have some old systems there arent WPA driver for), and MAC filtering. The router is a Netgear WGR614 (b/g). I am using the WEP40-/128Bit key on the Ubuntu connection and 64 bit on the router (it worked before). I am using WEP index key 1 and both Ubuntu and the router have the exactly same key. The router is set to channel 11 and authentication is set to open system. I know it isn't totally secure but its more than the neighbors have and my theory is hackers go after the easiest prey.

On top of this, I am an ubuntu idiot. I have a little RH experience but Ubuntu has me baffled. I will follow directions to the T to get this fixed. Thanks in advance for any help.:(:confused:

---

### Post by superprash2003 on 2009-05-10
which version of ubuntu are you using? have you looked into system->pref->network configuration.. under WIRELESS

---

### Post by Shadefly on 2009-05-10
I am running version 8.04.1 Hardy. 

I went to your tutorials and tried to manually configure the wireless card but got errors for the sudo commands.

Command I typed:
sudo iwconfig eth1 ap 11:11:11:11:11:11 (where the 1's are the AP address from the scan. My network came up as cell 08 out of 10)
Error returned:
Error for wireless request "Set AP Address" (8B14) :
    SET failed on Device eth1 ; invalid arguement

and
sudo iwconfig eth1 key s: xxxxxxxxxx (where x'x are the WEP key and no space. removed space so the mad face would not appear in the message)
Error returned:
Error for Wireless Request "Set Encode" (8B2A)
    Set faile on device eth1: invalid argument

also, the network manager is in System, Admin, Network Manager, then I selected "edit networks" to get to the wireless tab. It see the AP just wont connect to it

---

### Post by coffeeaddict22 on 2009-05-10
open a terminal, type in ```
nm-tool
``` and if you need further help, post the output back ( It gives most of the info your wireless is using in text, so you can post it easily if you need to...)

---

### Post by Shadefly on 2009-05-10
In desperation, I used update manager to update Ubuntu. I it updated about 22 programs(?) and boots much faster now but still no connection and becuase there is no HW address it does not see any access points now.

nm-tool response (wireless only since the wired connection works)

Device       eth1
Type         802.11 WIFI
Driver       wl (I am sure I had the Broadcom driver loaded, may be the command lines I tried last night put this back to wl)
State        Unamanged
Default      No
HW address   00:00:00:00:00:00

Capabilities
Supported    Yes

Wireless Settings
  WEP encryption   Yes
  WPA encryption   Yes
WPA2 encryption    yes

Wireless access points
(nothing under here)

---

### Post by Shadefly on 2009-05-10
When I go to system/administration/hardware drivers it still shows the Broadcom STA driver is loaded.

---

### Post by jwaclawsky on 2009-05-10
I have a Dell Insperion 9 with Ubuntu 8.04 and my wireless IS WORKING FINE. I am using it right now! ...as I am typing this message. I did an nm-tool and my output is: 

- Device: eth1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        00:23:08:69:47:5A

  Capabilities:
    Supported:       yes
    Speed:           54 Mb/s

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points(* = Current AP)
    smashingcherries:Infra, 00:16:B6:1B:30:DB, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA
    *JJJMNET:        Infra, 00:14:A5:30:1A:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WEP
    super:           Infra, 00:17:F2:E2:CD:6B, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WEP
    2WIRE397:        Infra, 00:1E:C7:ED:4A:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    wrigley:         Infra, 00:1C:DF:D8:DD:B7, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    2WIRE421:        Infra, 00:24:56:E0:BF:F9, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA
    rdw:             Infra, 00:1C:10:A4:E5:37, Freq 2462 MHz, Rate 0 Mb/s, Strength 20 WPA
    2WIREGINA :      Infra, 00:14:95:15:C4:11, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WEP

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             68.87.72.130
    DNS:             68.87.77.130
    DNS:             68.87.66.196

Maybe this information will help you

---

### Post by coffeeaddict22 on 2009-05-10
Hi, 
Looks like network manager can't see your card.  What does ```
iwconfig
``` report back?

---

### Post by Shadefly on 2009-05-10
iwconfig gives the following:

lo   no wireless extensions

eth0 no wireless extensions

sms no wireless extensions

eth1  IEEE 802.11 Nickname:""
     Access point : Not - Assocaited
     Link Quality: 5 Signal level:0 Noise Level:0
     Rx Invalid nwid:0 Invalid crypt:0 invalid misc:0

And to answer the above post, it was working fine until we added a second wireless network configuration. Now when it sees the router it wont connect. After updating Ubuntu with update manager it does not see any wireless network.

---

### Post by Shadefly on 2009-05-10
I went to the syslog and found there is a problem with the driver for the broadcom wireless nic. I do not know what these errors mean at thispoint but maybe someone has some advice on how to fix the issue. even though network manager says the wireless card is using IPV4, it looks like it assigned and IPV6 address? please see the syslog below that starts with the initial load of wl from what I can tell:

May 10 18:53:21 neal kernel: [   40.064104] wl: module license 'MIXED/Proprietary' taints kernel.
May 10 18:53:21 neal kernel: [   40.131671] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
May 10 18:53:21 neal kernel: [   40.194675] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
May 10 18:53:21 neal pulseaudio[4842]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/platform_parport_pc_632
May 10 18:53:21 neal nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_23_08_71_3d_4a, iface: eth1)
May 10 18:53:21 neal nm-system-settings:    Ifupdown: get unmanaged devices count: 1
May 10 18:53:21 neal nm-system-settings:    SCPluginIfupdown: locking wireless connection setting
May 10 18:53:21 neal NetworkManager: <info>  eth1: driver is 'wl'. 
May 10 18:53:21 neal NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
May 10 18:53:21 neal NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
May 10 18:53:21 neal NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_08_71_3d_4a 
May 10 18:53:21 neal NetworkManager: <info>  (eth1): now unmanaged 
May 10 18:53:23 neal avahi-daemon[4462]: Registering new address record for fe80::223:8ff:fe71:3d4a on eth1.*.
May 10 18:57:31 neal ntpd[5027]: synchronized to 91.189.94.4, stratum 2
May 10 18:57:31 neal ntpd[5027]: kernel time sync status change 0001
May 10 18:58:15 neal ntpd[5027]: Listening on interface #6 eth1, fe80::223:8ff:fe71:3d4a#123 Enabled

---

### Post by coffeeaddict22 on 2009-05-11
That syslog looks OK.  There's a bit of a dummy spit about pulseaudio, but the network manager mostly behaves.  Just to confirm, what does ```
lshw -C network
``` show?

Assuming you're running Ubuntu 8.10 or 9.04, the network manager is the 4 bars up on the panel.  When you right click, networking and wireless are enabled?  If you choose Edit connections, what options do you have under wireless?

---

### Post by Shadefly on 2009-05-16
out of town on business this week so not able to work on it until today. 
When I type the command you list above 

lshw -C network

it returns

bash: lshw: command not found

I am running Hardy, 8.04.1

---

### Post by Shadefly on 2009-05-16
When I right click on the bars, I can only edit connections to see them. Until the last update, I used ot be able to see the network connections and be able to select one. 

When Iedit connetions, a window with 5 tabs comes up: Wired, Wireless, Mobile Broadband, VPN and DSL.

When I go to Wireless and click on my network name, then click Edit, it asks me if I want to allow application access to keyring. I click Always Allow, the popup comes up again, I click Always Allow again and I can edit the connection.

Connect autmatically is checked, the SSID is correct, it is set for infrastructure mode, BSSID and MAC Address are blank and MTU is set to Automatic

On the Wireless Security tab:
Set to WEP 40/128 bit key
Key is entered correctly
WEP index is set to 1 to match the router
Authenitcation is Open (same as router)

IPV4 settings tab
Method set to DHCP
DNS server and search domains are blank
DCHP CLient ID set to Mini

---

### Post by yeats on 2009-05-16
> **Shadefly said:**
> out of town on business this week so not able to work on it until today. 
When I type the command you list above 

lshw -C network

it returns

bash: lshw: command not found

I am running Hardy, 8.04.1

Are you running the preinstalled Dell version of Ubuntu?  I noticed on mine that some programs I'm used to using are not installed in that version (I've since moved to Ubuntu Netbook Remix on Intrepid).  There is a great site with a lot of info here: [http://www.ubuntumini.com/](http://www.ubuntumini.com/) .  I haven't seen if your issue is covered there, though...

---

### Post by coffeeaddict22 on 2009-05-16
From what you've said, something else is grabbing the wireless interface.  wl is the Broadcom driver; the problem is in your config with the second network if I had to guess.  try ```
ifconfig down
ifconfig up
```
to see if that does it; otherwise, you probably should delete the other connection next.
lshw is a really nice little tool; it lists all the hardware available, and is part of a normal Ubuntu install, so I'm a little surprised it isn't there.  Check it's installed: one way is System/Administration/Synaptic Package Manager: type lshw in the search bar, and it'll come up.  If it's not installed, install it.

---

### Post by Shadefly on 2009-05-16
Chrissharp123 - yes this is the pre-installed version that came with the mini. I have used update manager to get updates (over 100 of them)

When I type ifconfig down, it returns 

Down: error fetching interface information: device not found

???

I did have to load lshw and once I did, the out put is below

 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:71:3d:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:96:25:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.10 latency=0 module=r8169 multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: sms
       serial: 00:53:49:41:4e:4f
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
neal@neal:~$

---

### Post by yeats on 2009-05-16
> Chrissharp123 - yes this is the pre-installed version that came with the mini. I have used update manager to get updates (over 100 of them)

That's exactly what you should do.  One thing to note is that the Dell version has Dell-specific software repositories and is NOT drawing from the "regular" Ubuntu ones.  So some of the advice/instructions/etc. that applies to the default version of 8.04 may not apply exactly to the Dell version.

As an example, when you typed "lshw -C", you got the message "command not found".  In "default" Ubuntu, it would have said something like "The program 'lshw' is not installed.  You can installing by doing 'sudo apt-get install lshw'"  

Since I'm so used to the way Ubuntu normally works, I had replaced the Dell version within 48 hours of getting my Dell mini :-).  I'm not necessarily advising you do the same, but it might be something to consider (and may even solve your issues here).

Anyway - I'll shut up and let coffeeaddict22 work with you ;-)

---

### Post by Shadefly on 2009-05-16
All I want is to have a working Mini. If I have to reload with a real OS instead of the Dell-ized version (we do that a lot, I work for Dell on the corporate side with servers and storage), I'll do it. BTW, we no longer sell any of the Mini's with Ubuntu. Too much of a hit on the blogosphere for not supporting it through our normal support is my guess.

---

### Post by yeats on 2009-05-16
> All I want is to have a working Mini. If I have to reload with a real OS instead of the Dell-ized version (we do that a lot, I work for Dell on the corporate side with servers and storage), I'll do it. BTW, we no longer sell any of the Mini's with Ubuntu. Too much of a hit on the blogosphere for not supporting it through our normal support is my guess.

Hmm.  I just ordered mine at the end of April - it's a Vostro A90.

Anyway, if you want to reinstall, follow these instructions on the site I referenced before:

[http://www.ubuntumini.com/2009/03/screenshot-tour-installing-ubuntu-904.html](http://www.ubuntumini.com/2009/03/screenshot-tour-installing-ubuntu-904.html)

Ubuntu Netbook Remix is really cool and makes the Dell version look really boring and corporate IMHO. :-)  Try the live USB to see if you like it.

---

### Post by coffeeaddict22 on 2009-05-17
Yes, that's standard output for ifconfig down.  Sorry, should have mentioned that: it's an instruction to the PC to shut the network interfaces down.  You've got the right driver, so hopefully taking it down and then back up again (that's the ifconfig up) may set the problem right.
Next up, type in ```
nm-tool
``` It may give the bit of info needed.  I'm not sure you've got it installed.  It's part of the Gnome network manager applet package, so if it's not there, there's ways around it, but it's the easiest way I know of to get all the required info...

---

### Post by Shadefly on 2009-05-17
Things have gone from bad to worse. Now it wont connect via the ethernet port on the side either. I am trying to find a way to go back to factory config and start over or load 9.04 (jaunty jackalope?).  I had to type the output by hand below:

nm-tool works. Here is the output

State: Connected

Device eth0
Type: wired
Driver: R8169
State: unmanaged
Default: no
HW address: 00:00:00:00:00:00

Capabilities
Supported: yes
Carrier Detect: yes
Speed: 100 Mb/s

Wired settings

Device eth1
type: 802.11 WiFi
Driver: wl
State: unmanaged
Default: no
HW address: 00:00:00:00:00:00

Capabilities
Supported: yes

Wireless Settings
WEP Encryption: yes
WPA encryption: yes
WPA2 encryption: yes

Wireless access points

(none listed)

---

### Post by Shadefly on 2009-05-18
so I thought it might be a good idea to start from scratch again. I dug up the CD that came with the MIni and found the Ubuntu LiveUSB program was on it along with an img file. I formatted a 2GB USB and key, loaded the image and am re-imaging my Mini now. 

Once it connects via wired ethernet, I'll use update manager to get all the updates, then try to configure wireless again.

The main reason I am doing this is it srted locking up on me. not sure if that was something I did, or if there is some other problem but at least the new image will (hopefuly) eliminate the load. I dread it being a hardware problem. 

I'll post again once the image is loaded, updated and I try to configure wireless again.

Any suggestions on the wireless peice are welcome.
:popcorn:

---

### Post by Shadefly on 2009-05-18
ok, everything is reloaded and update manager only loaded about 80 different updates. Less than the fitst time around. I am guessing I had an old image when I received it.

I configured wireless and it worked the first time. Still something strange though. the icon in the status bar at the top is 2 monitors now, not the 4 bars for wireless. Even when wireless is connected (takes about a minute or so) when I hover over the icon it says "no network connection" Any idea why? Its working now, even after 5 reboots.

---

### Post by coffeeaddict22 on 2009-05-18
I'd guess nm-tool says about the same thing too.  The network manager is a bit glitchy at times, and from what you're saying it's not registering the network interfaces.  You could try either 1) reinstalling it (System/Administration/Synaptic Package Manager, search for network manager in the top bar, right click and choose reinstall) or alternatively, remove it and install wicd (find it in the same place).

---

### Post by HermanAB on 2009-05-18
You likely need to do a cold boot to get the WiFi modem to work again.  Power the machine down completely - remove the battery if necessary - then power up again.

---

### Post by duhrel on 2009-05-20
> **Shadefly said:**
> out of town on business this week so not able to work on it until today. 
When I type the command you list above 
 
lshw -C network
 
it returns
 
bash: lshw: command not found
 
I am running Hardy, 8.04.1I'm getting the same exact response. I think you and I have the same problem with our Mini's. Can anybody chime in with some help?

---

