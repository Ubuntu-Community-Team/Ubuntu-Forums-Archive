---
title: "&quot;Network-&gt;DNS&quot; keeps changing without my OK - Heron"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by shortyjacobs on 2008-07-15
Hi all....longtime lurker, first time poster.

Every time I restart Hardy, the "DNS" tab under "Network" acquires two new entries: "192.168.2.1" under "DNS Servers" and "Belkin" under "Search Domains".

These two entries kill my internet browsing, as it causes every page I load to first spend 30 seconds in "looking for www.xyz.com" limbo in firefox.  Every time I start Hardy, I have to open the panel, "unlock", and delete the two entries.  As soon as I do, internet browsing returns to full speed.

What file is persistently "re-adding" these two entries?  How do I stop this?

THANKS!
Keith

---

### Post by shortyjacobs on 2008-07-16
mid-morning bump?  I know some smart person can answer this for me!

---

### Post by Iowan on 2008-07-16
Are you getting your address via DHCP? In particular from a Belkin device?  Under **/etc/dhcp3/dhclient.conf** is a **request** line that includes dns-servers. You might first copy that file to another name (like dhclient.conf.bak) and remove that entry from the file ( I like **sudo nano /etc/dhclient.conf**), save it, and restart networking.

---

### Post by shortyjacobs on 2008-07-16
Thanks Iowan!...no luck however.

I did exactly as you said, first removing just the "domain-name-servers" part of the line, then commenting out the whole line, doing both a ctrl-alt-bkspace and then a full "shut down" restart...the entries in the network panel still stubbornly reappear.

I am indeed getting my addy via DHCP, and it is indeed from a Belkin router.  I just don't quite understand, however, how a Belkin router can make changes to my "super duper secure" Ubuntu?:confused:

Any other ideas?

---

### Post by ModelM on 2008-07-16
I assume you have a couple of preferred DNS servers. For this example I'll use the addresses of OpenDNS, you can change the addresses to whatever you want.

In the file /etc/dhcp3/dhclient.conf, pick a spot for a new line around line 18 or so. The location isn't critical, and space it out with a couple of blank lines to make it easy to find.

Add this line here:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

You can use these address, or choose your own DNS server adresses.

Now, after you reboot, you'll see your preferred DNS addresses right at the top of the /etc/resolv.conf file. Below these entries will be the entries from DHCP, but it won't matter. This file is parsed from the top down and, as long as your preferred DNS servers are working, the DHCP info will never be reached.

---

