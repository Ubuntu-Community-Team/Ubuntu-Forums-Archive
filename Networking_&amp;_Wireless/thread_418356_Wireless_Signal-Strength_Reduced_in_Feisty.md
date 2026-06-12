---
title: "Wireless Signal-Strength Reduced in Feisty"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by englishtim on 2007-04-22
I've just installed Feisty, and noticed that my wireless connection signal-strength has dropped dramatically compared to Dapper - it's now so bad that it frequently drops the connection, and also seems to vary quite a bit. Has anyone else seen this? Are there any fixes or workarounds? Are there any "hidden" settings for controlling the wirelss card?

Everything about my setup is otherwise unchanged, including the location of my Wireless Access-Point and the places in the house that I normally work. Under Dapper, wireless connectivity worked brilliantly well.

Other details:
- Feisty was installed "clean" onto an empty partition;
- The wireless card is a Netgear WG511v2, using the Marvell driver under ndiswrapper with WPA security;
- I used the "Windows Wireless Drivers" ndiswrapper GUI to install the Marvell driver

Although I've used Dapper for a while, I count myself as very much a Linux novice and I've no idea where to start with this.

Thanks in advance!

---

### Post by morky on 2007-04-24
> **englishtim said:**
> I've just installed Feisty, and noticed that my wireless connection signal-strength has dropped dramatically compared to Dapper - it's now so bad that it frequently drops the connection, and also seems to vary quite a bit. Has anyone else seen this? Are there any fixes or workarounds? Are there any "hidden" settings for controlling the wirelss card?

Everything about my setup is otherwise unchanged, including the location of my Wireless Access-Point and the places in the house that I normally work. Under Dapper, wireless connectivity worked brilliantly well.

Other details:
- Feisty was installed "clean" onto an empty partition;
- The wireless card is a Netgear WG511v2, using the Marvell driver under ndiswrapper with WPA security;
- I used the "Windows Wireless Drivers" ndiswrapper GUI to install the Marvell driver

Although I've used Dapper for a while, I count myself as very much a Linux novice and I've no idea where to start with this.

Thanks in advance!

I got the same problem. i'm sitting right next to the wireless-router and my connection-strength is 50-60%

---

### Post by deadlines on 2007-04-24
> **englishtim said:**
> I've just installed Feisty, and noticed that my wireless connection signal-strength has dropped dramatically compared to Dapper - it's now so bad that it frequently drops the connection, and also seems to vary quite a bit. Has anyone else seen this? Are there any fixes or workarounds? Are there any "hidden" settings for controlling the wirelss card?

Everything about my setup is otherwise unchanged, including the location of my Wireless Access-Point and the places in the house that I normally work. Under Dapper, wireless connectivity worked brilliantly well.

Other details:
- Feisty was installed "clean" onto an empty partition;
- The wireless card is a Netgear WG511v2, using the Marvell driver under ndiswrapper with WPA security;
- I used the "Windows Wireless Drivers" ndiswrapper GUI to install the Marvell driver

Although I've used Dapper for a while, I count myself as very much a Linux novice and I've no idea where to start with this.

Thanks in advance!

I'm running into a similar issue, I wonder if you're observing any of the errors I'm seeing in my logs, see: [http://ubuntuforums.org/showthread.php?t=420741](http://ubuntuforums.org/showthread.php?t=420741)

Also just out of curiousity what brand & model is your wireless router?

---

### Post by morky on 2007-04-27
> **deadlines said:**
> I'm running into a similar issue, I wonder if you're observing any of the errors I'm seeing in my logs, see: [http://ubuntuforums.org/showthread.php?t=420741](http://ubuntuforums.org/showthread.php?t=420741)

Also just out of curiousity what brand & model is your wireless router?

```

iwconfig ath0
ath0      IEEE 802.11a  ESSID:"bengtogmalcolm"  Nickname:""
          Mode:Managed  Frequency:2.484 GHz  Access Point: 00:40:10:20:00:03   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/94  Signal level=-18 dBm  Noise level=-82 dBm
          Rx invalid nwid:2192752  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Nope not the same.. But some info about my hardware:

*Thinkpad T42P
*Atheros Communications, Inc. AR5212 802.11abg NIC
*Linksys WRT54GS running DD-WRT

---

### Post by deadlines on 2007-04-27
Check out my [other post]("http://ubuntuforums.org/showthread.php?t=420741"), in short I was able to finally get stable using ndiswrapper and by using wicd rather than network-manager.  Don't know if this will help you, but it may be worth a shot.

Cheers

---

### Post by Kobalt on 2007-04-27
Network-Manager does reduce my signal strength as well (an average 20%). I've flushed it since and I'm glad I did. 
See this guide to configure your network security properly and stick to the good old network-monitor : [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by tl3000 on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/105357](https://bugs.launchpad.net/bugs/105357) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/105357](https://bugs.launchpad.net/bugs/105357) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **englishtim said:**
> I've just installed Feisty, and noticed that my wireless connection signal-strength has dropped dramatically compared to Dapper - it's now so bad that it frequently drops the connection, and also seems to vary quite a bit. Has anyone else seen this? Are there any fixes or workarounds? Are there any "hidden" settings for controlling the wirelss card?

Everything about my setup is otherwise unchanged, including the location of my Wireless Access-Point and the places in the house that I normally work. Under Dapper, wireless connectivity worked brilliantly well.

Other details:
- Feisty was installed "clean" onto an empty partition;
- The wireless card is a Netgear WG511v2, using the Marvell driver under ndiswrapper with WPA security;
- I used the "Windows Wireless Drivers" ndiswrapper GUI to install the Marvell driver

Although I've used Dapper for a while, I count myself as very much a Linux novice and I've no idea where to start with this.

Thanks in advance!


See the related bug report and add your inputs:

[https://bugs.launchpad.net/bugs/105357](https://bugs.launchpad.net/bugs/105357)

---

### Post by stevieb on 2007-04-28
same problem here, on a Lenovo 3000 C100.  i found if i don't use any connection manager, wireless seems to work fine, although i don't know how to check signal strength in terminal.

-steve

---

### Post by stevieb on 2007-05-05
hey, check this out-

i went back to dapper, and wireless works great again.  unfortunately, no desktop effects :-( and no more suspend/hibernate.  i wonder whether putting a 2.20 or 2.21 kernel would give both?

-steve

---

