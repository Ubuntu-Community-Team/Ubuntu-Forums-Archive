---
title: "Can't connect to internet"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by JRylez on 2011-03-03
Im sorry, i know there are mannnny threads for this but i cant seem to find one that goes for me, i can't open windows network. It says "Unable to mount location: Failed to retrieve share list from servers" and from that nothing has really happened. I have verizon fiOS wireless internet with a  essid and a WEP but have no idea what to do... please help? Oh also i just downloaded ubuntu like two hours ago

---

### Post by Ben Page on 2011-03-03
It seems you are trying to connect to Windows network i.e. Windows based PC on the network. This has nothing to do with the internet. If you want to connect to another PC with Windows OS, install SAMBA and set it up so it's in the same workgroup as the Windows PC and turn off password protected sharing on that Windows PC.

If you want to connect to the WWW network aka the Internet, check if you have internet connection and adapter enabled. Type ifconfig into terminal and post the output.

---

### Post by maqtanim on 2011-03-03
Not sure what you asked for.

If you want to connect the internet (e.g. google.com, ubuntu.com etc), then go to System > Preferences > Network Connections. There you'll find to setup the internet connection for wireless.

---

