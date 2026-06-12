---
title: "Correct use of DNS entries for cross site Samba"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by Ifan_Jones on 2018-09-06
Hi All

I just need to confirm the DNS settings for Samba across multiple subnets connected via VPN.

Joining workstations from other sites than 192.168.14.0/255 works just fine, however the login time is very,very long for user accounts at the remote sites.  Login time is fine on the 192.168.14.0/255 subnet.

I suspect I have not got DNS setup correctly (please see attached)

The DHCP server at each site lists it's own DC as Primary DNS and SERVER1 as Secondary DNS

I have disabled roaming profiles as staff mainly stay at their own site.

Workstations are Windows 7 and 10

---

### Post by TheFu on 2018-09-06
I haven't a clue, but don't you need a WINS server?

BTW, 192.168.14.0/255 is not network nomenclature.  /32 is the largest number allowed - that would mean a direct route to one host.   255.255.255.0 is a /24.   255.0.0.0 is a /8.  It is binary math and IPv4 is limited to 32-bits.  It is only important if you type it in somewhere.

---

### Post by Ifan_Jones on 2018-09-06
Well, had read up about that.  I 'assumed' that WINS was builtin to Samba 4 as it's now standalone AD-DC.   I'll keep digging!

---

### Post by SeijiSensei on 2018-09-06
Modern versions of Windows use DNS as well as WINS.

Try installing the smbclient package if you don't have it already,  Then try to connect using its -d switch to increase its debugging.  A value of 2 or 3 should give you a lot of info.

Also what do you see in the remotes' samba logs when you connect?  Again you might want to increase the debug level on the server side to get more detail.

One way to see if DNS matters is to use IP addresses in the UNC like \\10.10.10.10\share.  Are these connections any faster?  If not, DNS is probably not the culprit.

Is there a central, authoritative server for DNS?  Are the DC DNS servers slaves to that one?

---

