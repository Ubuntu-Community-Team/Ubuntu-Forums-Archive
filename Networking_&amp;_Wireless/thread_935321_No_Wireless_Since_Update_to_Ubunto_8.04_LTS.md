---
title: "No Wireless Since Update to Ubunto 8.04 LTS"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by Aziza Tullia on 2008-10-01
Hi! Newbie here. I had Ubuntu 6.x for a year, no problem. Then I did a BUNCH of updates, winding up with Ubuntu 8.04 LTS. Ever since, my Network Manager detects ZERO wireless networks (I have tried several). With the Ubuntu Help Center, I was able to figure out the problem (I think), but there was no suggestion of how to solve it. 

cf.
"Troubleshooting 3.2.3 Check device is on"

I enter 
<sudo lshw -C network>
to see that while my Network controller and Ethernet interface seem fine, to my untrained eyes, my Wireless interface is clearly marked 
<*-network DISABLED>.

Sadly, the help guide only then offers a suggestion for "If the device is turned on", suggestion nothing for when, as in my case, the device is turned off. 

Long story short, how can I **ENABLE MY WIRELESS INTERFACE**?

Much Thanks!

---

### Post by pastalavista on 2008-10-01
Right-click on the network icon in notification panel and see if it has "enable wireless" as a choice. Then check System > Administration > Hardware Drivers to see if they're enabled there. If they are enabled, disable them, restart, and then enable them and reboot again.. that's fixed mine on several occasions. Also, does your computer have a physical switch to manually turn the wireless on and off? Mine does and once I didn't notice it was in the off position and I thought there was something wrong with Ubuntu. Spent too much time checking all the wrong things. Computers don't make us smart, they just let us feel like we are sometimes... make us feel stupid sometimes too.

---

### Post by Aziza Tullia on 2008-10-01
Thanks for your reply! 

I found the Hardware Drivers management window. And I tried to click on the Enable button for the Broadcom B43 wireless driver. When I did so, my system tried to Download Package Files, and then came up with an error message...

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_311-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_311-1_i386.deb)
Could not resolve 'archive.ubuntu.com'

Seems to me that my computer is trying to access files on the internet in order to enable the wireless- which is inhibited by the fact that wireless is not enabled, and therefore the system is unable to access any internet files? Catch 22!!!

Hmm... What to do?

---

### Post by Aziza Tullia on 2008-10-01
Further Information:

In the window where I am asked to confirm that I want to enable the Boradcom B43 wireless driver, there is this message:

While this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware.

So does that mean that I'm missing the firmware to enable/run this driver?

And by the way, what is firmware?

Thanks!

---

### Post by pastalavista on 2008-10-01
You could download the [.deb file]("http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_311-1_i386.deb") above and transfer it to your Ubuntu and double-click to install. Deb files are easy. Firmware is "embedded software" that makes a device work. Drivers are the software that communicates to the firmware at boot. Your firmware is probably OK unless it has been exposed to a strong power surge or magnetic field.

Good-luck.

---

### Post by Aziza Tullia on 2008-10-06
humph! 

i finally found time to follow up on this problem, and when I tried to track down this file that my computer wants to "fetch" off the internet, it comes up as a FILE NOT FOUND. When entered directly as a url, and when searched on google. 

Oh woe! What to do?!

---

### Post by pastalavista on 2008-10-06
I just tried to download it (the link you gave in your first post and copied by me in my answer) and it worked fine. Watch for typos... right-click the link below and save target as:

[http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_311-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_311-1_i386.deb)

edit: ok, I tried the package and it is corrupt. It must have been updated. try to find it at this site

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by Aziza Tullia on 2008-10-06
Please excuse my prior hastiness. That recent moan was not very well researched... This one is:


So I found the necessary files on the Ubuntu Archives. I downloaded them onto my friends computer, transfered them to a CD, and tried to install them on my computer. 

Firstly, I was informed that said package was already installed. But since it hasn't been working, I tried to install it again. 

And, ho! It reads as such:

Failed to install package.

...Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--install):
  subprocess post-instillation script returned error exit status 1

Voila! [accumulating frustration ensues]

Any ideas to further my current dead-end plan of action?

Thanks!

---

### Post by Aziza Tullia on 2008-10-06
[Sorry about the lag]

I checked out that site recommended, BerliOS Developer. I don't see the exact version I'm looking for on their download list. (I think I need b43-fwcutter_011-1_i386.deb

All their offerings end in .bz2, and they only go up to 09... I think I need 011.

Any suggestions?

Thanks!

---

