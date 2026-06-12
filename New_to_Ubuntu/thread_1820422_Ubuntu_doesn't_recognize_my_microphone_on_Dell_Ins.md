---
title: "Ubuntu doesn't recognize my microphone on Dell Insprion 1545"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by HunterDX77M on 2011-08-07
I have an integrated microphone on my laptop that I was able to use when I was using Windows XP. For what ever reason, Ubuntu can't recognize that I have a microphone. How can I fix this?

System info:
Ubuntu 11.04 (Natty Narwhal)
Using Intel HD Audio IDT 92HD71

I am not sure what other information is need to solve this problem (please ask).

---

### Post by SalHelder on 2011-08-07
Try this, run:

gnome-volume-control

In the input tab check if your mic is there. If so after selecting it it should give you a reaction when you talk or make a sound.

---

### Post by HunterDX77M on 2011-08-07
> **SalHelder said:**
> Try this, run:

gnome-volume-control

In the input tab check if your mic is there. If so after selecting it it should give you a reaction when you talk or make a sound.

Thanks, but I've already tried this. Actually this is how I discovered the problem, because when I first went there, it showed nothing in the section where I would select a microphone.

---

### Post by SalHelder on 2011-08-08
Do you get any output of this command:

ls /dev/audio*

?

---

### Post by HunterDX77M on 2011-08-08
> **SalHelder said:**
> Do you get any output of this command:

ls /dev/audio*

?

It's telling me that no such file or directory exists.

---

### Post by SalHelder on 2011-08-08
Just in case it doesn't work what I'll suggest now, paste the output of lspci. Anyway, try running:

gstreamer-properties

Set all to ALSA, and then run:

alsamixer 

See if you can spot your mic here now. (use the right arrow on the keyboard)

And then go to gnome-volume-control and see if it shows up there now.

---

### Post by HunterDX77M on 2011-08-08
Okay, I got a little lost after I went to the mic section on alsamixer. Please see the screenshot attached and you'll see what I got (and maybe you can make some sense of it, because I can't). 
:confused:
But the mic didn't appear in the list on the Gnome volume control window, so I don't think it worked (I mean changing the mic the ALSA).

Question: Do I have to change only the mic to ALSA or everything (Output audio/video)? Because everything else is working fine.

Output of lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Intel Corporation WiFi Link 5100


```

---

### Post by SalHelder on 2011-08-08
Actually you should change all to ALSA you can revert that easily if something goes wrong anyway. And you should be able to see more, keep going to the right (there's probably more hidden in the right side) you see more devices. And then use the up and down keys to adjust volume.

---

### Post by HunterDX77M on 2011-08-08
> **SalHelder said:**
> Actually you should change all to ALSA you can revert that easily if something goes wrong anyway. And you should be able to see more, keep going to the right (there's probably more hidden in the right side) you see more devices. And then use the up and down keys to adjust volume.

There is nothing further to the right, and I changed both the input and output audio to ALSA.

---

### Post by SalHelder on 2011-08-08
What happens when you press F4 in alsamixer?

---

### Post by HunterDX77M on 2011-08-08
> **SalHelder said:**
> What happens when you press F4 in alsamixer?

Here is a screenshot. What does it mean?

---

