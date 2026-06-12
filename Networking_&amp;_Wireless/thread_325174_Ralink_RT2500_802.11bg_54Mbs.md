---
title: "Ralink RT2500 802.11b/g 54Mbs"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by krish3 on 2006-12-25
I can`t get my laptop connected :???:  ...I followed this link- [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#compile](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#compile)
but it didn`t work...what should I do? I have ubuntu 6.06.
newbie

---

### Post by mojoman on 2006-12-26
I have a card with that chip and it worked out of the box both Breezy and Dapper, no compilation needed (though I went through a minor hell trying to install the drivers for Debian). Is it detected at all? Could you post the output of ifconfig and iwconfig?

/Mojoman

---

### Post by krish3 on 2006-12-26
thanks for your response :) 

krish@krish-laptop:~$ ifconfig
eth0      kapseldus:Ethernet  HWaddr 00:14:2A:B0:BC:90
          UP BROADCAST MULTICAST  MTU:1500 meetrika:1
          RX pakette:0 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:0 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000
          RX baite:0 (0.0 b)  TX baite:0 (0.0 b)
          katkestus:217 baasaadress:0xc00

lo        kapseldus:Kohalik loopback
          inet aadress:127.0.0.1  mask:255.0.0.0
          inet6 aadr: ::1/128 skoop:host
          UP LOOPBACK RUNNING  MTU:16436 meetrika:1
          RX pakette:7 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:7 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:0
          RX baite:372 (372.0 b)  TX baite:372 (372.0 b)

ra0       kapseldus:Ethernet  HWaddr 00:0D:F0:1F:9E:9A
          inet6 aadr: fe80::20d:f0ff:fe1f:9e9a/64 skoop:ühendus
          UP BROADCAST RUNNING MULTICAST  MTU:1500 meetrika:1
          RX pakette:24 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:70 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000
          RX baite:1632 (1.5 KiB)  TX baite:4804 (4.6 KiB)
          katkestus:209 baasaadress:0x8000

krish@krish-laptop:~$ iwconfig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"SpeedTouch"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:11:F5:FC:CF:98
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=75/100  Signal level=-33 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

I hope that´s  you can understand,(diffrent language)

---

### Post by mojoman on 2006-12-26
Ok, it looks like the card is detected at least. You could try to bring it up with the command

sudo ifconfig ra0 up

(I'm not sure the sudo part is needed but it won't hurt).

Also, key configure files are etc/network/interfaces and etc/resolv.conf , you could have a look at those as well. 

interfaces should contain information such as IP, netmask, WEP-key (if used) etc. The following is an example of that file (roughly how mine looked with Debian)

```
auto lo 
iface lo inet loopback 

auto ra0 
iface ra0 inet static 
address 192.168.0.2 
netmask 255.255.255.0 
broadcast 192.168.0.255 
gateway 192.168.0.1 
up iwconfig ra0 essid WHATEVER-YOUR-ESSID-IS
up iwconfig ra0 channel auto (or # if you have specified a channel)
up iwconfig ra0 key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx (substitute x with your WEP-key)
```

resolv should contain your nameservers.

I'm away over the holiday so I can't access my linux machines right now but I have a server running with wireless ralink 2500 and that configuration should work for you as well. Also, I have my laptop running on ralink with Debian Etch, and that should also be of help. If you can't make any headway with this info just post back and I'll see what more I can think of. If that fails, I'll be home to my Linux machines on friday and we should be able to fix it then.

Merry Christmas, and so on...
/Mojoman

---

### Post by dmizer on 2006-12-26
blacklist ipv6.

```
gksudo gedit /etc/modprobe.d/blacklist
```
add the line:
> blacklist ipv6
to the end of the file, and reboot.  should work then.

---

### Post by krish3 on 2006-12-26
but when I have dhcp, do I have to put gateway,netmask and others too or would this be just enought?:

iface ra0 inet dhcp
wireless-essid SpeedTouch
wireless-key s xxx

auto ra0

I added blacklist ipv6 to the blacklist, but it didn`t work

---

### Post by mojoman on 2006-12-26
> **krish3 said:**
> but when I have dhcp, do I have to put gateway,netmask and others too or would this be just enought?:

iface ra0 inet dhcp
wireless-essid SpeedTouch
wireless-key s xxx

auto ra0

I added blacklist ipv6 to the blacklist, but it didn`t work

If you have a dynamic IP dhcp should be enough (as I have several machines at home I prefer to have static). Is the card lit up at all? Was there any effect at all from "ifconfig ra0 up"?

/Mojoman

---

