---
title: "hidden ssid"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Red Rebel on 2009-01-03
Hi I have chose to hide the ssid of my router, however, neither Ubuntu nor my windows machine see my router now. I tried to connect to hidden network with ubuntu, but it creates a "fake" name under networks list with no signal strengh? Can someone tell me how to configure a connection with hidden ssid on Ubuntu and windows? Any help would be greatly appreciated

---

### Post by superprash2003 on 2009-01-03
which ubuntu version are you using?? have you disabled roaming mode and tried connecting manually in network manager?

---

### Post by Red Rebel on 2009-01-03
I am using Ubuntu 8.10 Desktop. I have not disabled roaming mode. How do I do that? I assume when you say 'network manager' you mean 'network connections'? I have tried to 'connect to hidden wireless network', but it didn't work. I am going to try to 'create new wireless network' in a bit, to see if I could get it to work. Thanks.... I will post my results shortly.

---

### Post by superprash2003 on 2009-01-05
this should help .. yes preferences->network configuration .. there under Wireless.. Click on Edit and enter SSID manually there.. if not you could do this via old network manager.. follow this till step 4  [http://www.prash-babu.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://www.prash-babu.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) . .. then follow this [http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html](http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html)

---

### Post by mcduck on 2009-01-05
The "Connect to Hidden Wireless Network" is the correct option. Just make sure you type the SSID correctly (it's case-sensitive!).

---

### Post by stchman on 2009-01-05
> **Red Rebel said:**
> Hi I have chose to hide the ssid of my router, however, neither Ubuntu nor my windows machine see my router now. I tried to connect to hidden network with ubuntu, but it creates a "fake" name under networks list with no signal strengh? Can someone tell me how to configure a connection with hidden ssid on Ubuntu and windows? Any help would be greatly appreciated

Hidden SSIDs are actually worse than broadcasting your SSID.  Don't be led that if you have a hidden SSID that you are secure.  If you want security use WPA or WPA2 encryption with at least a 24 character passphrase with uppercase, lowercase, numbers and symbols.

If your router is not WPA capable use WEP.  WEP kind of sucks, but is better than nothing.

Also MAC filtering is completely worthless as well.

---

