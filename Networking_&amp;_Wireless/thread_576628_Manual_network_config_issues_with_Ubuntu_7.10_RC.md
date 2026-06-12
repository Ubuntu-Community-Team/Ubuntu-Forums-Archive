---
title: "Manual network config issues with Ubuntu 7.10 RC"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by openaddict on 2007-10-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152982](https://bugs.launchpad.net/ubuntu/+bug/152982) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey guys, I'm not sure if this might be a bug in the Release Candidate for Ubuntu 7.10, but I had some issues with manually configuring the network on the live CD when I was attempting to install it.  The problem was an incorrect DNS entry from my DHCP server which I tried to override by manually configuring the network connection, however Ubuntu didn't save my changes or reload the network settings.   I eventually had to correct the issue on my DHCP server and reboot the 7.10 live cd which then pulled the correct DNS information.  

I even swapped out the NIC at first, because I thought it was a hardware issue not accepting or being able to change any network settings.  My laptop running 7.04 had no issues manually configuring the network.

Just FYI.  I was able to get around it, but it did cause me confusion at first by not being able to configure the network settings manually on the live cd.

---

### Post by anubhavrocks on 2007-10-15
I guess LIve CD settings are not persistant,if you install Ubuntu and then save setting they should behave normally,

---

### Post by openaddict on 2007-10-15
Yep, I'm aware they aren't persistent changes, but the problem was I couldn't change the network settings at all.

---

### Post by anubhavrocks on 2007-10-16
okay i am sorry i got your query wrong.You can also check the  file to see if the changes have been written to.Also you should disable Roaming mode on that interface.
```
/etc/network/interfaces 
```

---

### Post by telemetry on 2007-10-24
I'm having problems with DNS - I've tried editing resolv.conf and other settings but although I can change DNS it's all lost on reboot.  This is despite editing in root.  I'm not sure what to do - as each time i log on i have to manually input my DNS as the default is something like: 192.6.1.1 which repository and firefox don't respond to but oddly: konqueror doesn't mind.

I'm hoping somebody can offer me a solution - as the alternative is to reinstall gutsy gibbon and try and edit DNS at the start although I'm not sure that would work.

thanks
robert.

---

