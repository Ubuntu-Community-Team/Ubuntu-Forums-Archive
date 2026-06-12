---
title: "Wireless Network connections"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by LGCarmona on 2009-03-28
Theory says that network connections are handled by Ubuntu’s NetworkManager. Clicking it will show a list of nearby wireless networks (I've ensured the right kind of wireless protection i.e. WEP/WPA has been detected by Ubuntu). Connecting to a network is simply a matter of selecting it and typing the wireless password when prompted. When done, click CONNECT,

except that in me case CONNECT is not an iluminated option.

What gives?

---

### Post by RedSingularity on 2009-03-28
Make sure you have selected the correct Wireless protection protocol.

---

### Post by trot2millah on 2009-03-28
Ya make sure you have entered the correct passkey or hex code, and all the settings match up with what it should be.  Then the option should be illuminated, you can't connect without information.

---

### Post by fly-by-night on 2009-03-28
In my case selecting connection from list is never available.  And my password only work pre-configured.

I had to manually configure mine under Settings/Preferences/Network Configuration.

Under the Wireless section, Add your setting manually.  You may have to specify DNS Servers under IPv4 Settings (I could connect to router, but not Internet).

Also if yours is still not on the list when trying to make connection, Select Connect to Hidden Wireless Network - change "New" to your connection name and connect.

Another something, when you switch wireless off and back on you may have to right click the Network icon and deselect Enable Networking and the reselect it (wireless will then be on).

---

