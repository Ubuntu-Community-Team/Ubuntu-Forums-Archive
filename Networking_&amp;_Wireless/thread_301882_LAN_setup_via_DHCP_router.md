---
title: "LAN setup via DHCP router"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by Billyum on 2006-11-17
Greetings:

I am using Xubuntu 6.10. I installed Samba OK, it seemed, but I cannot yet network with the Windows machines at home. All the machines get IP addresses from the DHCP router. In the router's list of clients every machine appears, but my Xubuntu machine has no name listed, just the MAC address of the ethernet card. Pinging works OK. My Xubuntu machine shows up as a Samba server in the workgroup listing of the Windows machines, but they cannot connect to it. Maybe the lack of a name in the router's list has something to do with that. Or maybe the problem lies elsewhere. Any help much appreciated. 

Billyum

---

### Post by rickyjones on 2006-11-17
Having the name in the router signifies nothing - my latest Ubuntu server didn't show up in the DHCP list with a name (I also didn't have Samba installed.)

When you try connecting from a Windows machine, what error does it give you? Please try to be exact - maybe include a screen show if applicable.

Can you connect just using the IP address? E.g.: \\192.168.1.2

More information /will/ be necessary :)

---

### Post by Billyum on 2006-11-18
Thanks, Ricky! :D 

I tried various ways to connect from a Windows machine, and always got this error message:

  The network path was not found.

There is no sign of the Xubuntu machine, BillyBob, in Network Neighborhood, but there is an icon in Workgroup computers. Clicking that icon produces this longer message:

  \\BillyBob is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

  The network path was not found.

As for permissions, on BillyBob I ran

  sudo smbpasswd -a Billyum

entered a password, and got this error message:

Failed to initialise SAM_ACCOUNT for user Billyum. Does this user exist in the UNIX password database ?
Failed to modify password entry for user Billyum

That's a hurdle to overleap, but shouldn't I be able to connect to a sign on screen, even without adding the user?

Also, I did create a shared folder, \home\public , which seems to be OK.

Many thanks,

Billyum

---

### Post by nickmcg on 2006-11-18
> **rickyjones said:**
> Having the name in the router signifies nothing - my latest Ubuntu server didn't show up in the DHCP list with a name (I also didn't have Samba installed.)

When you try connecting from a Windows machine, what error does it give you? Please try to be exact - maybe include a screen show if applicable.

Can you connect just using the IP address? E.g.: \\192.168.1.2

More information /will/ be necessary :)

There's info in these threads, but in summary you need to install winbind and samba, and edit /etc/nsswitch.conf changing the hosts line to include 'wins'
e.g hosts: files wins dns

[http://www.ubuntuforums.org/showthread.php?t=278992](http://www.ubuntuforums.org/showthread.php?t=278992)
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

Hope that helps

Nick

---

### Post by Billyum on 2006-11-19
Well, I have solved that problem. How? I installed Ubuntu instead of Xubuntu. 

Cheers,

Billyum

---

