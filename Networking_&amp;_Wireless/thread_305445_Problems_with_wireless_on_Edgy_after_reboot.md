---
title: "Problems with wireless on Edgy after reboot"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by omarino on 2006-11-23
I newbie here, so be tolerant, please :). I've managed to install edgy on my hp notebook and things are working quite nicely. But there is a strange problem with my wireless connection, that bugs me!

I managed to configure the wireless on my notebook to connect to a wireless router (static adress and WEP), but after each restart the internet is not working.

The wireless card in the panel shows, that it is conneted, the signal strength is over 95% but pings on the network are not working.

I've found out, that to make the connection alive again, i have to change the settings of the wireless adapter (password firs to asci and than back to original settings - hexadecimal). After that the network starts responding as it should.

Maybe somebody has a clue, what is the problem, or if not - can help me write a script that wold set the wrong settings and than the right ones again, to reset the network automaticaly after each reboot.

Thanks, o

---

### Post by ovimunt on 2006-11-23
I've got exactly the same problem. 

The thing is that I've been using Ubuntu Dapper for quite a while and everything used to work fine. Now I've got a new HDD so I thought to do a fresh installation of Ubuntu Edgy. All my problems started with this new installation.

Fortunately I still have my old HDD and all the data is still there so I connected it back and started again in Dapper and everything works FINE! So I am pretty sure the problem is down to Edgy.

Also, I've tried quite a few things to fix it but nothing worked and I'm starting to loose my patience now. One thing I've noticed is that at times, when I check the internet protocol for the wireless interface, only IPv6 appears and no IPv4 and this is obviously a problem. Once I restart the wireless both IPv4 and IPv6 show up and it works, sometimes... but not always... So next I've tried to disable IPv6 by editing the ***/etc/modprobe.d/alias ***file but surprisingly enough IPv6 remains enabled no matter how many times I restart the computer.

In conclusion I've got a feeling this problem is related to IPv6 but I'm not quite sure how to fix it so I'll stick to Dapper for now.

It would be great if anyone could help with some suggestions. 

Thanks

---

### Post by simosx on 2006-11-23
> **ovimunt said:**
> I've got exactly the same problem. 

The thing is that I've been using Ubuntu Dapper for quite a while and everything used to work fine. Now I've got a new HDD so I thought to do a fresh installation of Ubuntu Edgy. All my problems started with this new installation.

Fortunately I still have my old HDD and all the data is still there so I connected it back and started again in Dapper and everything works FINE! So I am pretty sure the problem is down to Edgy.

Also, I've tried quite a few things to fix it but nothing worked and I'm starting to loose my patience now. One thing I've noticed is that at times, when I check the internet protocol for the wireless interface, only IPv6 appears and no IPv4 and this is obviously a problem. Once I restart the wireless both IPv4 and IPv6 show up and it works, sometimes... but not always... So next I've tried to disable IPv6 by editing the ***/etc/modprobe.d/alias ***file but surprisingly enough IPv6 remains enabled no matter how many times I restart the computer.

In conclusion I've got a feeling this problem is related to IPv6 but I'm not quite sure how to fix it so I'll stick to Dapper for now.

It would be great if anyone could help with some suggestions. 

Thanks

To figure out if you really have the "IPv6" issue, run the command

$ host [www.google.com](www.google.com)

and post the full result. If you have the IPv6 issue, you will get a strange error message at the end of the command.

"host" is a program like nslookup that resolves hostnames, etc.

---

### Post by FrodoB on 2006-11-24
> **omarino said:**
> I newbie here, so be tolerant, please :). I've managed to install edgy on my hp notebook and things are working quite nicely. But there is a strange problem with my wireless connection, that bugs me!

I managed to configure the wireless on my notebook to connect to a wireless router (static adress and WEP), but after each restart the internet is not working.

The wireless card in the panel shows, that it is conneted, the signal strength is over 95% but pings on the network are not working.

I've found out, that to make the connection alive again, i have to change the settings of the wireless adapter (password firs to asci and than back to original settings - hexadecimal). After that the network starts responding as it should.

Maybe somebody has a clue, what is the problem, or if not - can help me write a script that wold set the wrong settings and than the right ones again, to reset the network automaticaly after each reboot.

Thanks, o

This sounds like your DNS hosts are not setup correctly.  Can you verify those?

---

### Post by hasplu on 2006-11-24
I agree for the DNS hosts. I had the same problem on Drapper, after entering the correct DNS everything went OK

---

