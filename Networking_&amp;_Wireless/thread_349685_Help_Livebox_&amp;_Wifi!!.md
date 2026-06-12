---
title: "Help: Livebox &amp; Wifi!!"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by My_web on 2007-01-30
Hi Everyone 

I've just started using Ubuntu & find it great. I'm connected to the internet via USB cable to my livebox & that worked as soon as I plugged it in. 

As it's a laptop I'd like to get the wifi working but I've read more or less every thread I could find about it and I still can't solve the problem. It's reconized the wireless card because when I do "iwconfig" it shows:

[INDENT][B][I]lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-214 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      no wireless extensions.[/I][/B][/INDENT]

From what I understand Ubuntu has recognized my wireless card as ra0? Sorry if this is a stupid question. As I said I'm a newbie :( Any help would be greatly appreciated

---

### Post by Beej on 2007-01-30
I have a Livebox (orange in the UK?) and a ralink (ra2500) laptop card. 

All I had to do to get mine working was enter my details in gnomes network settings (wep key, essid) ticked the connect box, and most importantly pressed the button with a number 1 on it on the Livebox, which puts it into pairing mode.

Voila, it connects. Hope this helps if not let me know, and I'll try and help.

---

### Post by My_web on 2007-01-30
Hi

By Gnome Network Settings do you mean here:
System>>Administration>>Networking>>Wireless Connection?

If so I have filled that in like so:
**Network name (ESSID) :** Livebox-6740 (As written under Livebox)
**Password Type :** Hexidecimal ?:confused: 
**Network Password :** The 26 Digit Wifi Security Key on the bottom of the livebox

After that Connection Settings are on "Automatic configuration DHCP"

And I put the livebox in association mode by pushing 1 before trying to connect.

Is there something I am doing stupidly wrong? The password it is the security key on the bottom of the livebox right? :confused:

Thanks for your help!

---

### Post by Beej on 2007-01-30
Yeah sounds like your details are right, can you post the contents of your /etc/network/interfaces

my looks like this

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
wireless-essid Livebox-1968
wireless-key **************************

---

### Post by My_web on 2007-01-30
Erm sorry if I sound stupid but how do I find that?

---

### Post by My_web on 2007-01-31
I still haven't worked out how to find that :confused: 

Can anyone point me in the right direction to /etc/network/interface ?

Sorry as you can tell I'm a newbie lol

**EDIT: Don't worry I've found out how to get it**

> sudo gedit /etc/network/interfaces

---

### Post by My_web on 2007-01-31
Here are the contents for /etc/network/interfaces as you asked for

> auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface ra0 inet dhcp
wireless-essid Livebox-6740
wireless-key **************************

auto ra0

auto eth1

auto eth0

Any ideas?

---

### Post by Beej on 2007-01-31
Your interfaces file looks fine

Is your problem you can't connect to the internet? If so is the internet connection already set up, through another machine windows or similar?

---

### Post by My_web on 2007-01-31
Yes the internet is already set up. I'm using the internet on the PC with ubuntu at the moment with a USB cable to the livebox. But I'd like to set up the wifi but whatever I try doesn't seem to work.

When I had windows my wifi card built in my laptop worked fine. Any ideas??

---

### Post by My_web on 2007-01-31
I've still got no further. I have tried kWifi & Wifi Radar with no success. What else could be the problem?

When I run Wifi Radar it shows 17 connections of which 2 have full signals?? Now I live in the country side and I know for sure that the only signal is from my Livebox. Why do all these appear & if it shows a signal why can't I connect to it? 

Help please I'm starting to pull my hair out lol :)

---

### Post by My_web on 2007-01-31
I've just tried Kwifi again and now I have a full signal from my Livebox.

But when I try using the internet in Firefox nothing happens!!! Can anyone help please???

On the livebox I have turned off the need for a security key as I live in the countryside no-one can connect to it anyway.

Any ideas as to why I still can't connect with it??

---

### Post by Beej on 2007-02-01
Plea for help here, can anybody else help?

---

### Post by BobboProfondo on 2007-03-27
I wonder if this is a timing issue. My experience with the Livebox ran a lot like this. 

Each time I connect I have to ensure that I've put the Livebox in pairing mode (press the wee '1' button on the back) before I switch the laptop on. 

Then if something gets reset for any reason, I have to put it in pairing mode again, then go into System -> Administration -> Networking and Deactivate and Reactivate my wireless connection while the Livebox is pairing. 

Incidentally I've connected two laptops from work (running Win2k and WinXP) and once they have paired once I don't have to do this again, but with my Ubuntu laptop I have to pair each time I switch it on. I understand that the Livebox uses MAC address filtering (and going into the livebox configuration from my WinXP desktop I can see the two work laptops' MAC addresses listed as 'connected' devices.)

Does anyone know how I can pair my Ubuntu laptop once and for all so I don't have to go through the pairing rigmarole each time?

TIA

Edit:
A couple of days later it has paired, and the MAC address is listed in the Livebox configuration pages, so... fixed.

---

