---
title: "Wireless detects networks fine but will not connect"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Muchacho_Gasolino on 2007-07-23
My wireless networking has been working fine ever since I installed Feisty a few months ago, even WPA security, but two weeks ago it suddenly stopped working. knetworkmanager detects all of the same networks that it used to, but quits at the 57% - "IP configuration started" spot.

I tried removing the security on my network and trying again, but no luck. I also tried connecting to the same network with Windows and everything worked fine. The wired connection works fine in windows and linux as well. I'm not an expert at using iwconfig, but I followed the man page and I think I entered everything correctly for the unsecured network and was unable to connect that way either.

I have an Atheros AR5212 in a Thinkpad T43.

---

### Post by Muchacho_Gasolino on 2007-07-30
sound familiar to anyone?

---

### Post by Muchacho_Gasolino on 2007-08-09
I removed the security from my network and I'm trying to connect using iwconfig, but no luck. Here's the iwconfig output:

right after I enter

      ```
sudo iwconfig ath0 essid "SSID"
```

, I get

    ```
 lo        no wireless extensions.

     eth0      no wireless extensions.

     wifi0     no wireless extensions.

     ath0      IEEE 802.11g  ESSID:"SSID"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:3908  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

     irda0     no wireless extensions.
```

But then, 30 seconds later or so, it changes to this:

     ```
lo        no wireless extensions.

     eth0      no wireless extensions.

     wifi0     no wireless extensions.

     ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:6115  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

     irda0     no wireless extensions.

```
Anyone know anything I should try? Here's lspci:

    ```
 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to    DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

I heard there were some driver problems with the Atheros AR5212 in certain kernels. I'm running 2.6.20-16-generic

---

### Post by clive_pearce on 2007-08-09
Hi, yesterday I had a similar problem. My Realtek NIC driver had been updated by Microsoft Updates. (yes I know Windows)

I rolled back the driver in windows device manager. This cured it for me, & another guy on this forum with a similar problem. 

Post back if it works.

---

### Post by Muchacho_Gasolino on 2007-08-09
Ok, so I found that there were some problems with the 2.6.20-16 kernel not including the driver, but that they should be fixed by installing the linux-restricted-modules package. I have that package installed for both the generic and 386 kernels.

---

### Post by versvs on 2007-08-09
> **Muchacho_Gasolino said:**
> Ok, so I found that there were some problems with the 2.6.20-16 kernel not including the driver, but that they should be fixed by installing the linux-restricted-modules package. I have that package installed for both the generic and 386 kernels.

I have exactly the same problem with kernel 2.6.22.9 in Gutsy. My card is Intel pro w3945 and it has been working properly with older kernels.

---

### Post by Muchacho_Gasolino on 2007-08-10
What does lspci report for your wireless chipset? Atheros AR5212?

---

### Post by Muchacho_Gasolino on 2007-08-10
I just went back to kernel 2.6.20-15, and it still doesn't seem to be working. With knetworkmanager, I got the card to associate with my access point once, but it still seemed to not be able to communicate with it. I haven't been able to get the card to associate using iwconfig.

---

### Post by Muchacho_Gasolino on 2007-08-10
So here is what happens when I use wpa_supplicant in kernel 2.6.20-16:

```
sudo wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
Trying to associate with 00:0*:**:**:**:** (SSID='SSID' freq=2437 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:0*:**:**:**:** (SSID='' freq=2437 MHz)
ioctl[IEEE80211_IOCTL_SETMLME]: Invalid argument
Association request to the driver failed
Associated with 00:0f:b5:ae:dc:a6
CTRL-EVENT-CONNECTED - Connection to 00:0*:**:**:**:** completed (auth) [id=0 id_str=]
```

iwconfig then says

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"FAMILYSTONE"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0*:**:**:**:**
          Bit Rate:36 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/94  Signal level=-39 dBm  Noise level=-96 dBm
          Rx invalid nwid:13830  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

```

But, I can't connect to my router or anywhere else on the internet. It's associated but then again not associated? I don't get it.

Also, I went back and censored my MAC because I got a feeling it might not be good to post it where all the bad guys can see it. Is there any cause for worry about publicizing a MAC address?

---

### Post by Muchacho_Gasolino on 2007-08-12
Ok, I got it working. I'm actually posting on it right now. It kind of feels like it's going unusually slow, though. I think what I was doing wrong earlier was just not getting an IP address with dhclient after I associated with iwconfig. After I did that, I wasn't able to load up any websites at first, but after a few minutes, I could. It was strange, because I could ping google.com fine right after I got an IP address, but I couldn't load it up in Firefox.

The pinging is still kind of acting strangely. I can't ping nytimes.com or my school's .edu address, but I can load up the web pages fine for both of them.

---

### Post by Muchacho_Gasolino on 2007-08-12
WPA is working now, too. Now the weird thing is that I can't pull up my router's page. I type in the router's IP in the address bar in Firefox and it tells me Problem Loading Page. If I plug this laptop directly into the router, though, it works fine.

---

### Post by Rigit on 2007-08-12
I am using Ubuntu with the gnome desktop and do not have a problem at all with any connections.  I am a newbie so I wanted to try Kubuntu to make sure I wasn't missing anything.  I downloaded the over 4 gig dvd and ran the "live" cd and cannot get wireless to connect at all even when putting a static ip in with all the other proper settings.  I am new to Linux but have supported Windows computers for years.  I am familiar with networking and ip addressing but am having no luck with KDE.  I have gnome working with VPN and opening up my remote desktop on my Windows XP pc at work through my home wireless network.  The laptop I am running the fully loaded Gnome version on is the same one I am trying to run Kubuntu on.  It is a Toshiba M45-s331.  I will never go back to Windows again after experiencing Ubuntu.  I tried OpenSuse with the Gnome interface but Ubuntu was much more intuitive for the things I do and ran much faster on those things.  Please help a newbie to experience the best of both worlds--KDE and Gnome.

PS  I guess I need to include that it does see my wireless home network but just will not connect to it and pass data.

---

### Post by Muchacho_Gasolino on 2007-08-12
Is your network secured? If not, try this:

Open up a terminal and type
```
iwconfig
```

It should output a list of of four or five different interfaces on the left, all of which should say "no wireless extensions" on the right except for one. In my case, it is ath0. Replace ath0 in all of the the following with whichever interface it is for you.

```
sudo iwconfig ath0 essid "yourssid"
```
```
sudo dhclient ath0
```

the iwconfig line should associate you with the router, and the dhclient line should get you an IP. If your network is secured, you'll have to do some other stuff. Let me know how this works.

---

### Post by Rigit on 2007-08-12
I do have wep.  I tried your suggestion and this is what I got

Listening on LPF/eth1/00:0e:35:c2:65:cf
Sending on   LPF/eth1/00:0e:35:c2:65:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I went ahead and went to the knetworkmanager and put in my wep keys and it came up.  I know my subnet mask is a 24 bit mask so I wouldn't expect it to find anything on a 255.255.255.255 subnet.  I may just dual boot Kubuntu and Ubuntu to make sure I don't run into problems.  I am on call for my company and need to be able to remote into my work pc.  I tend to be an all-or-nothing kind of person and really like to take the plunge without looking back.  Ubuntu is working so well that I feel I can get everything back up and working in probably an hour.  Thanks so much for responding so quickly.  People like you is what makes us newbies such easy converts to an excellent product. This stuff is so cool.  Ubuntu rocks:guitar:

---

### Post by Rigit on 2007-08-12
I do have wep.  I tried your suggestion and this is what I got

Listening on LPF/eth1/00:0e:35:c2:65:cf
Sending on   LPF/eth1/00:0e:35:c2:65:cf
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I went ahead and went to the knetworkmanager and put in my wep keys and it came up.  I know my subnet mask is a 24 bit mask so I wouldn't expect it to find anything on a 255.255.255.255 subnet.  I may just dual boot Kubuntu and Ubuntu to make sure I don't run into problems.  I am on call for my company and need to be able to remote into my work pc.  I tend to be an all-or-nothing kind of person and really like to take the plunge without looking back.  Ubuntu is working so well that I feel I can get everything back up and working in probably an hour.  Thanks so much for responding so quickly.  People like you is what makes us newbies such easy converts to an excellent product. This stuff is so cool.  Ubuntu rocks:guitar:

---

### Post by Muchacho_Gasolino on 2007-08-12
Yeah, the community is the best part. :)

