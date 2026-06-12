---
title: "Tip: Dell 1420n wireless problem"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by David Ostrom on 2007-12-18
**This post could be related to an Ubuntu bug filed at**: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-043723acc841dd51a6c2dc294ccb036a75ceccac](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-043723acc841dd51a6c2dc294ccb036a75ceccac) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,
I purchased a Dell 1420n with Ubuntu (Fiesty) and have been having a problem connecting to wireless with network manager applet. Occasionally the "enable wireless" would  not be there. I would then have to restart my computer to get it working again, this has been a big pita. Here is my solution. Hope this helps others who have had the same problem.
David

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-043723acc841dd51a6c2dc294ccb036a75ceccac](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-043723acc841dd51a6c2dc294ccb036a75ceccac)

Restarting nm-applet
In my case (on Edgy) I had wireless with WPA working but no wireless connections ever showed under the network manager applet. To solve this issue I simply killed the nm-applet process (since there's no quit option via right-click) and then restarted the service. Wireless showed up right away. To kill the process go to System > Administration > System Monitor. Select the Processes tab and scroll to find a process called nm-applet. Click to highlight it and hit the "End Process" button. I added a "Run Application" utility to my panel, so I just click that and type in "nm-applet" to start it back up.

---

