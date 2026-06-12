---
title: "Wireless network problem"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by ciaros on 2008-11-25
Hi guys,

Sorry for the ambiguous title but I'm having a problem setting up an Ad-Hoc wifi connection in Hardy. I have currently set up my WinXP desktop to provide internet connection sharing yet when I try to connect on my hardy laptop the network connection icon in the notification area disappears.

The problem only occurs when I click on any Ad-Hoc connection available to me and does not get as far to try authenticating. When I add the network monitor icon back to the panel it only displays the local loop back connection, even if I plug into my network via Ethernet once the above error has occurred.

If I try to manually change my adapter to Ad-Hoc mode using terminal I am given the error:
[I]
'Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Device or resource busy.'[/I]

I haven't got a clue as to what causes this and was wondering if anybody would know where to start?

Thanking you in advance!

---

### Post by jnorthr on 2008-11-25
You may find some answers in the system logs.
goto System>Admin>System Logs
which should show the kernel messages written into /var/log/syslog
and then review the messages near the bottom of the scroll pane as these should be the most recent messages.

I think i'd try to turn off any wep/wpa security until this i resolved.

You could also try using 'managed mode' rather than ad-hoc just to see what happens.

What do you see from the iwconfig and ifconfig commands ?

---

### Post by Ayuthia on 2008-11-25
> **ciaros said:**
> Hi guys,

Sorry for the ambiguous title but I'm having a problem setting up an Ad-Hoc wifi connection in Hardy. I have currently set up my WinXP desktop to provide internet connection sharing yet when I try to connect on my hardy laptop the network connection icon in the notification area disappears.

The problem only occurs when I click on any Ad-Hoc connection available to me and does not get as far to try authenticating. When I add the network monitor icon back to the panel it only displays the local loop back connection, even if I plug into my network via Ethernet once the above error has occurred.

If I try to manually change my adapter to Ad-Hoc mode using terminal I am given the error:
[I]
'Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Device or resource busy.'[/I]

I haven't got a clue as to what causes this and was wondering if anybody would know where to start?

Thanking you in advance!

Did you do ifconfig wlan0 down before switching over to ad-hoc mode?

---

