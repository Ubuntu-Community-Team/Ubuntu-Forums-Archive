---
title: "wireless problems Ubuntu 10.10"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by Gluebuntu on 2010-11-05
I am using Ubuntu 10.10, and I can't seem to connect to my home wireless network. I click the wireless icon and select my home network from the list (it doesn't broadcast it's SSID) and Ubuntu starts trying to connect but then it just tells me that the Network connection is disabled and I am offline.:confused: I am using a netbook EEE PC and Ubuntu is in a dual-boot with Windows 7 (which was originally the only OS on it.) Wireless worked fine before I upgraded from 10.04 to 10.10

I know this probably isn't enough, are there any commands I can use to get more information?

I am a beginner "absolute beginner" so please provide me with detail when answering my question. Thanks.

---

### Post by bioterror on 2010-11-05
> **Gluebuntu said:**
> I am using Ubuntu 10.10, and I can't seem to connect to my home wireless network. I click the wireless icon and select my home network from the list (it doesn't broadcast it's SSID) and Ubuntu starts trying to connect but then it just tells me that the Network connection is disabled and I am offline.:confused: I am using a netbook EEE PC and Ubuntu is in a dual-boot with Windows 7 (which was originally the only OS on it.) Wireless worked fine before I upgraded from 10.04 to 10.10

I know this probably isn't enough, are there any commands I can use to get more information?

I am a beginner "absolute beginner" so please provide me with detail when answering my question. Thanks.

You could tell us the manufacturer of your eeepc and model.
Helps alot when trying to identify the chipset and if there's any bug raports already been made.

---

### Post by DirtyPC on 2010-11-05
Umm.. could you post ifconfig?

Also, never though ubuntu worked very well on eee pc's, could just be me though.

---

### Post by corncob on 2010-11-05
Try the netbook remix.  Ubuntu 10.10 didn't support wireless in my eeepc netbook either but NBR does.

---

### Post by Gluebuntu on 2010-11-06
Here is the output of some commands.

iwconfig:
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
        
```

ifconfig:
```


eth0      Link encap:Ethernet  HWaddr e0:cb:4e:9b:54:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:f6:21:e0  
          inet6 addr: fe80::225:d3ff:fef6:21e0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2317 (2.3 KB)  TX bytes:1736 (1.7 KB)

```

ASUS Eee PC 1005HAB

Wireless Module: AW-NE785H

So, if I still wan't to stick with ubuntu, I need to downgrade to 10.04?:(

---

### Post by RaunchyRedneck on 2010-11-06
This is nuts.  

I was connecting to my home network (wireless N) just fine, then I upgraded to Meerkat away from home.  When I came back home, the wireless would not connect.  I switched the router from Wireless N to Wireless G, and now I can connect.

I hope the worldwide community can get this resolved.  I'm just starting, but I hope to contribute if and when I can.

---

### Post by Goku34 on 2010-11-06
Try connecting to you modem or router with a Ethernet cable. That work for me when I first put Ubuntu 10.04 on my computer. I had to do that with Ubuntu 10.10
When you connect the Internet should work but only with the cable. if you want wireless go to system>administration>additional drivers and then install the wireless drivers. if there are two install both just to be safe.

---

### Post by Gluebuntu on 2010-11-08
Thank you very much for the advice everyone, for now I'm just sticking with 10.04

I tried NBR by the way and that didn't even recognize that I had anything to go wireless with (It was pretty cool though).

---

### Post by John Peschken on 2010-11-08
Which eeePC do you have?  I have a 904HA, and have had no troubles with Ubuntu 10.04, 10.10, or Mint.  I'm not near it right now, but that has an Atheros brand wireless adapter, I think.  

I did have trouble similar to what you describe one time.  I went through the steps to set up the connection again, telling it I wanted to connect to a non-broadcast SSID, supplied the WPA2 password,  and it has been healed since.  I'm guessing you have probably been down that road already, but if not maybe that will help.

---

### Post by John Peschken on 2010-11-08
> **John Peschken said:**
> Which eeePC do you have?  I have a 904HA, and have had no troubles with Ubuntu 10.04, 10.10, or Mint.  I'm not near it right now, but that has an Atheros brand wireless adapter, I think.  



Oops!  I see you answered that already.  Sorry.

---

### Post by ricardisimo on 2010-11-16
I have wireless disabled as well. I've looked to see if anything got blacklisted by accident, but I can't spot it. I'm on a Compaq Presario CQ60 Notebook PC. the internal adapter is as follows (as per "sudo lshw":
```
*-network DISABLED
             description: Wireless interface
