---
title: "Cisco AM10 USB wireless in Ubuntu/Raspberry Pi"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by adabc on 2015-05-02
[FONT=system][COLOR=#ff0000]Warning: PLEASE DO NOT TRY THIS IF YOUR USB WIRELESS CARD IS NOT CISCO AM10[/COLOR]
Solution:
1. Download usb-modeswitch from [http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)
    note: if you get usb-modeswitch from "sudo apt-get install usb-modeswitch", 
         you will get old one and it won't work!
[COLOR=#000000]2. **sudo apt-get install tcl tcl-dev libusb-1.0**[/COLOR]
3. [B][COLOR=#333333]tar -xf [/COLOR]usb-modeswitch-2.2.1.tar.bz2
[/B]4. [B]cd usb-modeswitch-2.2.1
[/B]5. **make**
6. [B]sudo make install
[/B]7. [B][COLOR=#000000]sudo usb_modeswitch -v 1307 -p 1169 -L
[/COLOR][/B]8. [B]ifconfig
[/B]9. if it work, you will see your wlan0!

Actually I did this in Raspberry Pi(I think the ubuntu will also work). After I google this issue, I end up with this [closed thread]("http://ubuntuforums.org/showthread.php?t=1808690&highlight=am10"). After I did my 4hrs research, I finally get it worked. I should thank ohmysql(this guy had lot of enthusiasm to get this done[/FONT][FONT=system]) and usb-modeswitch([thread between ]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=635&start=45")[/FONT][[FONT=system]ohmysql and Josh, the author of usb-modeswitch[/FONT]]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=3&t=635&start=45")[FONT=system]). This won't be possible without them. [/FONT]

---

