---
title: "Hardy broke my Wireless!- Broadcom"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Questioneer on 2008-05-04
Hello-
So. I just upgraded(wiped 7.10 harddrive, install 8.04 fresh. I usually do this to keep my PC running smoothly and less bloated).
I'm using Linksys PCI Broadcom BCM4306 wireless card.

So, in 7.10, I could install the bcm43xx driver as it was in the restricted drivers. For some reason, it wasn't in the restricted drivers(or whatever it is called now). My ATi Radeon driver was there, but no wireless.
So. I go download Darkn00b's/bmartin's old wireless tool([http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)) and connect via ethernet, and install the firmware.(It says the firmware will work, too)
Then, an update for it pops up in the restricted drivers section. OK, I upgrade the driver.

Restart, and what do you know! I can see my network in the little applet on the bar perfectly. So, disconnect the ethernet, and try and connect to the network. OK, type in my password, which I'm 100% sure works, choose WPA, which I know works, and try and connect.

It will not Connect!
So, I try all the encryption types possible, and try manual config., nothing. 
'iwlist wlan0 scan' also shows my network, and confirms that the encryption type is WPA or WPA2.

I'm sure the network is good, too, because I have connected to it in 7.10, and just successfully connected to it on another Windows PC.

What could be wrong?

PS- I have wpa_suppliment

Thanks,
Questioneer

---

### Post by johnaaronrose on 2008-05-04
Questioneer,

I've got same problem. I'm now going to report it as a bug on Launchpad. Network Manager can't see any wireless routers, presumably due the [B]Broadcom 4311 wlan mini card not working.

Regards,
John
[/B]

---

### Post by deaf_girl on 2008-05-04
I have a friend who's having the same issuses with the Broadcom 4311 card in his laptop. It works in Windows but not Ubuntu 8.04.

Any help would be appreciated.

---

### Post by smorris on 2008-05-04
I'm experiencing the same issue. Upgrade to Hardy, activate broadcom 4318 wireless, and I can see my wireless AP. Choose WPA personal, enter password, but it does not seem to connect; I can't ping or resolve anything in FF. Same settings worked fine in Gutsy, and continue to work on my Mac.

---

### Post by exactopposite on 2008-05-04
try this

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

---

### Post by matic13 on 2008-05-04
i do that in 7.10 but in hardy i must type that too   
 
```
sudo apt-get install b43-fwcutter
```


```
sudo wget http://download38.mediafire.com/2bdi9e0d0l7g/jyjze9dd7t9/network-manager_0.6.6-0ubuntu1_i386.deb
```

```
sudo dpkg -i network-manager_0.6.6-0ubuntu1_i386.deb
```

reboot 

and i think that will works :)

---

### Post by Ayuthia on 2008-05-04
> **Questioneer said:**
> Hello-
So. I just upgraded(wiped 7.10 harddrive, install 8.04 fresh. I usually do this to keep my PC running smoothly and less bloated).
I'm using Linksys PCI Broadcom BCM4306 wireless card.

So, in 7.10, I could install the bcm43xx driver as it was in the restricted drivers. For some reason, it wasn't in the restricted drivers(or whatever it is called now). My ATi Radeon driver was there, but no wireless.
So. I go download Darkn00b's/bmartin's old wireless tool([http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)) and connect via ethernet, and install the firmware.(It says the firmware will work, too)
Then, an update for it pops up in the restricted drivers section. OK, I upgrade the driver.

Restart, and what do you know! I can see my network in the little applet on the bar perfectly. So, disconnect the ethernet, and try and connect to the network. OK, type in my password, which I'm 100% sure works, choose WPA, which I know works, and try and connect.

It will not Connect!
So, I try all the encryption types possible, and try manual config., nothing. 
'iwlist wlan0 scan' also shows my network, and confirms that the encryption type is WPA or WPA2.

I'm sure the network is good, too, because I have connected to it in 7.10, and just successfully connected to it on another Windows PC.

What could be wrong?

