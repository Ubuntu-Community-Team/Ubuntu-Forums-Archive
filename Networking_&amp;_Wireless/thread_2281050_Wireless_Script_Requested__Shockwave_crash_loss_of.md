---
title: "Wireless Script Requested:  Shockwave crash loss of network"
date: 2015-06-04
forum: Networking &amp; Wireless
---

### Post by mchain on 2015-06-04
Attached below find wireless scripts requested.

Wireless-info.txt had to be split to attach.

Do you need the script run when I have no network, local or internet?  Cannot view router page when Shockwave crashes, nor do I have internet access.  Almost seems as if a firewall block rule is in effect.  Yet, the usb dongle is still connected and the network icon at the top is showing connected.

 Rebooting has always fixed this issue.

If I do not run shockwave, issue does not appear.

Thanks.

---

### Post by jeremy31 on 2015-06-04
Go into Network Manager, select your wifi connection and change IPv6 to ignore, then reboot

---

### Post by mchain on 2015-06-05
@ jeremy31,

Followed instructions, ran shockwave flash, router page and internet access lost after a few minutes.  No network available even tho the wireless connection is live and still connected.

If I do not run shockwave, then internet connection is good and remains active.  Something else is disabling data streaming, but don't know what.  Only known trigger so far is running shockwave.  Normal surfing does not trigger loss of data streaming.

Need the wireless script run after the connection goes down?  I've saved the terminal code to do so.

Bitdefender antivirus updater always reports server address is incorrect when this happens, so cannot update definitions.  Rebooting fixes issue.

Thanks.

---

### Post by jeremy31 on 2015-06-05
I think a big part of the issue is the wifi adapter that needs ndiswrapper to work.  Changing the wifi router encryption to WPA2 only or WPA2-PSK/AES might help but I had one of those Netgear adapters and didn't have much luck keeping it going in Linux and it isn't easy troubleshooting them either.  I have no problems with my Atheros and Intel internal wifi cards in my laptops but I have a TP-Link TL-Wn722n 150 Mbps that works great with no issues

Also, I didn't realize at the beginning that you were the one to report this on linux mint forum

---

### Post by mchain on 2015-06-07
Hi jeremy31,

Thank you for your support.  :D

Yes, I initially installed LinuxMint Cinnamon and had the same exact issue, so reported such at their forum.  It's too bad support there was non-existent, so I moved over to 14.0.02 using the same SanDisk Cruzer 16 GB flash drive, knowing that support over here was likely better as I've run Heron in the past (wired connection only).  I know one is not supposed to do that, but without support what is one to do?

Looks as if the wireless hardware needs to be changed to something automatically supported by Ubuntu and without the need for ndiswrapper install, which has unfortunately turned out to be somewhat problematic in use.  

Is TP-Link TL-Win722n 150 Mbps available retail and compatible for Win 7 soon to be Win 10?  Desktop Mini-tower HP/Compaq DX2300 (six) USB 2.0 ports?  I take it this hardware is supported by Ubuntu out-of-the box?

Invaluable information, exactly what I was looking for.  

BTW, what if anything, do I need to do to completely uninstall the ndiswrapper and information about the NETGEAR N300?

Thank you.  :D:D:D

-mchain

---

### Post by chili555 on 2015-06-07
Here ya go! [http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG](http://www.amazon.com/TP-LINK-TL-WN722N-Wireless-Adapter-External/dp/B002SZEOLG)

---

### Post by mchain on 2015-06-11
@ chili555,

Thank you.  Will go and get the new usb wireless adapter.  

Would I use something like synaptic to remove ndiswrapper since I wouldn't need it?

---

### Post by mchain on 2015-07-30
@chilli55,

Two months later, your proposed suggestion to change out the NETGEAR N3100 usb wireless stick for the TP-LINK adapter has worked exceptionally well.

Turns out NETGEAR was also problematic for Windows too.  Towards the end, had to continually reset the wireless connection to clear up issues with the connection.  Have no such issues with TP-LINK and none for the foreseeable future.  It just works!  Bought mine at Micro-Center locally and no issues of any kind on either Ubuntu or Windows.

Now, if we could just get the native disk benchmarking in Ubuntu to work without presenting a halt error, everything would be just dandy.  But that is off-topic here, so we'll just leave that alone.

Cheers!  :D

-mchain

---

