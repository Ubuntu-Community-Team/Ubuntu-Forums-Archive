---
title: "acer aspire one wireless"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by kornelix on 2008-12-02
When I first insalled 8.10 wireless worked. Not any more, presumably because of updates downloaded a few days ago. I went hunting in the forums and found lots of similar complaints. I have tried the recipes found in community docs but they did not work (go back to ath_pci driver in place of newer ath5k). I tried booting to older kernels and that did not work. I tried going back to 8.04 and that failed too. The closest I got was using ndiswrapper and the windows driver (device AR5BXB63). This combination was at least showing available WLANs and trying to connect, but failing (the Linux drivers had not even shown any wireless device to connect with). The dmesg output: "setting AP mac address failed".

Details of the most "hopeful" combination:
  *  ath_pci and ath5k both included in /etc/modprobe.d/blacklist
  *  ath5k included in /etc/modules (else ndisgtk says "no hardware")

Any advice? Wait for another kernel? Buy a different computer?

---

### Post by kornelix on 2008-12-07
I found the following black magic works for the Acer Aspire One and Ubuntu 8.10.

Get the Windows NT driver for the atheros chip AR5BXB63.
I found it here with a google search: 
[http://rs334.rapidshare.com/files/122151469/atheros_ar5bxb63_driver.exe](http://rs334.rapidshare.com/files/122151469/atheros_ar5bxb63_driver.exe)

Using Windows NT, run the downloaded .exe file and it will 
unpack the contained driver files into a new directory.

Move these files to someplace handy in your Ubuntu system.
(I used a USB stick).

In Ubuntu 8.10, do the following:

[LIST]
[*]add ath_pci and ath5k to /etc/modprobe.d/blacklist
(this disables two most recent Linux atheros drivers)
[*]add the ndiswrapper package: ndisgtk 
(2 prerequisite packages will also be added)
[*]use the menu:  system > admin > windows wireless
[*]press "add new driver".
[*]browse and select net5211.inf from the Windows driver files
[/LIST]
 You may be able to select a wireless network and connect.
Click on the panel network icon. If not, reboot and try again.

This same procedure also works with Ubuntu 8.04, but the resulting 
wireless connection will be lost after a reboot. If you **power off** and
reboot, the connection comes back. At least that is what I now see. 
Strange.

---

