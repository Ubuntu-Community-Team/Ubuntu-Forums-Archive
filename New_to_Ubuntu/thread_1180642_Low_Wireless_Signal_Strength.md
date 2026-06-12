---
title: "Low Wireless Signal Strength"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by patioheater on 2009-06-07
I am currently experiencing the above, causing my net to run slow or even hang completely. I have Wcid installed after having the same problem with Atheros and Madwi-fi. I have tried the backports thingy but it won't install, so I was wondering would a kernal update help? I'm currently on 2.6.28.12 Update manager doesn't seem to want to let me do it
Is there a way to do it manually? If so, how?

---

### Post by Steelmourne on 2009-06-07
If you are using jaunty try installing linux backports module from the terminal. It tends to fix weak signals from Atheros wireless cards. Did any errors come up during install?

---

### Post by patioheater on 2009-06-07
This is the error with the backports command

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  linux-backports-modules-jaunty: Depends: linux-backports-modules-jaunty-generic (= 2.6.28.13.17) but it is not going to be installed
E: Broken packages

---

### Post by patioheater on 2009-06-07
:rolleyes: Sorry about the bump, but this forum moves so fast, never seen one like it lol

So any ideas about installing an updated kernel?(see first post)

Will it effect what I have now?

---

### Post by kwacka on 2009-06-07
The package you are trying to install is an empty file, to allow kernels to update without losing your wifi settings., its not installing because there is a problem with your settings.

If you open a terminal and type: ```
sudo iwconfig <device>
```

and upload the output (change <device> to your device name, e.g. eth0, ath0, eth1).

---

### Post by patioheater on 2009-06-07
bash: syntax error near unexpected token `newline'

---

### Post by kwacka on 2009-06-07
You may not have entered the command accurately

e.g. 
sudo iwconfig ath0
sudo iwconfig eth0
sudo iwconfig wlan0

anything typed after the '0' will give the error.

---

### Post by patioheater on 2009-06-07
wlan0     IEEE 802.11bg  ESSID:"XXXXXXXnetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:C4:D8:23:A9   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:F1B1-9F1F-C91A-B594-5337-D619-2088-8E0B-3BFB-9A6A-D92C-CF0B-04E4-46D4-B208-4FB8 [2]   Security mode:open
          Power Management:off
          Link Quality=34/100  Signal level:-69 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by kwacka on 2009-06-07
> **patioheater said:**
> wlan0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm  

Firstly try increasing your transfer rate (if you can).
```

sudo iwconfig wlan0 rate auto
```

Does this help?

---

### Post by patioheater on 2009-06-08
Nope. How on earth do you get to know all those commands?

wlan0     IEEE 802.11bg  ESSID:"xxxxxxxnetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:C4:D8:23:A9   
          Bit Rate=2 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:BE7E-6992-4B4C-5866-672F-E570-596F-04E1-9ACF-FBA7-B3BA-6199-5859-00FC-26FD-712E [3]   Security mode:open
          Power Management:off
          Link Quality=32/100  Signal level:-69 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by niteshifter on 2009-06-08
> **patioheater said:**
> Nope. How on earth do you get to know all those commands?

The man utility. Example:
```
man iwconfig
```

man uses the less utility (it paginates a file - shows a screenful at a time) and has built-in help (type an h) - but arguably the most reached for commands are for searching. While reading a man page /string will search forward for string, ?string searches backward, n move forward to next string, N move backward.

But how does one know which command to use or that might be useful? Use the apropos command. Try this:
```
apropos wireless
```
and you'll see a list of commands useful for wireless stuff.

Want to use the GUI to show man pages? Use Ubuntu's Help Centre: just type man <command> in the search box.

---

### Post by patioheater on 2009-06-12
Seems to have been so much better since I changed wireless channel, tho it can't be interference as I'm not exactly innundated with other networks

---

### Post by carcar1 on 2009-06-12
The madwifi driver for any atheros chipset is just low.  The ubuntu driver is just doing this for some reason.  Ndiswrapper was a little better.  I have the oh so famous atheros ar5007eg and ar5006eg so I would know.

---

