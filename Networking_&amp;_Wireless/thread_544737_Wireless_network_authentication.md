---
title: "Wireless network authentication"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by bigggnick on 2007-09-06
Hello all,

My school recently added a wireless network  I want to connect with my laptop, but I can't find the options to do it. Heres the instructions they give for mac and windows machines:

From Windows XP systems:  (using the built in windows wireless configuration manager)

Once booted up right click the wireless icon in the lower right tasktray
Select View Available Wireless Networks
Select the change advanced settings option
Select the wireless networks tab
Select the Add button
Enter the SSID of SchoolWiFi, leave all other options at defaults
Select the Authentication tab
Change the EAP type to Protected EAP (PEAP)
Select the properties option
Set the Authentication method to EAP-MSCHAP v2
Select the Configure Button
If your not sure or your machine is not a domain member, clear the "Automatically use my windows logon name and password" (and domain if any) check box
Select OK
Check off the enable fast reconect check box
Clear the validate server certificate check box
Select OK
When prompted for logon information, use your domain username and password and the domain name School
Select OK (twice)
You may notice a balloon popup on the wireless icon in the task try asking for credentials, select this popup by left clicking to be given the opportunity to logon

If this does not work, it is possible that you have another wireless configuration manager. Please see tech student for configuration.


From a MAC OS X system:  "FOR OS 10.4/ TIGER"

(Dear MAC users, please excuse my use of the improper names for stuff)
Select the wireless icon in the menu bar from the finder.
Select the Other option from the popup menu.
The network name is SchoolWiFi
The encryption type is WPA Enterprise
Your username is the same name you use on the domain, please remember that you are authenticating against a domain so you should use the
format School\USERNAME
Your password is the same as your domain password and follows the domain password policies.

I tried downloading every wireless network manager I could find under the add programs list (WiFi radar, KNetwork Manager, SWScanner), but none will give me these options.  Using the Knetwork manager, I can connect to it but i get "Page Not Found" errors from Fire Fox. Is there some trick to being able to input things such as encryption type (other than ASCII and Hex) and to put in things such as passwords? Am I missing something obvious?

Thanks

---

### Post by drewcoll on 2007-09-07
Try WICD

It connects to many networks that others cant.

---

### Post by bigggnick on 2007-09-09
k, thanks. I'll give that a shot.

---

