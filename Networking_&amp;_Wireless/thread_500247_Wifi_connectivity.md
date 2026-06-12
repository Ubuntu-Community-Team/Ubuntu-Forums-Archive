---
title: "Wifi connectivity"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by RxRated on 2007-07-13
I have a Toshiba laptop with a realtek 8180 mini pci wifi card.  The computer connected fine with Edgy, but after upgrading to Fiesty, it will not.  I edited the blacklist file and have the drivers working.  Network manager shows my essid in the choice of wireless connections.  I tried disabling all security as well still no connect.  After about 2 hours of rebooting, and attempting to connect, it DID!!  It asked for a keyring password to save my security password, etc.  So, I thought I'd reboot to see if it would re-connect.  Upon booting, it again asked for my network keyring password, but will not connect.  I am VERY confused as to why it connected once. (I know it was connected because I surfed the net, and downloaded a file).  I connect immediately with wired ethernet.  

Thanks in advance to anyone willing to help,

Steve

---

### Post by jml on 2007-07-13
Here is a thread I found searching the forum with the terms realtek 8180.  Hope it is helpful.

[http://ubuntuforums.org/showthread.php?t=2681&highlight=realtek+8180](http://ubuntuforums.org/showthread.php?t=2681&highlight=realtek+8180)

Joe

---

### Post by RxRated on 2007-07-13
OK!  This is a VERY strange glitch.  After failing to connect, I tried the option "connect to other wireless network" in network manager.  I tried creating an essid the same as mine, but with an x at the end, because of a post I'd read here about realtek lan cards not reading the essid correctly.  It tried to connect and immediately failed.  I then tried to connect to my network which was on the roaming list with the correctly spelled essid and it worked!  I have rebooted 3 times and the glitch follows the same pattern.  It will not connect, I try manually creating a wireless account which fails, then try again to connect to my account and it works????

Any ideas what could be causing this?

---

### Post by jml on 2007-07-13
That one stumps me. It may be a configuration issue.   Hopefully someone else will have an idea.

Joe

---

### Post by RxRated on 2007-07-13
It seems as if it will not transmit, when I choose a network from the list, but when I try the connect to other wireless network, it turns it on.  The icon that shows when it's trying to connect consists of 2 dots with a blue arrow circling around.  Neither dot lights up when I select my network.  Then when I try the other network option, the bottom dot lights green.  After it fails, I select my network from the list and the bottom dot immediately turns green, followed shortly by the top one turning green and it then changes to a row of bars representing a signal strength and it is connected.

Very Strange.

---