PS- I have wpa_suppliment

Thanks,
Questioneer

The module that you are trying to use is depreciated (bcm43xx).  The developers of that module have created b43/b43legacy with ssb to replace that one.  This happened in 2.6.24 (Hardy's kernel).  The guide that you used works for Gutsy and older.  There is a chance that bcm43xx is still working, but b43 or b43legacy is conflicting with it.  You will most likely have to go into /etc/modprobe.d/blacklist and blacklist bcm43xx (using sudo/root privilege) because the guide that you used would have removed it.

You should try matic13's suggestion.  I am not familiar with his network-manager suggestion though.  I have not tried it.  I have a 4306 rev 03 (14e4:4320) and it works fine with b43-fwcutter.

---

### Post by Ayuthia on 2008-05-04
johnaaronrose and deaf_girl-
Can you post your lspci -nn?  If you have a rev 02 version of the 4311, please try this guide: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990).  They tried a patch for this revision and found that the patch broke the other Broadcom cards so they had to back out the patch.  However, if you have the rev 01 version, you can try that post or you can install b43-fwcutter (if you have a working internet connection).

---

### Post by Ayuthia on 2008-05-04
> **exactopposite said:**
> try this

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)
This post will work for Gutsy or older, but the Hardy version is using the b43 and ssb modules with requires additional steps.  This post would be more helpful: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by alawho on 2008-05-04
I have broadcom as my ethernet manager, a bcm5705, but it's intel that's being used for the wireless.  Intel's ipw2200 driver is what's installed now and all I had to do was enable the radio of the wireless on the pc.  First I checked the bios and it was enabled, then on my Dell X300 I toggled (Fn and F2) to enable the card.  My newer Dell actually has a switch on the side of the laptop.  Since then I've had no problems.

---

### Post by Questioneer on 2008-05-04
Hey-
Thanks for the help everybody.
> i do that in 7.10 but in hardy i must type that too 
matic- Everything works except that last line. I get:
> 
dpkg-deb: `network-manager_0.6.6-0ubuntu1_i386.deb' is not a debian format archive
dpkg: error processing network-manager_0.6.6-0ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 network-manager_0.6.6-0ubuntu1_i386.deb


When running it.

> This post will work for Gutsy or older, but the Hardy version is using the b43 and ssb modules with requires additional steps. This post would be more helpful: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)
OH noes! NDiswrapper is an extreme last resort for me; I detest it. I suppose I'll try it next, but...

Anyway- I completely reinstalled 8.04 again because I had screwed around with some of the wireless files and GNOME programs waaay too much.
This time, the broadcom driver was an automatic option, so I installed it completely using the Restricted Drivers thing.

Here's my iwconfig output:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WURN1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:E9:A4:2E   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


and iwlist wlan0 scanning output:
> 
          Cell 01 - Address: 00:18:01:E9:A4:2E
                    ESSID:"WURN1"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=76/100  Signal level=-52 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000042a81181



Any ideas? Now it even appears I'm connected to the network...
PS- There is NO Mac Filtering on the router.

Cheers,
Questioneer

---

### Post by Ayuthia on 2008-05-04
Does ifconfig show an inet addr?  It should look something like:
```
wlan0     Link encap:Ethernet  HWaddr 12:aa:34:bb:56:cc
          inet addr:192.168.0.240  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe32:fc24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15844838 (15.1 MB)  TX bytes:2352447 (2.2 MB)

