---
title: "Internet connection problem"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by Duju on 2007-12-06
I am a compleat novice with ubuntu and linux for that matter,  I tried fiesty fawn both live disc and the install ,  both worked fine but i the meantime I changed my broadband setup from a usb to my ntl set top box , To ethernet  with cable modem and a separate  wirless router though my main compter is conneted to the router through a ethernet cable.  My modem and router was supplied by virgin media the router is called dynomode br 6004 w-g1 the modem has no name this setup works perfectly in windows,  but in ubuntu I get cannot conect to server.  I have also tried the new version (gutsy gibbion) live disc with the same result  
iwoud appretiate some help with his problem  thanks in advance

---

### Post by tak1150 on 2007-12-06
> **Duju said:**
> I am a compleat novice with ubuntu and linux for that matter,  I tried fiesty fawn both live disc and the install ,  both worked fine but i the meantime I changed my broadband setup from a usb to my ntl set top box , To ethernet  with cable modem and a separate  wirless router though my main compter is conneted to the router through a ethernet cable.  My modem and router was supplied by virgin media the router is called dynomode br 6004 w-g1 the modem has no name this setup works perfectly in windows,  but in ubuntu I get cannot conect to server.  I have also tried the new version (gutsy gibbion) live disc with the same result  
iwoud appretiate some help with his problem  thanks in advance

I'm a bit confused. Are you having problems with wired (ethernet) connection to your computer or wireless?

---

### Post by Duju on 2007-12-06
both there is no connection at all

---

### Post by tak1150 on 2007-12-06
Do you know what network card (ethernet) you have on your machine?
If so, what is it?
Have you tried clicking on the network manager icon in Ubuntu? If you left click on it, you can choose which connection to connect to.

Tak

---

### Post by Duju on 2007-12-07
my nic card is realtek rtl8139/10x family fast yes i have used the icon at the top of te screen i have tried to connect on  wired  auto and wirless and thinking that it cannot see my router i tried to enter my router address manually (192.168.1.1) still no joy

---

### Post by tak1150 on 2007-12-07
> **Duju said:**
> my nic card is realtek rtl8139/10x family fast yes i have used the icon at the top of te screen i have tried to connect on  wired  auto and wirless and thinking that it cannot see my router i tried to enter my router address manually (192.168.1.1) still no joy

Can you post the output of the following command from your terminal?
```
lspci
```

Are you sure that there is no security feature on the router? There may be an IP address filter of some sort.
There are other things you could try once you actually install Ubuntu, but I understand it's scary if even the ethernet network doesn't work in live CD.

---

### Post by Duju on 2007-12-07
i have included ifconfig and iwconfig don't know why but it seems to help in solving these sort of problems thought id just mention  my router has a firewall i have tried it with it turned off without any improvement also i have wpa on my wireless ubuntu asks me for the passkey when i supply it it just keeps asking the same question :-


ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 6700 XL (rev a2)
02:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:05.0 Communication controller: Agere Systems Unknown device 0620
ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:B2:1A:9B  
          inet6 addr: fe80::213:d3ff:feb2:1a9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D3:B2:1A:9B  
          inet addr:169.254.7.63  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:BF:52:68:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-BF-52-68-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$

---

### Post by tak1150 on 2007-12-07
It seems like you ARE connected to the ethernet work.
What happens when you ping a website? For example,
```

ping www.google.com -c 3
```

---

### Post by Duju on 2007-12-08
the reply was  ping: unknown host [www.google.com](www.google.com)

---

### Post by tak1150 on 2007-12-08
> **Duju said:**
> also i have wpa on my wireless ubuntu asks me for the passkey when i supply it it just keeps asking the same question :-



For the WPA pop-up thingy, you may want to select "TKIP" (or whatever you're using) from the pulldown menu. On my system, if the mode is set to "Automatic," it does not work. I have to choose TKIP manually.

Also find the IP address for your router (often it's 192.168.0.1) and ping that address as shown earlier.

If the above do not work, if I were you, I'd reset the router. This would cause any wireless settings (such as WPA passkey setting etc) to be lost, but all the settings will go back to the factory setting. In that setting, you should at least get ethernet connection between the router and your machine. Then trying pinging the router. If that does not work, then there is something wrong with the driver for your ethernet card in Ubuntu. If we come to that conclusion, then we'll try to find the right driver for you.

Tak

---

