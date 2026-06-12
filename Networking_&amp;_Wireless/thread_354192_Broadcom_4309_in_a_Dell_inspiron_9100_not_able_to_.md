---
title: "Broadcom 4309 in a Dell inspiron 9100 not able to get wirless LAN up and running"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by rexbanner3 on 2007-02-05
The title pretty much states my pronlem. I have a dell inspiron 9100 with a broadcom 4309 chipset. I have tried fwcutter and ndiswrapper several times, but am not able to get it to work. when i do iwconfig it shows up as eth1 but will not detect my network. Any advice or am i stuck with the ethernet cable until a native driver is written?

---

### Post by Metaljaz on 2007-02-05
If you haven't already read through the below threads and see if you missed something:


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by rexbanner3 on 2007-02-06
Thank you for your reply. i have read through both of them again verbatim and followed them. I am still not able to connect or even get a signal from my my wifi network, Any other advise would be appreciated,

---

### Post by Metaljaz on 2007-02-08
I to am using a Dell Inspiron XPS with built in wireless broadcom 43xx. I haven't really tried getting mine to work because i am using a wireless pci card. I had bookmarked the links i sent you so i will have them when i take on the task. since i am able to connect with this card i may not fool with the broadcom 43xx.
Two other links to try. Let me know how you make out.

[http://www.linuxquestions.org/questions/showthread.php?t=462995](http://www.linuxquestions.org/questions/showthread.php?t=462995)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by TheFourthOne on 2007-02-11
Hey!

I have been looking all over the place, reading tuts trying different things with no success. I am running a Dell Latitude D600 with the BCM 4309 chipset. I DID FINALLY get it working!
Go [here]("http://products.wildpackets.com/?v=bs2h5ampbyiw0049&s=1") that should download the 4309 driver (it is the driver specifically for the 4309) open it up and copy the .info and the .sys file to your desktop. then go [HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset")
and download the file they offer (keep this page up too, it's the one you'll use to follow directions) after you download the file open it up (don't extract) and copy the 32 bit file to the desktop. Open that file up and replace the .info and .sys files inside with the ones you have on your desktop. then replace the 32 bit file into the .tar.gz file you downloaded and continue following the directions in the ubuntu starter guide. Note this is for 32 bit, but I think if you find the 64 bit driver you could follow the same principal. Also I'm running Edgy, but if ndiswrapper works in other distros I don't see why it wouldn't work for anyone else. Hope it helps! :)

---