```

You might even want to take a step back and remove any encryption on your router until you can get it connected.  It will help you pinpoint your issue.  Can you post your lspci -nn also?  The 4306 card can be either b43 or b43legacy.

---

### Post by Questioneer on 2008-05-04
ifconfig:
> wlan0     Link encap:Ethernet  HWaddr 00:12:17:7e:f6:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lspci -nn:
> 
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770]
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771]
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller [8086:27c1] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
01:00.1 Display controller [0380]: ATI Technologies Inc RV380 [Radeon X600] [1002:5b72]
04:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] (rev 01)
05:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
05:05.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)


I'll test my router without encryption. The embarrassing truth right now is I can't find the option to turn Encryption off on the routers 192.168.1.1 configuration website! Verizon seems to be making it very hard to turn off Encryption.

Quite frankly, I don't care about encryption. I live in the country with wide open space, so it isn't like 3 blocks down the street a guy is hacking into my PC to steal personal data. However, those who share the wireless network with me demand encryption...

---

### Post by Ayuthia on 2008-05-04
Well, the 4306 card that you have is the same as my Dell laptop and it is happy using the b43 driver.  I am in a similar situation as you, I am in the country so I have no encryption on mine.  If anyone is coming in to hack into my laptop, they are either coming in through dialup or else they are sitting in my driveway and I will be able to see them...

Unfortunately, I have not tried using WPA on mine as of yet.  I am planning to do it soon more for educational purposes, but I have not found the time yet.

---

### Post by psiklotron on 2008-05-04
matic3's post from 7 hours ago worked for me.
I just typed sudo apt-get install b43-fwcutter into command and the wifi card started working. I have not tried updating or restarting yet but at least the blue light indicating my wifi card was working came on and i can see my WEP connection.

thanks much. I'm on a compaq presario v2000 with a fresh install of hardy heron.

---

### Post by Questioneer on 2008-05-04
Yeah: I can connect to the network without the encryption...

---

### Post by Questioneer on 2008-05-04
I'll try the ndiswrapper approach tommorrow.
Thanks everyone.

---

### Post by johnaaronrose on 2008-05-05
Ayuthia,

Relevant part of lspci -nn is:
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

I'm confused as to what to do. I have ndiswrapper loaded with the relevant Windows driver installed, but it's no go with eth1 as it doesn't pick up the router. I had the idea that the fwcutter method no longer worked from Gutsy onwards?

---

### Post by Ayuthia on 2008-05-05
> **johnaaronrose said:**
> Ayuthia,

Relevant part of lspci -nn is:
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

I'm confused as to what to do. I have ndiswrapper loaded with the relevant Windows driver installed, but it's no go with eth1 as it doesn't pick up the router. I had the idea that the fwcutter method no longer worked from Gutsy onwards?
Actually, the bcm43xx-fwcutter is not working for Hardy on forward.  It has been replaced with b43-fwcutter.  I have been able to get both ndiswrapper and b43 working on my 4311 rev 01.

Can you tell me what you have done so far for ndiswrapper?  You will need to do is make sure that b43 is blacklisted in /etc/modprobe.d/blacklist and ndiswrapper is in /etc/modules.  The last part is figuring out if you need ssb or not.  Do you know what your wired card is?  If it is a Broadcom, you might have to do something special.  If it is not, you should be able to just blacklist ssb.

---

### Post by exactopposite on 2008-05-05
> **Ayuthia said:**
> This post will work for Gutsy or older, but the Hardy version is using the b43 and ssb modules with requires additional steps.  This post would be more helpful: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

i linked to the wrong post. The one u linked to is what i meant to say. The info there worked for me

---

### Post by Questioneer on 2008-05-05
Is there a way I could possibly get WPA working without ndiswrapper?
PS- I checked, and I connect to networks fine without Encryption.

---

### Post by Ayuthia on 2008-05-05
> **Questioneer said:**
> Is there a way I could possibly get WPA working without ndiswrapper?
PS- I checked, and I connect to networks fine without Encryption.I am not for sure.  I would think so.  There are people out there using b43 and WPA.  I am going to try and see if I can get it set up over here.  If I can, I will let you know.

---

### Post by johnaaronrose on 2008-05-05
Ayuthia,

I have ndiswrapper as last line of /etc/modules.

Wired ethernet card is Broadcom 4401.

I have 'blacklisted' b43 (in /etc/modprobe.d/blacklist).

I have done sudo /etc/init.d/networking restart.

Now showing wireless routers in Network Manager applet. 

Able to connect to my wireless router using WPA & view websites OK.

Thank you.

---

### Post by Ayuthia on 2008-05-05
> **johnaaronrose said:**
> Ayuthia,

I have ndiswrapper as last line of /etc/modules.

Wired ethernet card is Broadcom 4401.

I have 'blacklisted' b43 (in /etc/modprobe.d/blacklist).

I have done sudo /etc/init.d/networking restart.

Now showing wireless routers in Network Manager applet. 

Able to connect to my wireless router using WPA & view websites OK.

Thank you.
I am not for sure if you have the setup already to make sure that ssb is loaded after ndiswrapper or not, so if you haven't, you can check this link out.  It gives three different options.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c)

---

### Post by Ayuthia on 2008-05-05
> **Questioneer said:**
> Is there a way I could possibly get WPA working without ndiswrapper?
PS- I checked, and I connect to networks fine without Encryption.

Well, here I am using WPA!  I have not fully figured out how to set it up through /etc/network/interfaces yet, but I have tested it through Wicd and NetworkManger (KDE)

How do you normally configure WPA?  Do you use NetowrkManager or do you go through /etc/netowrk/interfaces?

You might try out Wicd.  You can install it by:
```
sudo aptitude install wicd
```Nothing fancy.  When you open up screen, it will list out the available networks and there will be a little arrow by the name.  Click on the arrow and find Advanced Settings.  From there, just find the encryption section and enter your info there.

EDIT:
I did end up getting WPA-PSK working through /etc/network/interfaces.  I used this link: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) and followed the section on Sample configuration WPA1 & DHCP, ESSID broadcast enabled.  Worked without any issues.

---

### Post by Questioneer on 2008-05-09
Help! WICD does NOT work for me!
So, I go find my network in wicd, and click on the WPA 1/2 encryption, type in my encryption code, and it DOES NOT WORK! It simply doesn't connect, and seems to stall for a while at 'Obtaining IP Address'
What is wrong????

MY router info:
WPA2 TKIP, ASCII
No ESSID broadcast, but WICD shows it simply as 'WPA2', which I click on.

I really, REALLY do not want to try and do that command line thing; I've reinstalled 8.04 like 3 times after screwing THAT up...

---

### Post by Questioneer on 2008-05-09
Could someone create a file as in that command line explaination creates for me, because whenever I try it, it never, ever works.

---

### Post by Questioneer on 2008-05-09
Oh-
I've also tried just WPA 1 encryption, which also doesn't work.

---

### Post by Ayuthia on 2008-05-09
> **Questioneer said:**
> Oh-
I've also tried just WPA 1 encryption, which also doesn't work.

You might try:
```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <passkey>

