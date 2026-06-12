---
title: "WEP KEY with wireless"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by violentpasta on 2007-05-01
Hello, im new to the whole ubuntu thing, but i have a usb wireless adapter with an antenna that accesses my wireless internet from my router in the other room.  it is WEP encrypted and i have the key with me. its 64 digits long. 

My problem is, it detects the wireless access point but wants me to input my password, but the dropdown options for the wireless key doesent include this key.  its like when i type it in, its all correct but the box that sais log into network greys out.  

In windows i type the key in and type it again in the confirm and it decreases in length significantly.  
Does anyone here know what im talking about?  i dont know much about WEP other than its weak security, i dont care i just want to access my stepdad's internet connection on ubuntu like i can on windows.  but the key is encrypted, do i need to decrypt it?  i have the 64 bit string i just am lost from here, any help is appreciated. thanks

---

### Post by jubilee33 on 2007-05-01
You can try supplying the WEP key the conventional way.  Open a terminal and type in:

```
sudo gedit /etc/network/interfaces
```

The text editor will open a file.  You probably can see in a section your "wireless-essid".  That's where your wireless connection info is stored.  Under "wireless-essid", add one line starting with "wireless-key".  So it looks like below:

```
wireless-mode managed
wireless-essid YOUR--ESSID--HERE
wireless-key YOUR-WEP-KEY-HERE
```

Good luck!

---

