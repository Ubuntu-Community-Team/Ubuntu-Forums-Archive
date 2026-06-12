---
title: "Can connect to router but not to web with static IP. Cannot get IP with DHCP"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by buntu_hugenewbie11 on 2014-02-05
When I try and access the router (wpa2 security, dhcp) I never get an ip address.
So I tried creating a fixed ip address and then I could connect to the router and I can ping other machines on the network though other machines cannot ping me.
If I try to ping an ip address (such as google dns) 8.8.8.8 I get nothing. So it is not just a dns issue.
Now if I clone the mac address and try dhcp I still cannot connect and do not get an ip address on the router. 
So for some reason with a fixed ip address I can get as far as the internal network, but noody can get to me and I cannot get out to the web.
My goal is just to e able to use the web so I don't care if it is a fixed ip or dhcp for this machine. But from what I've seen, it may be a bcm driver issue.
Thus far I have done a full factory reset of the router, and have purged bcml-kernel-source. I am still at the same point.

So my only access point is a wifi (Tenda) router that uses dhcp for ip allocation.
I am using Kubuntu 12.04.4 64 bit on a Dell Latitude E6510. I know it is not a hardware issue because I can connect to the router when I use Windows 7 (this is a dual boot machine).
I cannot post output because I have no access to the internet with the machine
The wireless card is BCM4313 according to lspci.
lsusb  shows BCM5880 Secure applications processor
Currently using brcmsmac driver (version: 3.2.0-37 generic)

When I restart networking  I get that it is deprecated it may not enable again some interfaces.

Please help.

---

### Post by tfrue on 2014-02-06
Have you tried configuring the IP from the routers interface and possibly assign an static IP add to the mac address of the computer?

---

### Post by buntu_hugenewbie11 on 2014-02-06
Yes.
That's actually the only way I can connect to the router.
Though a strange thing is that it never picks up my computer's name which is blank. But I assume that would not be a needed value.

---

### Post by tfrue on 2014-02-06
Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by varunendra on 2014-02-07
@buntu_hugenewbie11,

May help to take a look at the overall setup. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by buntu_hugenewbie11 on 2014-02-07
So I have no idea why this worked.
I had the router set-up for static IP for this machine in dhcp settings.
I then have kde settings set for DHCP automatic. That didn't work but then I used the clone address in the kde settings to create a clone.
The router still picks up the old address and somehow I can now get to the internet.

I wouldn't consider it solved because it is a strange way to make it work.
And I still have not figured out what went wrong.

---

### Post by buntu_hugenewbie11 on 2014-02-07
Here is what you asked for that I could not include before:
# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tenda_3D4B88"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C8:3A:35:3D:4B:88   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:82  Invalid misc:11929   Missed beacon:0

eth0      no wireless extensions.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 005: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 001 Device 004: ID 05ca:1814 Ricoh Co., Ltd HD Webcam

# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 002 Device 004: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 005: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 001 Device 004: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
root@myob11:/etc/wpa_supplicant# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [NVS 3100M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
04:00.0 CardBus bridge: Ricoh Co Ltd CardBus bridge (rev 02)
04:00.1 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 03)
04:00.4 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Tenda_3D4B88] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:      xx:xx:xx:xx (removed by author)

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MOTOROLA-C925C:  Infra, 90:B1:34:59:41:C6, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA
    Wave Coast Suite 7: Infra, 00:26:BB:75:7D:E3, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    SilyCar:         Infra, 00:1D:73:B1:C1:50, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    suite8:          Infra, 30:46:9A:47:24:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    *Tenda_3D4B88:   Infra, C8:3A:35:3D:4B:88, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA2

  IPv4 Settings:
    Address:         192.168.0.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    Address:         192.168.0.150
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1

    DNS:             192.168.3.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no


  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by varunendra on 2014-02-09
Please use 'Code' tags for posting outputs as I asked in my previous post. There is a very good reason for the existence of that feature.

> **buntu_hugenewbie11 said:**
> So I have no idea why this worked.
I had the router set-up for static IP for this machine in dhcp settings.
I then have kde settings set for DHCP automatic. That didn't work but then I used the clone address in the kde settings to create a clone.
The router still picks up the old address and somehow I can now get to the internet.

I wouldn't consider it solved because it is a strange way to make it work.
And I still have not figured out what went wrong.
By your description so far, the router settings look more suspicious to me than anything within the computer. And the outputs you posted is obviously not the report generated by the script as I originally asked. Except for a lot of "Invalid misc" in the output of "iwconfig", I have nothing to work on. Please post the report I asked for, it'll give us a wider picture of your setup to help us make better guess/decisions.

As of now, the only thing I can suggest to completely disable DHCP (even if just for a test) in the router and assign manual IP to a couple of your computers to see if they can communicate with each other that way. Obviously, also disable any custom firewall or NAT/routing rules you might have set on the router. Almost all the routers have this feature where you can simply export their current settings to a file, then import them again when and if needed.

---

