---
title: "DWL-G650 D-Link Wireless Card Instalation"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by blakedut on 2008-04-27
Hi, im kinda new so explain it slowly.  I bought a D-Link DWL-G650 but it wont work when i plug it into my laptop with ubuntu.  Any help would be appreciated.

---

### Post by chili555 on 2008-04-27
Please tell us which chipset this card has. Open a terminal Applications -> Accessories -> Terminal and, with the card inserted, do:```
sudo lshw -C network
```You will get some data about your ethernet connection, if any, and your wireless. Post the wireless details and we'll get you going.

---

### Post by blakedut on 2008-04-27
I entered in what you said, and entered my sudo password and it came up with this:
```
PCI (sysfs)   
 
 
SCSI                       
  *-network         
       description: AR5001-0000-0000 
       product: Wireless LAN Reference Card 
       vendor: Atheros Communications, Inc. 
       physical id: 0 
       version: 00 
       slot: Socket 0 
       resources: irq:11 
  *-network 
       description: Ethernet interface 
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 42 
       serial: 00:08:02:ba:a4:7e 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 
  *-network 
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications Inc. 
       physical id: 3 
       bus info: pci@0000:03:00.0 
       logical name: wifi0 
       version: 01 
       serial: 00:40:05:54:0c:23 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 

```

---

### Post by chili555 on 2008-04-27
Looks good so far. Let's now see:```
sudo iwconfig wifi0
sudo iwlist wifi0 scan
```Then we'll proceed.

---

### Post by blakedut on 2008-04-27
I enter the terminal and enter my password and it shows this:
```

blake@blake-laptop:~$ sudo iwconfig wifi0
[sudo] password for blake: 
wifi0     no wireless extensions.

blake@blake-laptop:~$ sudo iwlist wifi0 scan
wifi0     Interface doesn't support scanning.

blake@blake-laptop:~$ 

```
:guitar:

---

### Post by chili555 on 2008-04-27
Come on, wireless, no more hiding!

Please go to System-> Administration -> Network and unlock by giving your password. Is the little box next to Wireless checked? Check it, if not. Select Properties and check Enable This Connection. Did your wireless spring to life?

---

### Post by blakedut on 2008-04-27
What does it look like if its checked?

---

### Post by blakedut on 2008-04-27
And should roaming mode be enabled?

---

### Post by blakedut on 2008-04-27
I un-checked roaming mode and entered in my settings for the wireless network, but when i start mozilla it has a Page Load Error???

---

### Post by blakedut on 2008-04-27
By the way, im using 8.04

---

### Post by chili555 on 2008-04-27
Roaming mode should be checked if you will roam, that is, travel from Starbucks to airport to motel, etc. and want to roam from network to network. If most of your activity will be sitting at your desk at home, in my opinion, you don't want or need it.

Are you sure your settings are correct? ESSID is strictly case sensitive. Using any encryption? WEP, WPA or Klingon?

Did you give it a few seconds to try to connect? By the way, I'd suggest DHCP until we're sure all the other settings are correct.

---

### Post by blakedut on 2008-04-27
I gave it some time to connect, my router is strictly DHCP and it uses 64bit HEX, i entered the correct ESSID (Although in my other windows machine it is called an SSID)

P.S. I accidently told it WEP Ascii instead of WEP Hexidecimal, but it still refuses to connect.

---

### Post by chili555 on 2008-04-27
> in my other windows machine it is called an SSIDThat's *so* last year. Hpefully, for you Windows will soon be a fading memory!

Let's go back to the terminal:```
iwconfig
```Make sure the wireless interface is actually wifi0.```
sudo iwconfig wifi0 essid <your_ESSID>
sudo iwconfig wifi0 key <your_10_character_HEX>
sudo dhclient wifi0
```Sometimes, interfaces won't respond properly to dhclient, and require:```
sudo ifup wifi0
```Let us know.

---

### Post by blakedut on 2008-04-27
this is what happened when i typed ```
iwconfig
```

```

blake@blake-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wifi0     no wireless extensions. 
 
ath0      IEEE 802.11g  ESSID:"HOME"  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1   
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/70  Signal level=-90 dBm  Noise level=-90 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```
And this after ur second command
```

blake@blake-laptop:~$ sudo iwconfig wifi0 essid HOME 
Error for wireless request "Set ESSID" (8B1A) : 
    SET failed on device wifi0 ; Invalid argument. 

```

I have a strange feeling that u should be usin Ath0 instead of wifi0.

P.S. i got the wireless working by using ath0 instead of wifi0

---

### Post by darascon on 2008-06-05
I have the exact same problem with the exact same card specs, only I still cant seem to configure it to work. This is my first foray into linux, so I'm a bit lost. Thinking about trying the madwifi drivers but wanted to give a little system tweaking a try first.

---

### Post by dunbrokin on 2008-06-16
I have the same card - but not the same problem I think. I can see the my router (also Dlink) but I cannot connect because my router wants 64/128 bit hex and the Network Manager in Kubuntu does not have that option....how do I get the Network Manager to install more options?

---

### Post by dunbrokin on 2008-06-16
OK, I have got this card to work with Wireless Assistant....howeve, I can use Kopete and send IMs....but I cannot get Firefox to work with it...It just gives me an Offline Mode - try again!!

Very frustrating...

---

### Post by dunbrokin on 2008-06-16
> **dunbrokin said:**
> OK, I have got this card to work with Wireless Assistant....howeve, I can use Kopete and send IMs....but I cannot get Firefox to work with it...It just gives me an Offline Mode - try again!!

Very frustrating...

ok solved it by clicking work>offline .....darn!!

---

### Post by chris1890 on 2008-06-27
ok, erm, just went through the codes and stuff in the terminal, and basically, it wasnt working with wifi0 or whatever was similar to that.. if people cant get that to work, try wlan0 as that made mine work.

---

