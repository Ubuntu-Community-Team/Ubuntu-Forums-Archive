---
title: "Wi-Fi No-longer working &gt; Network manager also missing icons &gt;"
date: 2020-11-21
forum: Networking &amp; Wireless
---

### Post by GeordieJedi on 2020-11-21
Hi there guys.

I was looking for a bit of help with a quirky issue that I've been
experiencing, please.

I am currently accessing the internet through my mobile phone via a hotspot/tethering.

I can tether / hotspot wirelessly if I use my laptop.
However ATM I have to use the charging/data cable if I want to tether via my main desktop PC

I'd much rather use my desktop PC to work from, as its much more ergonimicaly set up.


I have x2 wireless USB adabptors
1. Linksys WUSB54GC v1 802.11g Adapter
2. Sony /UWA-BR100 802.11abgn Wireless Adapter [Atheros AR7010+AR9280]

When I type lsusb I get the following response:

1. Code: ```
lsusb
```

Output:
```
Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73] 
```


2. Code:```
lsusb
```

Output:
```
 BUFFALO INC. (formerly MelCo., Inc.) Sony 
UWA-BR100 802.11abgn Wireless Adapter [Atheros AR7010+AR9280]
```


Troubleshooting:

1. I've dowloaded and intalled the correct drivers for both USB adaptors.

2. The OS recognises the USB adaptors (when they are plugged in)

3. I've tried various power cycyles, changing to different USB sockets buses - (without success)

4. The ironic thing is, this was working (for a couple of days) before it stopped.

I believe that I (may) have inadvertently caused this.

I was going to (physically) swap USB adaptors. To do some quick speeds tests on each of the USB adaptors

Using KDE network manager, there were some icons / click boxes for Wireless adaptors and aeroplane mode.

I chose the de-select wireless adaptors (thinking that it would un-mount) the USB stick,
and allow me to insert the different wireless adaptor more easily.

Ever since then, I cannot use the USB adaptor to connect to my phone to access the internet.

In-fact, the actual icon/click box for wireless networks on KDE network manager has totally vanished.
However the icon/click box for Aeroplane mode is still there and available on network manager

I've also ran the rfkill command to clear any soft or hard blocks for
wireless adaptors, however this also has not resolved the issue, or brought back the icons
to let me use my USB wireless adaptors.


TIA for any help or advice.

Useful details:

OS: Ubuntu 18.04 LTS
OS type: 64-bit

DE: KDE 5.12.9
Kernel: 4.15.0-99-generic

---

### Post by praseodym on 2020-11-21
Try
```

sudo systemctl restart NetworkManager.service
```

---

### Post by GeordieJedi on 2020-11-21
Hi there, praseodym. Thanks for responding

I've just tried that.
The command completes successfully

However I am still unable to connect to my phone via Wi-Fi
The icons / click boxes to enable Wi-Fi are still missing from the network control centre.

---

### Post by jeremy31 on 2020-11-21
Check ```
cat /var/lib/NetworkManager/NetworkManager.state
```
If networking or wireless entries say false change them to true

---

### Post by GeordieJedi on 2020-11-21
Hi jeremey31

I did as you asked.
The text / config file was set to false.

I opened up the file in gedit as sudo.
Changed the state to "true" and saved the file

Re-tried to connect to the phone via Wi-Fi = Not able to

Re-booted the PC, checked the file again, it has been re-set to false.

I've re-edited, and saved the file, and rebooted twice now with the same result
The state keeps flipping back to "false"

---

### Post by jeremy31 on 2020-11-21
You might have to change the Network states in Network Manager then.  I am not sure why you needed to install drivers for that BUFFALO INC. (formerly MelCo., Inc.) Sony 
UWA-BR100 802.11abgn Wireless Adapter [Atheros AR7010+AR9280] device as that should be supported in the kernel

---

### Post by GeordieJedi on 2020-11-28
OK, do you know how I would go about doing that please ?

---

### Post by jeremy31 on 2020-11-28
In terminal ```
nmcli networking on
nmcli radio wifi on
```
See if that gets it working

---

### Post by GeordieJedi on 2020-11-28
OK, I ran both of those commands.

They execute properly (without any failures)
However, neither USB adaptor is providing a Wi-Fi connection.

Re-typing ```
lsusb
```
Both devices are recognised or seen by the kernel

However (as another test) I logged into Gnome DE and retested the adaptors
and neither one was recognised by the OS / DE

But typing lsusb does show them as devices connected to the computer.

---

### Post by jeremy31 on 2020-11-28
Can you run the wireless script and post results

---

