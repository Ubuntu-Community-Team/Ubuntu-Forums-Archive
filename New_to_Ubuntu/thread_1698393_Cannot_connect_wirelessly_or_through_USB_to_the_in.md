---
title: "Cannot connect wirelessly or through USB to the internet."
date: 2011-03-02
forum: New to Ubuntu
---

### Post by stephenkrogh on 2011-03-02
Hi guys. I am running Linux Mint Julia. I am posting my question here, because my understanding is that Julia is based on Ubuntu. My problem is that I cannot connect to the internet. I have an HP Pailion dv2000 laptop, and I was running it with the wireless internet toggled off to save battery power. WHen I toggled the wireless back on, the computer no longer read it. It thinks it is still toggled off. This in itself might indicate simply a hardware problem, except that when I plug my computer directly into the USB hookup to the router, it also fails to work (interestingly, it does work if I plug in the ethernet connection). This leads me to believe that perhaps my OS is not communicating with the hardware. Any suggestions? Thanks!

---

### Post by vivek.pandey on 2011-03-02
try this type lsusb in terminal and see whether your usb device is being listed over there or not

---

### Post by stephenkrogh on 2011-03-02
It looks like it reads it. I can move things onto external hard drives through my usb. Also, a lot of info popped up about the drive when I typed it in.

---

### Post by vivek.pandey on 2011-03-02
hey what i meant was if i am getting right you are trying to coonect through a usb modem  as your title of the thread suggests right?

---

### Post by stephenkrogh on 2011-03-02
That's right. More distressingly, though, I cannot connect through wireless either. The only way I can connect is through ethernet connection.

---

### Post by vivek.pandey on 2011-03-02
k so i was referring to that device only see if it is listed on typing lsusb command.. next thing right click on network manager applet and check whether the type of connection you are trying is ticked (or checked) ie say if your connection is broadband it is checked or not...many time it happens that it automatically gets unchecked

---

### Post by stephenkrogh on 2011-03-02
Ok, so USB is being shown. When I right click on the network applet, "enable networking is checked. But, "enable wireless" cannot be checked, it isn't even highlighted. I suspect it is because the computer isn't recognizing that I've toggled the wireless connection (on these hp pavilions, you have a toggle on the front of the computer, which allows you to turn wireless on or off. A light indicates if it is on. Though I've toggled it on, the light is not on.

---

### Post by mick8985 on 2011-03-02
Go into your bios and deactivate the switch on the front. (You can do this on dells at least)
Then you'll know whether it's a problem with the switch.

---

### Post by stephenkrogh on 2011-03-02
Ok, how do I do that?

---

### Post by mick8985 on 2011-03-02
Restart you laptop and hit F1 repeatedly as you see the HP logo, you should enter setup mode from there navigate the menus until you find options for the wireless switch
On my dell I can toggle it so it switched bluetooth & wifi, Blueooth, Wifi or None. Choose None or Bluetooth.

---