**             product: AR5001 Wireless Network Adapter**
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:24:2c:6d:fa:9b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff
```
Ive tried my USB wireless adapter, which the laptop recognizes, but still can't use. Not only is wireless disabled perpetually, but the "enable wireless" option is grayed out, unalterable.

Both the internal and USB wireless were working flawlessly under 10.04. Thanks for any help you can give.

---

### Post by ricardisimo on 2010-11-16
I just tried
```
sudo rfkill unblock all
```
based on the suggestion from [here]("http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/"). No effect. Then I tried editing /var/lib/NetworkManager/NetworkManager.state manually. Nada.

By the way, the line I edited to read "WirelessEnabled=true", automatically reverts to "WirelessEnabled=false" at the next boot, maybe even immediately.

Any other suggestions?

---

### Post by Amefurashi on 2010-11-17
I've had the **very** same problem and this worked for me:

[http://blog.mattrudge.net/2010/07/29/acer-aspire-atheros-wifi-under-ubuntu-10-04/](http://blog.mattrudge.net/2010/07/29/acer-aspire-atheros-wifi-under-ubuntu-10-04/)

:)

---

### Post by uRock on 2010-11-17
> **Gluebuntu said:**
> Thank you very much for the advice everyone, for now I'm just sticking with 10.04

I tried NBR by the way and that didn't even recognize that I had anything to go wireless with (It was pretty cool though).
Ubuntu Nebook Edition doesn't have any different drivers from what the desktop version offers. It just has a few GUI modifications to make it look better on the smaller screen.

---

### Post by ricardisimo on 2010-11-17
> **Amefurashi said:**
> I've had the **very** same problem and this worked for me:

[http://blog.mattrudge.net/2010/07/29/acer-aspire-atheros-wifi-under-ubuntu-10-04/](http://blog.mattrudge.net/2010/07/29/acer-aspire-atheros-wifi-under-ubuntu-10-04/)

:)

I'm giving it a try, but obviously I'm not going to be installing a Lucid version on my 10.10, will I? "linux-backports-modules-wireless-maverick-generic" rather than "linux-backports-modules-wireless-lucid-generic" makes more sense. I just hope that line commands will work the same for both.

---

### Post by ricardisimo on 2010-11-17
No dice. Thanks, Amefurashi, but I installed linux-backports-modules-wireless-maverick-generic, rebooted and ran the commands as posted in the article, and it made absolutely no difference. Wireless is still disabled, and the option to enable isn't there... still grayed out. Attaching little screenshot segment to that effect.

Actually, I'm going to reboot again, but I doubt that's the deal-breaker. Could a mod or admin please remove the [SOLVED] tag from this thread? The OP decided to stick with 10.04 rather than upgrade, which is not really a fix nor a solution, and certainly doesn't help folks like myself who would like more help with this problem. Thanks in advance.

---

### Post by walt.smith1960 on 2010-11-17
I would think the network adapter would be supported natively in Maverick.  Here is the relevant portion of 'lspci' on a ThinkPad.  This is an upgrade from Lucid which may or may not be relevant. The adapter is a TrendNet PCMCIA.

```
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
**16:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)**

```

so my Atheros AR5001 is supported without backports being enabled unless it's a adapter version issue.

---

### Post by ricardisimo on 2010-11-17
So, what would I need to post here to get some sort of diagnosis? Here's lspci:
```
~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by ricardisimo on 2010-11-18
A bump, by way of another request that a mod or admin remove the [SOLVED] tag from this thread.

---

### Post by bthomson100 on 2010-11-20
I'm having this problem too with an EEE PC 1005HAB and Ubuntu 10.10. I am able to turn the wireless on in Windows using Fn-F2 but not in Ubuntu. I just turned it on in Windows 7 and then it stays on even when I boot into Ubuntu. It would be nice to be able to turn it on and off in Ubuntu to save battery power when not using wireless but most of the time I'm plugged into AC power so it isn't a big deal yet. When I travel however, it might become an issue, although having a 6 cell battery is great, even when there's a wireless drain that I don't need.

---

### Post by ricardisimo on 2010-12-04
It's definitely only happening on my laptop, not the desktop computer. Can anyone point us towards a solution? Wireless connections are really not something one should have to worry about nowadays, seems to me.

---

### Post by ricardisimo on 2011-01-07
Any sort of help would be appreciated, including referring me to another forum. Several months now, and the only responses have been from others with the same problems. Thanks.

---

### Post by seeam khan on 2011-04-21
hello, 
i am using compaq presario CQ40. i install system>administration>additional drivers, then restart my machine. then wireless works great in one of my office branch. but in another branch wireless connection doesn't establish. i write down the password then click connect then it took a long time but after that the wireless window came out, then i click connect again and again but same thing happen every time....:(
i can connect both wireless with same laptop with winxp(so password must be ok). i am using ubuntu 10.10 inside winxp.

---

### Post by Acrosby on 2011-06-11
I am having similar issues on my desktop, I have a AE1000 USB, I dual boot win7/10.10, win7 connects np, 10.10 tries but doesn't. if I suspend the security on my router it will connect easily in 10.10, so must be a security issue. Any ideas??

---

