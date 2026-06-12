---
title: "WIFI - network drops out intermittently but consistently!"
date: 2024-10-09
forum: Networking &amp; Wireless
---

### Post by stevetu2 on 2024-10-09
Good morning - my first post.

I'm posting for my son who is working abroad and using a wireless connection on Ubuntu - version 22.04.4 with Kernel 6.8

He has an issue with the wireless connection dropping out on a regular basis - but not always after the same amount of time. 

I'm used to other Linux variants - so I have have managed to get him to run nmcli to try to see what is happening - and he's getting:

Network is now in the 'connected (site only)' state. 
Connectivity is now limited.

Googling that, it suggests using the system settings to stop/start the WIFI and failing that to restart the NetworkManager service.
 
I've talked him through the suggestions (using: sudo systemctl restart NetworkManager), but they appear to have no effect and he has to reboot to regain connection.

Is there a known issue - and anyone know of a workaround?

Thanks in advance.

PS after toggling the WIFI via system settings, the connection is still dead. Trying then to restart NetworkManager (sudo systemctl restart NetworkManager) and then using nmcli to get the status it shows... the attached (can't attach - how do I upload a local image here?)

---

### Post by praseodym on 2024-10-27
Please run the Wireless Script from the sticky thread and show the outputs

---

### Post by prcowley on 2024-10-28
I recently upgraded from 24.04 to 24.10 and immediately started to experience random wifi dropouts.
According to the log the error message was "Wireless secrets not provided" which I thought strange as I had not had any problems in the past.

What is happening is the router (not mine so unable to change anything) terminated the DHCP lease every 600 seconds (this is because 13 people use the WiFi where I live and the short time was to allow others to connect in time of high usage)

Anyway, the lease renewal business have been going fine until the upgrade to 24.10. I did a lot of internet searching but nothing worked until I saw this suggestion buried in a message "What I discovered was that when I chose to save the password for  "this user only (encrypted)" that I get the error "no secrets: No agents  were available for this request"{This is in the WiFi config setting for the connection I am using]
     HOWEVER, when I choose the option "store password for all users (not  encrypted)" that everything starts working straight away.   

I had wondered about that myself when trawling though the WiFi settings.  I changed the option to Store password for all users (not encrypted) and that fixed the issue
There is obviously some bug where the WiFi re-connection occasionally can't read the encrypted password (or it takes to long).

I hope this helps someone
Pete

---

### Post by lilyrogwes on 2024-11-16
You can try checking the router for any potential configuration issues and review NetworkManager logs for errors using journalctl -u NetworkManager. Additionally, disabling power management for the WiFi card and ensuring drivers are up to date may help. If the issue persists, trying a USB WiFi dongle could help isolate hardware-related problems.

---

