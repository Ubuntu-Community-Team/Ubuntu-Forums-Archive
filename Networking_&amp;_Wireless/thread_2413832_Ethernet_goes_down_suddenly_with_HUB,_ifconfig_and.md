---
title: "Ethernet goes down suddenly with HUB, ifconfig and shutdown hang"
date: 2019-03-02
forum: Networking &amp; Wireless
---

### Post by lupodellasleppa on 2019-03-02
Hello all

I get a strange behavior when connected on the internet via ethernet: everything works fine until my connection suddenly drops without any apparent reason.

I'm running Ubuntu 18.04.2 (been happening with .1 as well) on an Asus laptop K550J, and the ethernet cable is actually plugged in via [this]("https://www.amazon.it/gp/product/B01M7X7WQ9/ref=oh_aui_search_asin_title?ie=UTF8&psc=1") Ethernet/USB hub (on which my Logitech G402 mouse and Sharkoon Skiller keyboard are also attached).
When the connection goes down, I try ```
sudo ifconfig [ethernet_interface] down
``` but after password it will just hang on forever, ctrl+c won't even work and shutting down the terminal will tell me there are programs running in it.
Shutdown also would hang, and I cannot see the errors on screen sadly (because I'm using a monitor which goes blank on shutdown and the laptop's monitor won't show anything), but once it happened when I was using the computer without monitor attached and I think I saw some errors realted to **tlp**.

Do any of you guys have any clues cause it's a shame to hard shutdown and restart each time this happens.

Thanks

---

### Post by praseodym on 2019-03-03
Tried another USB port? Please show
```

lsusb -t
```

Maybe the current update is too high

---

### Post by lupodellasleppa on 2019-03-10
there you go:
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 5000M
        |__ Port 3: Dev 3, If 0, Class=Vendor Specific Class, Driver=r8152, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 4: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 6, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 7, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 5: Dev 7, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 7: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
```

thanks for replying

---

### Post by praseodym on 2019-03-10
What about plugging in the mouse and keyboard in other hubs?

---

