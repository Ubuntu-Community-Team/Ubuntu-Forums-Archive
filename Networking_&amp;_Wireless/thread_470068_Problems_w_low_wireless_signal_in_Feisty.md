---
title: "Problems w/ low wireless signal in Feisty"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by darth_indy on 2007-06-10
I'm having problems with low wireless signal on a new install of Feisty. I've pretty new to Ubuntu - installed about 1 1/2 weeks ago - but am ready, willing, and able to go into the terminal, but I'll need pretty clear instructions.

I have a Linksys WPC54G ver. 3 PCMCIA card, and I've already gotten it to work with the Broadcom drivers, but I'm still having problems with the connection strength. Right now, I'm about 10 feet away from the router, and it's showing 91% - not a problem, but when I go upstairs, it'll show around 40%. I can't connect to the internet up there, though when I had a Windows 2000 system set up, it connected fine with the same percentage. When I try lowering the sensitivity via iwconfig, I get this message:

Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device eth0 ; Operation not supported.

All I want to do is be able to get online at low connection. It shows the wireless network perfectly fine, but it refuses to go online. Is this a i-d-ten-t problem, or is there a tweak I can do in terminal or elsewhere? Any help would be greatly appreciated. Please let me know if there's any other info you need to help me.

**iwlist:**

eth0      Scan completed :
          Cell 01 - Address: 00:1A:70:45:8A:2B
                    ESSID:"*********"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-25 dBm  Noise level=-11 dBm
                    Extra: Last beacon: 32ms ago

**iwconfig:**

eth0      Scan completed :
          Cell 01 - Address: 00:1A:70:45:8A:2B
                    ESSID:"*********"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=91/100  Signal level=-25 dBm  Noise level=-11 dBm
                    Extra: Last beacon: 32ms ago

---

### Post by darth_indy on 2007-06-10
If it helps any, I'm using an older laptop - an IBM Thinkpad 600x. It used to have Windows 98 - the bane of my existence - before I installed Ubuntu. Everything else seems to be working fine, so I don't know if it would affect anything.

---

### Post by darth_indy on 2007-06-10
I hate adding a bump post, but I really need this problem fixed! Pretty please?

---

### Post by kevdog on 2007-06-10
As you using network manager to connect??

---

### Post by darth_indy on 2007-06-10
Yeah, I'm using network manager, but I can go thru the Terminal too if you need me to

---

### Post by kevdog on 2007-06-10
Couple of thing to try first:

1. Turn off encryption in the router, and tell me what happens.  I want to make sure this is not related to WEP.

2. What does /etc/network/interfaces file look like?

---

### Post by darth_indy on 2007-06-10
I'm still waiting for the other computer to start up, because it's the one with the router config. This is my etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface ppp0 inet ppp
provider ppp0

iface eth0 inet dhcp
wireless-essid {SSID}
wireless-key {WEP Key}

---

### Post by darth_indy on 2007-06-10
OK, I've turned off the WEP encryption. In iwconfig it lists the link quality as 70%, and iwlist has it as  91%. I don't know why it's different in the two.

---

### Post by darth_indy on 2007-06-10
Erm, was there any other info I needed to tell you?

---

### Post by darth_indy on 2007-06-10
OK, the only difference since I turned off WEP was that the signal got weaker, at least under iwconfig. I've noticed there was a difference between iwlist and iwconfig's percentages before, but I have no clue as to why. Did I do something wrong, or is that normal?

---

### Post by darth_indy on 2007-06-10
I turned WEP back on, and the signal's the same. So... I don't think WEP is the problem. (Yes, this is yet another bump message)

---

### Post by Karl S. on 2007-06-11
Helping bump, because I'm having a similar problem. WPA, not WEP. Broadcom 4318 in my laptop. Wireless works, but it deteriorates very quickly when I move away from the router. This isn't the case for the laptop running Windows.

---

### Post by darth_indy on 2007-06-12
Yet another bump - I really need wireless working upstairs!

---

### Post by darth_indy on 2007-06-13
Well, this is interesting... I just finished setting up another Ubuntu machine. Long story short, I cannabalized two junk systems and made one good system, and it installed Feisty, no problems. I have a wireless PCI card in - another Linksys, which is listed as compatible in the card lists - and the wireless works perfectly, at 38% signal strength. I set up the laptop right by it, and I get nothing.

My question is, is it the laptop's fault, the wifi card, the software, or Ubuntu?

---

### Post by jaguiler on 2007-07-11
I have very similar issue and it is very frustrating ?  Do I have to say ... never had these problems with XP .....
I hope we can get more reliabilty in other releases, as this WIFI support is rather disappointing.
:mad:

---

