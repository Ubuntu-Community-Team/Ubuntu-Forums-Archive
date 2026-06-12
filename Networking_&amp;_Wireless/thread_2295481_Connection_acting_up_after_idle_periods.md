---
title: "Connection acting up after idle periods"
date: 2015-09-19
forum: Networking &amp; Wireless
---

### Post by matanjonas on 2015-09-19
Heya folks.
I've been having a problem for the last couple of days, in which my Ubuntu 14.04 HP laptop is "losing" the wireless connection after long periods of idle time (i.e when I go to sleep). I log into the system after I return to it, and the wireless is connected but everything doesn't seem to have access to internet, whether it is the browser, Skype, Spotify, whatever. 
I've tried reconnecting to the same network, disabling and enabling the wireless networking alltogether, even restarting the computer - nothing helps. The only thing that solves it is disconnected the router and reconnecting it. I know it sound weird and not an OS problem but none of my flatmates have this problem, and neither does my phone, so maybe it is related somehow to my computer or Ubuntu?

Anyone has any idea? Anything I need to provide or check? It's the first time I'm writing a message on the board..

Thanks a lot!

---

### Post by praseodym on 2015-09-19
Please run the wireless-script from the sticky thread and show the outputs.

---

### Post by matanjonas on 2015-09-19
Right, sorry about that. Attached the .gz file on here

---

### Post by tgalati4 on 2015-09-19
You have a busy wireless neighborhood--lot of antennae and probably a lot of computers/phones connected to those antennae.  It's possible that your wireless shuts down because there is so much interference.  You have bluetooth coexistence turned on.  Try turning bluetooth off in BIOS and see if the connectivity improves.  Since bluetooth uses the same antenna as wireless, the additional interference could cause your connection to fail.

Your link quality is excellent and signal is quite strong:  Link Quality=70/70  Signal level=-38 dBm

Some wireless cards shut down when the signal is too strong as a safety measure.  Try moving the laptop away from the AP and see if the network stays up.

My signal at the moment is: Link Quality=61/70  Signal level=-49 dBm and I am 2 rooms away from the antenna.  You should be able to get a decent connection at 55/70 and -60 dBm.

Your router is using Channel 11 and you have many other AP's using that channel:

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      **12   APs on   Frequency:2.462 GHz (Channel 11)**
      1   APs on   Frequency:2.472 GHz (Channel 13)

Does your router and your laptop support 5 GHz band?  If so, use that, it tends to be less crowded.  If you don't have 5 GHz available, set wireless interference mode on--this will narrow your channels bandwidth from 40 MHz to 20 MHz because your signal is so strong.

---

### Post by matanjonas on 2015-09-19
Hey tgalati4, thanks for the quick response!

I tried to have a look around the BIOS for turning off BT but there doesn't seem to be any. I added the BT into the blacklist in blacklist.conf so it won't start as I boot the computer up, but I'm not sure if that's any good for the issue I'm trying to solve?

Furthermore I don't have anywhere else to put my laptop that's far from the router, I'm in the room furthest from the router and unless I'll put my laptop at the neighbour's I'm pretty much 'stuck' with 70/70? 

I'm not sure as well how to set up wireless interference mode, tried to google it but to be honest I'm not really sure if you meant something on my laptop or on the router? Would appreciate some clarification on that!

Thanks!!

---

### Post by tgalati4 on 2015-09-19
The Interference Robustness mode (20 Mhz vs 40 Mhz) is something that is switched on the laptop wireless card.  It acts like an FM Radio Station Local vs DX button.  By narrowing the frequency band (from 40 to 20 Mhz) you get a sharper signal and that can weed out interference.  It reduces range, but you have a strong signal to begin with.

Use a smartphone with WiFi Analyzer app and look for a cleaner channel.  In your case try Channel 4 or 13.  Don't use 11, because there are 11 other networks on the same frequency--that is bad.

I don't see a switch for it.  But you do have switches for power-saving mode.  You can play with those:

> parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


---

### Post by praseodym on 2015-09-20
Try these module parameters:
```

echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -rfv rtl8723be
sudo modprobe -v rtl8723be
```

---

### Post by matanjonas on 2015-09-21
I've tried switching our Wi-Fi channel to something less busy and so far so good, woke up this morning and the connection was good.
Thanks all for your help!

---

