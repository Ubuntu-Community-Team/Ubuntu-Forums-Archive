---
title: "How to use WPA-PSK?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by simon_pearson on 2007-05-09
Hi all,

I recently installed ubuntu and so far I am very pleased with it, except for one small problem: I am unable to get my wireless internet working.  I have a "RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)" internal wireless card.  It recognises the presence of the wireless networks, however when I enter my wireless network key it just stalls on the "Waiting for Network Key for the wireless network..." message.  Our home network uses "WPA-PSK + WPA2-PSK Security Encryption", but I do not see this listed in the network security dropdown box on ubuntu, so I'm guessing this could be the problem?  However I also tried my laptop on the university wireless network which uses WEP, and it still got caught on the "Waiting for Network Key for the wireless network..." after I entered the correct key.  Please can anyone advice me how to get my wireless internet working?

-Simon Pearson

---

### Post by simon_pearson on 2007-05-09
Any suggestions at all guys?

---

### Post by dpmccoy on 2007-05-09
Your profile didn't indicate, but are you using Ubuntu 7.04?  If so, you could be running into problems if you try to use network-manager.  Network-manager is buggy and doesn't work properly under 7.04.

I had connectivity issues after my upgrade to 7.04 from 6.10.  Everything worked fine under 6.10.  I was using knetworkmanager + ndiswrapper + WPA2 encryption.

I switched to Gnome from KDE, and now I use the wicd wireless program with ndiswrapper and WPA2 encryption.  The wireless always connects, and it never drops the connection.  This solution may suit your needs.

---

### Post by simon_pearson on 2007-05-09
Hi dpmccoy, yes I am using 7.04, so it sounds like that could be the problem.  Please could you outline exactly what I have to download/install in order to get the wireless working?  Thanks for posting.

-Simon Pearson

---

### Post by stchman on 2007-05-09
> **simon_pearson said:**
> Hi all,

I recently installed ubuntu and so far I am very pleased with it, except for one small problem: I am unable to get my wireless internet working.  I have a "RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)" internal wireless card.  It recognises the presence of the wireless networks, however when I enter my wireless network key it just stalls on the "Waiting for Network Key for the wireless network..." message.  Our home network uses "WPA-PSK + WPA2-PSK Security Encryption", but I do not see this listed in the network security dropdown box on ubuntu, so I'm guessing this could be the problem?  However I also tried my laptop on the university wireless network which uses WEP, and it still got caught on the "Waiting for Network Key for the wireless network..." after I entered the correct key.  Please can anyone advice me how to get my wireless internet working?

-Simon Pearson

I have been reading a lot of trouble with network-manager and Feisty.  I use Edgy and it works very well.  You could try "downgrading" to Edgy and wait for Feisty to get fixed.

---

### Post by dpmccoy on 2007-05-09
> **simon_pearson said:**
> Hi dpmccoy, yes I am using 7.04, so it sounds like that could be the problem.  Please could you outline exactly what I have to download/install in order to get the wireless working?  Thanks for posting.

-Simon Pearson

Download the Debian package from [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).

Install it, then uninstall network-manager and/or knetworkmanager.  Don't uninstall wpa-supplicant, however.

If I recall correctly, a 'wicd' entry will be added to the Application Menu under Internet programs. 

It has not failed me yet, and hasn't dropped the connection one time.  :)

You can add it to your startup programs as well.  If you need a tray icon, add the Edgy tray icon under the wicd directory to your startup programs...I guess they don't have a Feisty tray icon yet, but the Edgy one works fine.

Are you using the native Linux driver for your wireless card, or are you using the Windows driver w/ndiswrapper?

---

### Post by lxop on 2007-05-12
Brilliant!! I've been playing with the network manager for a while now, with no luck, but so far (cross fingers) wicd is doing great! Cheers
I might also put it out there for anyone reading, don't play with the static IP settings in wicd unless you have to use this setting, as wicd didn't let me change them back, it just kept resetting them to the on state. I had to remove the package, find the config files and delete them manually (these are in /opt/wicd) then reinstall. But good now! posting this from wireless :)

---

### Post by Jose Catre-Vandis on 2007-05-12
A quick search on the forum would have given your this execellent trhead no getting wireless with WPA=PSK going

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