### Post by omarino on 2006-11-25
Guys, read my post please. After changing the password settings to ASCI and back to ORIGINAL HEXADECIMAL everything starts working. Without entering the DNS records, which are ok from the begining.
If it werw DNS than the pings on local network would give ok results, but they dont.

---

### Post by FrodoB on 2006-11-25
Guy, we did read your post, as you asked in the first post be a little tolerant yourself, the phrase, "the internet is not working", does not necessarily imply that local pings do not work, it could just indicate that the internet does not work, but that locally things do, which is typical and you don't specify, so thanks for tipping you hand on that one. 

   Then I would be suspect of whether the key is entered into the interfaces file correctly.
  
 You could test this by entering the wireless key in manually at a terminal prompt using the iwconfig command. Cut and paste is likely to give the more revealing outcome.
 
 You say this is an HP notebook, does this imply one of the Broadcom built in wireless devices and ndiswrapper, or something else? If it is ndiswrapper make sure that the device is called wlan0. My Compaq's 4311 does not work if ndiswrapper calls it eth1, but becomes happy if I fix the devices' name in /etc/modprobe.d/ndiswrapper so that is just says:
 
 alias wlan0 ndiswrapper
 
Another thing, if you are using ndiswrapper do you have any competing drivers blacklisted? 

 Good luck

---

### Post by omarino on 2006-11-25
Sorry, didn' mean to be rude. My hp has an Intel card  and i'm using the original edgy drivers. The funny thing is, that there is no obvious difference between the working and non working state.

Here is the inteface state, while the network is non responsive:
```
bp@ubu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"mrezica"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate:2 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-48 dBm  Noise level=-49 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

sit0      no wireless extensions.

bp@ubu:~$ host www.google.com
;; connection timed out; no servers could be reached
bp@ubu:~$ 
```

here are the same command after reseting the password type first to ASCI and than back to HEX:
```
bp@ubu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"mrezica"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-31 dBm  Noise level=-32 dBm
          Rx invalid nwid:0  Rx invalid crypt:38  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

sit0      no wireless extensions.

bp@ubu:~$ host [www.google.com](www.google.com)
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 209.85.135.103
[www.l.google.com](www.l.google.com) has address 209.85.135.104
[www.l.google.com](www.l.google.com) has address 209.85.135.147
[www.l.google.com](www.l.google.com) has address 209.85.135.99
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
bp@ubu:~$ 


```

---

### Post by FrodoB on 2006-11-25
Will you get the same good effect if you reset the key using iwconfig like this?

 sudo iwconfig eth1 key s:xxxxxxxxxxxxx

 sudo iwconfig eth1 key xxxxxxxxxxxxxxxxxxxxxxx

Or only going through the Networking panel?

This is ndiswrapper, correct? It sure looks like it? If so what version are you using?

What is the card ID in the output of lspci? That may lead us to a good how to that explains what we are seeing here.

---

### Post by omarino on 2006-11-26
it works with terminal too. I'll write a simple script for a fix after reboot and that is it.
I don't think is ndiswraper though, i didn't install any special drivers for wireless.
thanks

---

### Post by FrodoB on 2006-11-26
OK, you are really close then.  Let us know what wireless device you are using including make, model, and version. 

Also the output from lsusb or lspci that shows the device would help.  

In addition the contents of the /etc/network/interfaces file would be most helpful.


Along with a dump of the /etc/iftab file.

You may have to keep using a script, but maybe we can see why this is happening so that you can use the normal method.

---

### Post by omarino on 2006-11-26
```
bp@ubu:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 0000:0000  
bp@ubu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
02:06.0 CardBus bridge: Texas Instruments Unknown device 8039
02:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
bp@ubu:~$ 

```
/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface eth1 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid mrezica
wireless-key xxxxxxxxxx

auto eth1
```
/etc/iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:17:08:40:23:3b arp 1

```

---

### Post by FrodoB on 2006-11-26
So you are using ndiswrapper? Correct?

If do go an look at the file:

 /etc/modprobe.d/ndiswrapper

inside it should be mapping ndiswrapper to your interface name in this case eth1.  Change that from eth1 to wlan0 and then modify the contents of /etc/network/interfaces so that everthing that says eth1 now says wlan0.

This is really a stab in the dark, but I had to do a similar thing with my Broadcom bcm4311 on my Presario laptop to get it to work on bootup. I noticed in the dmesg output that the interface was brought up as wlan0 and was being changed to eth1, so I decided to try not having it change and it made it behave much better. 

This may not do anything for you, but then again it should not be doing anything for me either.

---

