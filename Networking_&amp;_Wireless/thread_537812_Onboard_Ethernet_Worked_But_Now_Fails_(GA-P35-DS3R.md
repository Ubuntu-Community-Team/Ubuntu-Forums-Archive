---
title: "Onboard Ethernet Worked But Now Fails (GA-P35-DS3R)"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by arekmenner on 2007-08-29
Hello. I just built a new computer a while ago with the Gigabyte GA-P35-DS3R motherboard. It has an onboard ethernet cart. Now, earlier, when I was running purely on Linux, the card worked fine, right out of the box. When I got to college, however, I decided to dual boot for ease and compatibility. The first thing that happened was that I could access the internet with Linux but not Windows. So, I used Linux to go get some drivers for the card (and the other onboard cards that weren't recognized by windows). Then I rebooted to Windows and installed them.

Oddly enough, installing the drivers for the card in Windows seemed to break Linux's ability to use the very same network card. Neither the Linux LiveCD nor the Linux install (7.04) can use ethernet anymore. I do not know exactly what the onboard card is, but it uses the Realtek RTL 8168/8111 PCI-E Gigabit Ethernet NIC drivers. I located drivers for this card in Linux (obtainable at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false")) but they would not install. The poorly translated Realtek website informs me that this is because "You don’t load kernel source. Please install kernel source first."

So, there are a few possibilities that would be great. I would be willing to reboot any number of times and run diagnostic checks and paste stuff in here. If anyone could give me a way to fix it, that would be great. Also, if someone thinks it would help, if anyone could tell me how to install these drivers, that would also be greatly appreciated.

To clarify:
Ubuntu 7.04
Gigabyte GA-P35-DS3R motherboard
Onboard Ethernet uses RTL8168/8111 PCI-E Gigabit Ethernet NIC Drivers
Initially worked out of the box in Linux, once Windows Drivers installed, no longer works in Linux but does work in Windows.

---

### Post by noob12 on 2007-08-29
Try the solution here.  I think this applies to both 8168 and 8169 based cards.

[http://ubuntuforums.org/showpost.php?p=3209279&postcount=18](http://ubuntuforums.org/showpost.php?p=3209279&postcount=18)

---

### Post by arekmenner on 2007-08-29
Thank you very much! That's the problem.

I'm sorry, I tried to look for similar threads but I didn't find this one. Thank you very much, though!

---

### Post by noob12 on 2007-08-29
I'm about to post a fixit/howto for this.  It seems to be occurring pretty frequently after a new release of Windows drivers.

---

### Post by meagert on 2007-08-29
This fix works for me too!!. Thank You...You gotto love these forums!

---

### Post by noob12 on 2007-08-30
I've now posted the same material as a HOWTO here: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

