---
title: "server not found xubuntu"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by said-el on 2016-06-15
Dear All,

Recenlty , I start having problems with home WIFI , I tried in Windows and android and seems to work fine, 
But in Xubuntu 16.04 I keep having Server not found in Firefox or This site can’t be reached in Opera
Wireless script results  : [http://paste.ubuntu.com/17374502/](http://paste.ubuntu.com/17374502/)

Any help please

---

### Post by X-RED_Tech on 2016-06-15
You should change the wireless security to WPA2-AES.
WEP or open is practically the same.

Any reason not to use the internal card?
The driver used automatically for the USB wifi might not be the better. I'll leave that to the experts.

---

### Post by X-RED_Tech on 2016-06-15
PS - What were the results of this thread? -> [http://ubuntuforums.org/showthread.php?t=2323047](http://ubuntuforums.org/showthread.php?t=2323047)

---

### Post by said-el on 2016-06-15
> **X-RED_Tech said:**
> You should change the wireless security to WPA2-AES.
WEP or open is practically the same.

Any reason not to use the internal card?
The driver used automatically for the USB wifi might not be the better. I'll leave that to the experts.

The internal card is damaged, not working both in Windows and linux , that's why I bought wireless dongle

---

### Post by said-el on 2016-06-15
> **X-RED_Tech said:**
> PS - What were the results of this thread? -> [http://ubuntuforums.org/showthread.php?t=2323047](http://ubuntuforums.org/showthread.php?t=2323047)

It was solved , but I think this is a different issue here

---

### Post by X-RED_Tech on 2016-06-15
You could have have say thanks and at least posted a follow up telling others how the solution worked...
And my question was also a hint for trying it again. You're still using the original driver:
```
[COLOR=#000000]GENERAL.VENDOR:                         Realtek
[/COLOR]GENERAL.PRODUCT:                        802.11n WLAN Adapter
[COLOR=#000000]GENERAL.DRIVER:                         **rtl8192cu**[/COLOR]
```
Had you actually followed those instructions and you would be running with [COLOR=#000000]**8192cu** instead.[/COLOR]

---

### Post by chili555 on 2016-06-15
If the internal is not working, I'd certainly blacklist its driver so it doesn't cause any interference.

---

### Post by said-el on 2016-06-16
> **chili555 said:**
> If the internal is not working, I'd certainly blacklist its driver so it doesn't cause any interference.

Would you please tell me how to block it ?

---

### Post by said-el on 2016-06-16
> **X-RED_Tech said:**
> You could have have say thanks and at least posted a follow up telling others how the solution worked...
And my question was also a hint for trying it again. You're still using the original driver:
```
[COLOR=#000000]GENERAL.VENDOR:                         Realtek
[/COLOR]GENERAL.PRODUCT:                        802.11n WLAN Adapter
[COLOR=#000000]GENERAL.DRIVER:                         **rtl8192cu**[/COLOR]
```
Had you actually followed those instructions and you would be running with [COLOR=#000000]**8192cu** instead.[/COLOR]

Sorry , I did marked it as solved now.
is rtl8192cu different from 8192cu ?

---

### Post by chili555 on 2016-06-16
> **said-el said:**
> Would you please tell me how to block it ?In a terminal:```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot.

---

### Post by X-RED_Tech on 2016-06-16
Here the things: The internal is probably working just as good as the USB, the main problem being bad router settings (WEP). Apparently, it all started with this unanswered thread: [http://ubuntuforums.org/showthread.php?t=2250407](http://ubuntuforums.org/showthread.php?t=2250407)
Every other thread is the same.

> [COLOR=#000000]is rtl8192cu different from 8192cu ?[/COLOR]

Yes. The whole point of the other thread was to get you (and test) a new driver.

---

### Post by said-el on 2016-06-16
> **X-RED_Tech said:**
> Here the things: The internal is probably working just as good as the USB, the main problem being bad router settings (WEP). Apparently, it all started with this unanswered thread: [http://ubuntuforums.org/showthread.php?t=2250407](http://ubuntuforums.org/showthread.php?t=2250407)
Every other thread is the same.

Yes. The whole point of the other thread was to get you (and test) a new driver.

How can I block rtl8192cu and use 8192cu instead ?

---

### Post by X-RED_Tech on 2016-06-16
> **said-el said:**
> How can I block rtl8192cu and use 8192cu instead ?

So, 9 hours ago you finally posted this [reply]("http://ubuntuforums.org/showthread.php?t=2323047&p=13504823#post13504823") to the instructions for downloading&installing the new driver and blacklist the original, saying it's solved and now this?
Even if you had tried that solution which is doubtful, the most important issue here is the wireless security settings you should change in the router providing the "flat9" access point: Change WEP to WPA2-AES (AES can show up with a different name depending on the router, the point is to avoid TKIP). Yes, I'm aware it most likely work fine with Windows and even Android but its security its a joke and WEP can also negatively affect the network performance overall. Changing it to the recommended settings as above will improve the network for any and all clients regardless of the OS.

---

