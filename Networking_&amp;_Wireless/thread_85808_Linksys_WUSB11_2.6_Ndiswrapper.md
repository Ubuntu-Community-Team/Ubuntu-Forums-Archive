---
title: "Linksys WUSB11 2.6 Ndiswrapper?"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Keshyden on 2005-11-03
I have an old Dell Optiplex GX1 that I put Ubuntu on a few days ago. I am having one heck of a time getting my Linksys WUSB11 card working.

I first tried the at76c5032 drivers because I saw most people with that card had used that driver set.  That didn't work. I keep getting everything set and getting to run make and make install and it would output a loooong list or errors and end with a Error 2.

After getting tired of messing with that, I decided to try ndiswrapper.  I hooked up the Optiplex to my router (via cable) and downloaded a bunch of a packages, one of which was ndiswrapper.  I also installed the GUI for ndiswrapper which I found here:

[http://ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper)

Then, I downloaded the latest driver from Linksys.  I load the driver through the GUI and everything looks good. When I go to System > Administration > Windows Wireless Drivers it says under netusb (the driver file) that the hardware IS present.

When I go to configure my network, I set up a static IP and make sure the IPs are all right.

When I activate the connection, nothing happens.  My connection details are SSID=keep_out
Channel=11

Is there a special place to put in channel or something. I have unplugged/replugged, rebooted, and tried other drivers and nothing is working. But it should because it detects the hardware.

Any help would be appreciated!

Thanks for listening,

Keshyden :p

---

### Post by Keshyden on 2005-11-04
up

---

### Post by Lambert on 2005-11-04
If you open a terminal and type

```
iwconfig
```

post the output here

Also post output from

```
ndiswrapper -l
```

When you type iwconfig you should see your device and channel. If it's not 11 then to change channel type

```
sudo iwconfig <eth0> channel 11
```

Change eth0 to whatever your card is identified as.

Is your network encrypted with wep or wpa at all?

---

### Post by Keshyden on 2005-11-07
Here is the stuff.. Sorry I took a few days.

iwconfig...
```
wlan0     IEEE 802.11-DS  ESSID:"keep_out"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ndiswrapper -l...
```
Installed ndis drivers:
netusb  driver present, hardware present

```

No, I have no WEP or other encryption.

Here's something interesting...

I reinstalled Ubuntu today and hardwired it to install the ndiswrapper utils and all that.  Then I ran it ndsiwrapper was fine.  Went to configure network, set static ip and enabled the wifi/disabled the ethernet.  Tested out firefox. Woah! internet. then to make sure, unplugged cable. Woah! still internet.

Shut it down, took it up stairs, booted up Uh-oh! No internet.

Now I am here.

Thanks.. :confused:

---

### Post by Lambert on 2005-11-07
If you type in a terminal
```
lsmod
```

You should see ndiswrapper in the list. If not type

```
sudo modprobe ndiswrapper
```

Go to System>Administration>Networking and activate

If that works go back to the terminal and type

```
sudo ndiswrapper -m
```

This will set it so the module loads at boot time.

---

### Post by Keshyden on 2005-11-07
typed in lsmod and under module the first one is ndiswrapper.

wasn't working so i modprobed it.

one thing i did notice... before i had modprobed it, firefox would give me acould not connect to host w/e error instantly, and after i modprobed no error showed up. it just kept loading but nothing happened.

---

### Post by Keshyden on 2005-11-08
up

---

