---
title: "[SOLVED] Unable to print to network printer bizhub c352"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Alt69 on 2008-08-20
Hi, in need of some printing help. 

Yesterday there was blackout which resulted in everything going down. Once everything have been restarted, I am no longer able to print or use the scanning function of my Konica Bizhub c352 (c352).  I have had the photocopier printing and the ability to scan for over 5 months without making any changes. One note, the ip address changed after the powerage. I have now changed the ip address to 192.168.2.150, as the server came up with the photocopier ip address.
  (still learning about setting up servers properly)

Using Ubuntu 7.10 with latest patches. I run the gui interface on the server.



What I can do:

- on a WinXp laptop, I am able to get the Konica Pagescope utilities at 192.168.2.150.
   - I am able to change the settings on the photocopier.
- able to get to the SAMBA share on the server from all desktops.


What I can't do.
- on the server, I am not able to get to the Pagescope utilities. 
- I am not able to ping the address from either the server or any other desktop.
- not able to print to the c352.
- I am not able to scan from the c352 to the shared folder on the server.



Tried so far:
- changing the ip address on the printer settings on the server.
- port 9100 was the default port when I first installed it, and made sure it was still set to "ON" on the c352.
- I have deleted the printer and tried creating an new one. Under the device URI I have 
     Socket://192.168.2.150:9100


Is this a patch issue, as I am not sure what I am doing wrong, or what else to try. Any help would be greatly appreciated as our office is now unable to print.


Thanks,


PS. Is there anyone in the Burlington, Toronto GTA, ON area for support?

---

### Post by Alt69 on 2008-08-21
Hi, problem solved. Just wanted to let everyone know that the problem was with the Konica Surge protector. I had the network cable from the copier into the surge protector, then another cable from the surge protector into the jack in the wall. 

When I removed the network cable and plugged the copier directly into the wall, viola, connection.

And I had ruled out a cable issue, since I was able to get to the admin utility on the copier from the xp laptop. You learn something new everyday. :)


cheers,

---