```
Add that information into /etc/network/interfaces (via gksu gedit /etc/network/interfaces) and then restart your network (sudo /etc/init.d/networking restart).  Just replace your essid with your essid and the passkey with your passkey.  This is a sample PSK version.  I am currently out of town so I cannot test other WPA connections.

---

### Post by Questioneer on 2008-05-11
Hello-
Sorry, but that didn't work either.
I'm beginning to believe that the problem is the bcm driver.
Turns out I can't connect to any wireless network, and I was wrong earlier.
I've tried:
-WICD
-NDiswrapper
-Ubuntu restricted driver
-Athuya's thing from above

none have worked. I have not been able to CONNECT(But could see) any network with the above.(Except NDiswrapper, that didn't work at all)
 I'm a bit hesitant to try the posted method on pg. 2, as it seems to be for a mini-PCI card.
Can someone help?
Thanks,
Questioneer

---

### Post by Questioneer on 2008-05-11
By the way, I'm using a PCI Linksys Wireless G with Speed Booster adapter.
Thanks.

---

### Post by Questioneer on 2008-05-11
Model Number:
WMP54GS

---

### Post by anomsuratno on 2008-05-14
This link might help you with BCM43xx and Hardy:

[http://anomsuratno.wordpress.com/]("http://anomsuratno.wordpress.com/")

---