### Post by krish3 on 2006-12-26
It dosen`t do anything:-|

---

### Post by W3ird_N3rd on 2006-12-26
Not sure so just asking, did you try [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) ? I didn't need to compile anything using that guide. My connection doesn't work [flawless]("http://ubuntuforums.org/showthread.php?t=325095"), but at least it works, and the trouble doesn't have anything to do with de Ralink driver.

---

### Post by krish3 on 2006-12-26
it works in winXP fine (I have two operating systems:ubuntu 6.06 and winXP)

---

### Post by dmizer on 2006-12-26
post the output of ifconfig again please.

---

### Post by pointym5 on 2006-12-27
For what it's worth, I have a CNet CWC854 (RT2500) card that worked for some time in Dapper. I just upgraded to Edgy, and now plugging the card into the laptop causes an immediate system freeze. I'm going to try a clean re-install, which honestly I don't know why I don't do every time. Upgrading almost never works for me.

---

### Post by krish3 on 2006-12-28
krish@krish-laptop:~$ ifconfig
eth0      kapseldus:Ethernet  HWaddr 00:14:2A:B0:BC:90
          inet aadress:192.168.1.66  bcast:192.168.1.255  mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500 meetrika:1
          RX pakette:362 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:350 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000
          RX baite:302957 (295.8 KiB)  TX baite:48953 (47.8 KiB)
          katkestus:217 baasaadress:0xec00

lo        kapseldus:Kohalik loopback
          inet aadress:127.0.0.1  mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436 meetrika:1
          RX pakette:5 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:5 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:0
          RX baite:272 (272.0 b)  TX baite:272 (272.0 b)

ra0       kapseldus:Ethernet  HWaddr 00:0D:F0:1F:9E:9A
          UP BROADCAST RUNNING MULTICAST  MTU:1500 meetrika:1
          RX pakette:29 vigu:0 ära visatud:0 ületäit:0 kaadri vigu:0
          TX pakette:72 vigu:0 ära visatud:0 ületäit:0 carrier:0
          kollisioone:0 txqueuelen:1000
          RX baite:4078 (3.9 KiB)  TX baite:4380 (4.2 KiB)
          katkestus:209

---

### Post by krish3 on 2006-12-28
I retried that link,It didn`t work...but when I tested:sudo ifdown ra0 and later tried to put it up again then I got this: No DHCPOFFERS received.
No working leases in persistent database - sleeping. :confused: 
I read google something about ifcfg file...could that be the problem?

---

### Post by dmizer on 2006-12-28
do you have two adapters?  if so, you're not going to be able to get an ip from your ra0 connection if you're connected via another adapter (eth0 in this case).

you can't use two adapters on the same subnet.

so, to make the ra0 work, you'll have to take down the eth0 adapter first, then try to get a lease with the ra0.
```
sudo ifdown eth0
sudo ifup ra0
```

---

### Post by krish3 on 2006-12-28
it didn`t work:( 
I got whit ifdown eth0 - ifdown:interface eth0 not configured
and whit ifup ra0 - ifup:interface ra0 already configured

---

### Post by dmizer on 2006-12-28
do you actually have more than one network adapter (wired and wireless for example)?

post the contents of /etc/network/interfaces

as well as the output of lspci

---

### Post by krish3 on 2006-12-29
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid SpeedTouch


wireless-key s:xxxxxxxx

auto ra0


krish@krish-laptop:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller  (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI (rev 80)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 A udio Controller (rev 80)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev  80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 597 5
0000:02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:02:04.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)

yes I have, but when I`m not in wired connection then wireless still dosen`t work...(even if I deactivate it)

---

### Post by mojoman on 2006-12-30
Krish3, I'm back in Stockholm so now I got access to my machines. Let's see if we can sort this out.

I compared the howto that you followed with the howto that I followed when I installed Debian Etch and they're a bit different. Given that Ubuntu is based on Debian, and on Etch to boot if I'm not mistaken, I figure you might give this one a go.

Now, I had a minor hell trying to work this out on Debian Sarge BUT with Sarge it had to be done with a downloaded .deb and then manually compiled, and the compilation bit always failed. I then tried Etch and it installed and auto-compiled at first try.

I checked the repos with an ```
apt-get install -s rt2500-source
``` (-s for simulate) just to see if the package was there and what it was depending on and that package is available in the ubuntu dapper repos. Using module-assistant I figure that you should be able to auto-compile the package and then just enter the relevant information in your configuration files.

The link to the howto is:

[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)

I think it's an easier howto but it does of course require ... well, an Internet connection :rolleyes:  However, I hope the CD or DVD contains the essential packages, otherwise, you just have to download them as .deb and install them manually via USB stick or something. What you need is, I think,  build-essential, module-assistant, and the kernel-header that corresponds to your kernel. And the rt2500-source of course.

Hope this works...
/Mojoman

---

