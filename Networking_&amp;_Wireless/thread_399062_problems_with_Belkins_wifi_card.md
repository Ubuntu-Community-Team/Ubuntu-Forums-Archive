---
title: "problems with Belkins wifi card"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by led_scorched on 2007-04-01
I just installed Dapper Drake 6.06 LTS on a Toshiba Satellite A15.

I initially had issues getting the onboard ethernet card to work, but finally got it configured. But now i am trying to get the Wifi card to work without any success.

The card is a Belkins F5D7010 Ver 4100. When i goto Network Settings, it lets me Activate it, and claims it is working, but the card itself isnt doing anything. I dont even get the power light on it to come on.

Any ideas on how to get it working and connected?

---

### Post by Floppyjoe on 2007-04-01
Can you post the output of :
```
lspci
```

---

### Post by led_scorched on 2007-04-02
lspci
> 0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc essor to I/O Controller (rev 01)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Proc essor to I/O Controller (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated  Graphics Device (rev 01)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphi cs Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridg e (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller ( rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97  Modem Controller (rev 03)
0000:01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Eth ernet Controller (rev 83)
0000:01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbu s Bridge with ZV Support (rev 33)
0000:02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)


---

### Post by Floppyjoe on 2007-04-02
This is your wireless card here:
> Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

If you follow this link here it should be easy to set up:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)

---

### Post by led_scorched on 2007-04-02
tried this.  when i tried >  sudo ndiswrapper -i bcmwl5.inf

it shot back this> couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper line 135.


any ideas?

---

### Post by Floppyjoe on 2007-04-02
Is the file in your home folder?

---

### Post by led_scorched on 2007-04-02
its now in my home folder.  it originally DLed to my desktop.  now it wont let me remove the old one or reinstall because it already exist.

if it would be quicker and easier, you can IM me on MSN messenger or Yahoo

---

### Post by Floppyjoe on 2007-04-02
Just do this to remove invalid drivers:
```
sudo ndiswrapper -e bcmwl5
```

---

### Post by led_scorched on 2007-04-02
ok.  it deleted it.  i reinstalled it.  but it is still hanging up on line 135

---

### Post by Floppyjoe on 2007-04-02
I've been trying to duplicate that error but not having success.
Are both the .inf and .sys files in your home directory?

---

### Post by led_scorched on 2007-04-02
i got the .tar in there.  not sure about the .inf or .sys files

---

### Post by Floppyjoe on 2007-04-02
> **led_scorched said:**
> i got the .tar in there.  not sure about the .inf or .sys files
Open the tar file by double clicking on it and extract the driver files to your home folder.

---

### Post by led_scorched on 2007-04-02
> **Floppyjoe said:**
> Open the tar file by double clicking on it and extract the driver files to your home folder.

to /home or /home/me ?

---

### Post by Floppyjoe on 2007-04-02
> **led_scorched said:**
> to /home or /home/me ?
Sorry /home/username

---

### Post by led_scorched on 2007-04-02
by jove, i think we've got it.

i got lights a'blinking on the card.

thanks for your help!

---

### Post by led_scorched on 2007-04-02
another quick question.  When i first login, eth1 is set as my default connection.  And it shows signal, but i still have to go into system->admin->network and activate my wifi card.  is there a quick fix for this?  or is it just "one of those things"?

---

### Post by Floppyjoe on 2007-04-02
Did you do the:
```
sudo ndiswrapper -m
```
and 
```
sudo gedit /etc/modules
```
add the word ndiswrapper to this file then save and exit?

---

### Post by led_scorched on 2007-04-02
yea.  double checked, its there.

---

### Post by Floppyjoe on 2007-04-02
Are you using network-manager?
Can you post your /etc/network/interfaces file:
```
sudo gedit /etc/network/interfaces
```

This is what mine looks like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf


```

In this case my wireless interface is rausb0 and I have the information for my router connection under the rausb0 interface.

---

### Post by led_scorched on 2007-04-02
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid patterson

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1


need editting?

---

### Post by Floppyjoe on 2007-04-02
> **led_scorched said:**
> need editting?
It looks OK to me. I'm not sure why you would have to keep activating the card. You have me stumped for the moment. Maybe someone else has some experience with this and knows how to get around that.

---

