---
title: "Ubuntu 14.04 -- Do not see Centurylink Wifi Network"
date: 2016-06-11
forum: Networking &amp; Wireless
---

### Post by david526 on 2016-06-11
My household recently switched to Centurylink from Comcast. I am using Ubuntu 14.04.4. The issue I am having is I do not see MY CenturyLink wifi network in my ubuntu's list of available wifi connections. I can, however, see my neighbor's centuryilnk wifi networks as show up in my list of available wifi networks. 

I am using a C2000T modem/router. The ethernet connection works just fine. Also, I am able to connect to my CenturyLink wifi from my iPhone and several PCs (windows-based). So it does not appear to be an issue with my network, but with my OS. Is there something I need to do to activate the wifi network on my ubuntu system? Anyone have experience with this? I suspect the modem/router model may also be causing some issues.

---

### Post by praseodym on 2016-06-12
Remove the old network profile and create a new one. Also please run the wireless script from the sticky thread and show the outputs.

---

### Post by david526 on 2016-06-12
> **praseodym said:**
> Remove the old network profile and create a new one. Also please run the wireless script from the sticky thread and show the outputs.
Hi. Sorry for the lack of info. I made the same post on askubuntu.com [https://askubuntu.com/questions/785919/unable-to-see-my-centurylink-wifi-network-in-ubuntu-14-04-4](https://askubuntu.com/questions/785919/unable-to-see-my-centurylink-wifi-network-in-ubuntu-14-04-4)
If it is OK, I will just provide this link which contains all the troubleshooting I have performed as well as the outputs.

---

### Post by praseodym on 2016-06-12
Why are there wlan0 infos but no loopback interface in the "interfaces" file? Re-set it:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot

---

### Post by david526 on 2016-06-12
Hey, I think you were looking at the first output I provided. I changed it after one of the comments told me to. 
[http://pastebin.com/FyNT30nh](http://pastebin.com/FyNT30nh) this is the new one and it has the loop

---

### Post by wildmanne39 on 2016-06-12
Did you remove all your network connections in network manager then reboot and see if network manager can find the network?

---

### Post by david526 on 2016-06-12
> **Wild Man said:**
> Did you remove all your network connections in network manager then reboot and see if network manager can find the network?

No. How do I do that? Can't find any instructions on google.

---

### Post by wildmanne39 on 2016-06-12
Go into network manager click on edit connection then remove all wireless connections then reboot.
Thanks

---

### Post by david526 on 2016-06-12
> **Wild Man said:**
> Go into network manager click on edit connection then remove all wireless connections then reboot.
Thanks
Just did as you said. Went to Network Manager and clicked "delete" on all the wireless networks found. Then rebooted. I still don't see my network.

---

### Post by david526 on 2016-06-12
I tried to connect to the "DANG" network in wicd-curses. It gets stuck on "obtaining IP address"
[http://imgur.com/D1NB6Eu](http://imgur.com/D1NB6Eu)

---

### Post by wildmanne39 on 2016-06-12
You do not want wicd and network manager installed at the same time, remove wicd and go into your router because Ubuntu use to have trouble connecting to networks with names all in caps, please change the name to all lower case with no spaces or special characters. Then reboot.

---

### Post by david526 on 2016-06-12
> **Wild Man said:**
> You do not want wicd and network manager installed at the same time, remove wicd and go into your router because Ubuntu use to have trouble connecting to networks with names all in caps, please change the name to all lower case with no spaces or special characters. Then reboot.
I installed wicd-curses last night just to see if I could use this to connect to the network I cannot see in network manager. I removed it now again and changed my wifi network to all lower case "dang" and still see nothing. 

This is really started to annoy me. I don't understand what is going on.

---

### Post by wildmanne39 on 2016-06-12
Can you actually connect to one of the other networks? Did you do any upgrades recently?

---

