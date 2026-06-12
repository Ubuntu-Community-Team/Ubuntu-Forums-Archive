---
title: "Ubuntu 16.04 wifi works from livesession on installation CD but not from user"
date: 2017-07-12
forum: Networking &amp; Wireless
---

### Post by 1jacquez on 2017-07-12
I notice that this problem goes back many years - to 2009 and perhaps even earlier.

Here is what happened to my system.
1. Ubuntu 16.04 was installed on new PC about 2 months ago.
2. Initially Wi-Fi was not picked up after Suspend
3. Fixes reported in Forums helped when implemented, and for past few weeks no problems

Subsequently, Software Installer wobbled and stopped working this week. I tried all the fixes reported in the forums, none which worked. Error message says "Sorry, Ubuntu 16.04 has experienced an internal error".
The last straw fix was to reinstall Ubuntu, which I did.

After this install, Wi-Fi is not enabled. I tried all the fixes I found on the forums. 

Strangely, when the Installation CD is active, it picks up Wi-Fi fine (even from GUI).

But not from any user.

This means Wi-Fi is available (but does not show as being available), and that the PC connection, user etc. all work properly (as evident from it working from Install disk).
 I tried all the options reported in forums -- such as restarting the network manager. Nada worked.

No Wi-Fi connection in the area shows up in the GUI's top right task bar.
Enabling network is ticked on.

Following Edit Connections, the WiFi network shows - [but "Last used" says Never]

From System Settings no Wi-Fi shows.
Wired shows "Cable unplugged" - but I do not have an ethernet connection.

Under options it sets up default as ethernet.

I have no clue what else to do....

heeeeelp please! :)

---

### Post by BenginM on 2017-07-12
[SIZE=3][FONT=arial narrow]Salutations!

Please #See: 
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

and post the whole result of the script here using the [tags] code , for example:[/FONT][/SIZE]

[PHP]
[CODE}

########## wireless info START ##########

[/CODE]
[/PHP]

[SIZE=3][FONT=arial narrow]Thanks, and welcome to the forums! :)[/FONT][/SIZE]

---

### Post by Hadaka on 2017-07-13
Hi from your post, I am of the impression you have no way to access the internet.
*If  this is correct please post the output of..
```
lspci -n | awk '/0200|0280/{print$3}'
rfkill list all |awk '/no/'
```

*If not correct please do as Scary.sa post#2 suggests.
thanks

---

