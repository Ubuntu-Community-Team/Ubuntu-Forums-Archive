---
title: "Problem with Feisty and HP nx7300 (Dell Wireless 1390 WLAN Mini-PCI Card)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by uba704 on 2007-06-19
Hi!

I have problem using the wireless network on my HP Compaq nx7300 laptop. I am running the Feisty 7.04 Kubuntu live CD. When typing "lspci" I see among other things this line:

10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

which I assume is the wireless network card. When clicking on KNetworkManager icon I see "Wireless Networks: No wireless network found.". When clicking on "Manual Configuration" I see that eth1 (Wireless Network Device) has state "Disabled". When I mark that line and click "Enable Interface" it says "Enabling interface eth1" for about one second and then everything looks like before (i.e. eth1 has state "Disabled"). Any idea what might be wrong here? Under Windows Vista on the same computer the wireless network works perfectly.

When I compare with an IBM ThinkPad T43 laptop and run the same Feisty 7.04 Kubuntu live CD I see my network listed when I click on the KNetworkManager icon, but on my HP Compaq nx7300 I see "No wireless network found.". To me it seems like Feisty recognize my network card but can't use it of some reason.

Thanks for any idea about what to do!

---

### Post by chili555 on 2007-06-19
Broadcom cards want to load firmware which is not installed by default; it's proprietary, that is, not open source. I suggest you check here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by Ayuthia on 2007-06-19
If you haven't installed bcm43xx-fwcutter or ndiswrapper, you will need to do this.  

The easiest of the two is bcm43xx-fwcutter where you will just need to type 'sudo apt-get install bcm43xx-fwcutter' and if you have access to the internet via a wired connection, you can have it select the driver for you.  The downside to it is that in some cases, it does not connect faster than 11Mb.

The other route is ndiswrapper.  You can try this route:
[http://ubuntuforums.org/showthread.php?t=193728](http://ubuntuforums.org/showthread.php?t=193728)
The only thing that might be missing is the blacklisting of bcm43xx in /etc/modprobe.d/blacklist.  Just check the file after doing the steps and see if 'blacklist bcm43xx' is there.  If it is not, add it.

---