I've never done this before (only used WPA with command-line), but I think this is what you should do to enter the WEP key, if you want to try.

First enter

```
sudo iwpriv ath0 authmode 1
```

If you have an open key, or authmode 2 if it's shared.

Then,

```
sudo iwconfig ath0 key <wep key (in hex)> essid "yourssid"
```

or

```
sudo iwconfig ath0 key <s:ASCII string of key> essid "yourssid"
```

then

```
sudo dhclient ath0
```

See if that does anything.

I'm getting all this from the [MadWifi wiki]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"), which has been pretty useful to me in figuring out my wireless problems.

---

### Post by Rigit on 2007-08-16
I have gone back to Ubuntu (gnome).  I tried to use Kubuntu but it was much harder for me to get things accomplished and was not as fast as gnome in the things i did.  I also had some lock-ups and sometimes my laptop wouldn't boot.  I would also loose my connectivity now and then.  I had it dual booting with Ubuntu\Kubuntu and the same problems I was having with Kubuntu connectivity bled through to my Ubuntu installation.  I had Ubuntu reloaded in about 1.5 hours and am very happy with it.  I think I have found my distro.  I created a powerpoint presentation for the president of my  company to give to about 150 people and it worked flawlessly even with sound bites embedded.  Keep up the fantastic work guys.

---

