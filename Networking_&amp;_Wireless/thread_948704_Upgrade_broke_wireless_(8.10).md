---
title: "Upgrade broke wireless (8.10)"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by mojoguy on 2008-10-15
Running Intrepid Ibex (8.10) on a Dell e1505 laptop.  Today's updates wiped my wireless.  Ifconfig only shows eth0 and lo interfaces.  Needless to say, I can't connect to any wireless networks.  Though today's updates did include updates to kernel 2.6.27-7 (generic), booting with an earlier kernel does not help matters.

Anyone have any suggestions as to what to do/how to begin resolving this?  

Thanks!

---

### Post by rebound87 on 2008-10-15
Same problem here, but on an Asus F6V notebook.

I have no solution yet, but i can give some more details that might help solving the problem:

Output of lspci:
> 03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

Output of iwconfig:
> wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point:   Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I try to bring wlan0 up:
> SIOCSIFFLAGS: No such file or directory


And some lines from /var/log/messages
> Oct 15 19:29:06 sirion kernel: [   17.919726] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Oct 15 19:29:06 sirion kernel: [   17.919728] iwlagn: Copyright(c) 2003-2008 Intel Corporation
Oct 15 19:29:06 sirion kernel: [   17.929538] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 15 19:29:06 sirion kernel: [   17.929622] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Oct 15 19:29:06 sirion kernel: [   17.962096] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct 15 19:29:06 sirion kernel: [   17.962782] iwlagn 0000:03:00.0: PCI INT A disabled

---

### Post by virtuoso88 on 2008-10-15
Same with 8.1 on a thinkpad W500 and the Intel 5300 card.

---

### Post by marcelo.waisman on 2008-10-15
same with HP Compaq nx8220, guess its a general problem

---

### Post by StatusWoe on 2008-10-15
Hey Guys,

If I remember correctly this issue is caused by kernel updates not automatically picking up the kernel modules you need to enable your wireless cards. 

I have an atheros card and the instructions here seem to work when this happens. In any case it's likely a module not installed.

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)



Best of luck,
Brent

---

### Post by mojoguy on 2008-10-15
FYI: Running update again (later in the day) restores everything to working order.  Mind you, this only helps if you can plug in to a connection somewhere...

---

### Post by brandon moore on 2008-10-15
same here on Toshiba u205-s5057 running intrepid ibex. i have the intel PRO 3954ABG card.

edit: make that the 3945abg

---

### Post by oddworld on 2008-10-15
I have intel 3945abg. Same thing happened. Let me know what you find out.

---

### Post by randizzle on 2008-10-15
Am I the only one experiencing this on Hardy? There seems to be no available system updates for me to do, as intimated two posts up.

I am on a System76 Sabel Performance with a Hawking HWUG1 Wireless-G USB

---

### Post by lochiel on 2008-10-16
Same problem here on kernel 2.6.27.7.12 after update.
Disabled Ubuntu Atheros restricted driver (Now doesn't even show up as available). Installed madwifi as per related thread - no joy.

So if I need wifi I have to boot into kernel 2.6.27.4 where Atheros driver shows as available and configured but flgrx driver shows as deprecated but available for 2.6.27.7.

I guess you can't have it all working at once :)

---

### Post by brandon moore on 2008-10-16
My system recognizes the Intel 3945abg card, but does not pick up any essids with NetworkManager or wifi-radar.

Any ideas about a fix for this?

---

### Post by huangweiqiu on 2008-10-17
same here ,Dell XPS1210, wired

---

### Post by brandon moore on 2008-10-17
The solution for me was this: I downloaded linux-firmware_1.1_all.deb from here: [http://packages.ubuntu.com/intrepid/all/linux-firmware/download]("http://packages.ubuntu.com/intrepid/all/linux-firmware/download")

Then I installed it, rebooted and magically my wireless started working. I'm doing my partial upgrade to the newest version of Intrepid Ibex now. 

:):):)

---

### Post by Andre_Eisvogel on 2008-10-18
> **brandon moore said:**
> The solution for me was this: I downloaded linux-firmware_1.1_all.deb from here: [http://packages.ubuntu.com/intrepid/all/linux-firmware/download]("http://packages.ubuntu.com/intrepid/all/linux-firmware/download")

Then I installed it, rebooted and magically my wireless started working. I'm doing my partial upgrade to the newest version of Intrepid Ibex now. 

:):):)
Thnx, that did the job. :) thumbs up!
After ```
sudo aptitude install linux-firmware
``` and a reboot my wifi was up and running again

---

### Post by ions on 2008-10-24
> **Andre_Eisvogel said:**
> Thnx, that did the job. :) thumbs up!
After ```
sudo aptitude install linux-firmware
``` and a reboot my wifi was up and running again

Thank you. :)

---

### Post by SLeepdepD on 2008-11-06
I have a Compaq R3000 laptop.  Wireless worked with 8.04, but didn't with 8.10.

I followed this and it works now.  Thanks a lot.

---

