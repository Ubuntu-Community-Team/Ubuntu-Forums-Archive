---
title: "Airlink 101 AWLC3026 not working"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by miyamotofreak on 2007-11-12
I saw that the card works when with Ndiswrapper so I dled ndiswrapper and the xp driver for it. However when I hit install driver and select the inf file nothing happens. Any help? When I did lspci -v | less it did not come up but its in device manager. It's a 88w8335 [Libertas] 802.11b/g Wireless device made by Marvell.

---

### Post by miyamotofreak on 2007-11-12
Ok I installed the driver successfully and it says Hardware present but there is no option for Wireless in Network still.

---

### Post by Zedix on 2008-01-08
Having the exact same problem... I managed to install the windows driver and it says Hardware present, but the card doesn't show up in the network devices... 

If it can help, there's a green light that's supposed to be on when powered, but it's not on.

Some output that may be useful...

demsg | grep ndiswrapper
> [ 1813.028000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1813.040000] ndiswrapper (load_wrap_driver:118): couldn't load driver mrv8000c; check system log for messages from 'loadndisdriver'


lspci
> 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


Is it weird that it detects it as an Ethernet controller instead of a wireless ?

---

### Post by Zedix on 2008-01-08
Solved!

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

### Post by yurivict on 2008-02-12
I have AWLC3026 working but it has a major problem: on the network with encryption key it doesn't work.
Power light begins to flash and card isn't in RUNNING status.

Anybody made this card to work on the network with encryption?

It works almost fin on unprotected network. The only problem is that it shuts down sporadically.

---

### Post by danlaptic on 2008-07-11
> **Zedix said:**
> Solved!

[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

I followed this link, and followed the directions.  upon reboot, i still don't "have a wlan0 interface to play with"

i'm very sad.

what do you think i should i try next?

---

### Post by danlaptic on 2008-07-11
I also have installed a and working the intel pro/100 series.  I just upgraded from fiesty and was having problems getting it to work with that release, but there doesn't seem to be a problem.  the wired network works fine, it's just that when i want to get the wireless device working simultaneously with the intel pro/100.

is this going to be possible?

---

### Post by danlaptic on 2008-07-12
I feel bad for wasting anybody's time.  I used ndiswrapper and installed the windows xp driver.   it worked.

thanks

---

### Post by Exile32r4 on 2008-07-13
> **danlaptic said:**
> I feel bad for wasting anybody's time.  I used ndiswrapper and installed the windows xp driver.   it worked.

thanks

could you elaborate a little more? i have the same problem but it still doesnt show a wlan0 in Network

maybe its the driver im using?
i used the one in the guide and also tried the official driver

---

### Post by danlaptic on 2008-07-13
If it's a awlc3026 I assume it is an mrv8k card, but I suppose it doesn't hurt to check.

1.  To get the wireless card working I first checked to see if it was a mrv8k by going to the terminal and typing this into the terminal

lspci

In my case it was the last entry on the list and it displayed that Ubuntu did detect the hardware and that it was indeed a mrv8k card

2.  I disabled the bad driver by going to the terminal and entering this:

echo 'blacklist mrv8k' | sudo tee -a /etc/modprobe.d/blacklist

3.  I then used this link 
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k) and tried entering these commands in the terminal:

mkdir mrv
cd mrv
wget -c [http://www.cafuego.net/stuff/mrv.zip](http://www.cafuego.net/stuff/mrv.zip)
unzip mrv.zip
sudo ndiswrapper -i mrv8335.inf
sudo ndiswrapper -m
cd ..
rm -rf ./mrv

This didn't get my card working.

4.  I went to Applications, Add/Remove and typed in 'ndiswrapper ' and installed it.

5.  I went to the airlink 101 website and downloaded the windows xp driver:  [http://www.airlink101.com/support/index.php?cmd=files&id=56](http://www.airlink101.com/support/index.php?cmd=files&id=56)

6.  I unzipped the file and directed ndiswrapper to install the .inf file.  Then it worked.


I'm running 8.04 Ubuntu.
I hope this helps!

---

### Post by danlaptic on 2008-07-13
I should probably say that the after install, the Ndiswraper driver installation tool can be found in System > Administration > Windows Wireless Drivers

...At least for my 8.04 installation of Ubuntu

---

### Post by Exile32r4 on 2008-07-13
Ok great it works!
thanks a lot
it looks like it was a dumb thing to miss :(

---

### Post by danlaptic on 2008-07-15
I'm getting really poor signal strength with this card when there are multiple wireless networks detected.  

I've tried the Windows 2k driver as well as the XP, the 2k driver doesn't work at all.

I've removed the network manager utility and installed wifi radar, but the performance was the same no matter what utility I used.
 
Also, I have had no problems connecting to other public wifi networks, ie. panera & pulic library wifi networks as well as my home wireless network.  Signal strength has always been good.

I simply think this card looses much of its performance when there is interference from other wifi networks, and its probably not a problem with linux/ubuntu.  I searched for some product reviews, but nothing specific was stated about how it performs circa other wireless networks.

I'm thinking about buying a higher end model pcmcia wifi card (a whole $40), but would like to know if anybody else has experienced similar problems, if there is a workaround, or if I'm misinterpreting the symptoms, which are just really poor signal strength, 12-20% within 5-10 feet of Access Point when others seem to be connected just fine.

---

