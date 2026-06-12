---
title: "Help setting up a VPN connection using OpenVPN"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by qbektrix on 2008-10-17
I am using the VPN service from Witopia. I have the
[LIST]
[*]ca.crt
[*]<name>.crt
[*]<name>.key
[*]openvpn.conf
[/LIST]

How can i setup the connection? Where should i same the files? I tried it with the nm-applet's UI. But i am getting a connection error. Any clue os to my issue? Thanks

---

### Post by kevdog on 2008-10-17
Im not familiar with Witopia.  Do they have instructions?  Have you investigated using OpenVPN as the client? I believe the config file and the certificates are to be placed in /etc/openvpn

---

### Post by qbektrix on 2008-10-17
I am using openvpn client. I pasted the files in the same folder as suggested.

---

### Post by 1902 on 2008-11-11
i had the same problem, the openvpn will not work because of the NM bug that will not let you save your settings so you have to use witopia pptp, you need to save the files in usr/etc/openvpn and install the pptp client and manager (first you will need to have a witopia pptp username and password,if not create one) then follow this [http://ubuntuforums.org/showthread.php?t=964255&highlight=pptp]("http://ubuntuforums.org/showthread.php?t=964255&highlight=pptp")

it worked for me
hope it will work for you

cheers

---

