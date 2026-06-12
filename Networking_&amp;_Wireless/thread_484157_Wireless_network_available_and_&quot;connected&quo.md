---
title: "Wireless network available and &quot;connected&quot; but no internet"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by davbren on 2007-06-25
Hi, I just did a clean install of Feisty on my system and I have available networks using roaming mode so I know the my wireless card is recognised and in use, however when I try to use the internet I can't. its as though the network is not there...

When I look at the netwok information everything is blank there is not information on any of the headings. I also tried a manual configuration so that I entered in the Essid still with no luck. Any ideas?

Yeh is solved the problem with ndiswrapper, genius program WOOO

---

### Post by arvevans on 2007-06-25
A little more information would help debugging your problem:
[LIST]
[*]Can you connect to the internet in roaming mode using other than your own WiFi Hub/Router?
[*]Is this a problem of not having a valid IP address (DHCP issue)?
[*]Is this a problem of not having  DNS server(s) assigned to translate URL' to IP addresses?
[*]What version of Ubuntu Linux are you running?
[*]Are you using a laptop or desktop computer?
[/LIST]

If running Ubuntu with the Gnome interface:
[LIST]
[*]Go to: System-Administration-Network
[*]Click on (highlight) Wireless Connection
[*]Select Properties, and make sure that roaming mode is checked, and that this uses DHCP mode (no hard coded IP address, no Subnet mask, and no Gateway configured)
[*]Select "General" and enter a host name (single word, can be almost anything)
[/LIST]

[LIST]
[*]Open a CLI (Command Line Interface) by going to: Applications-Accessories-Terminal
[*]enter "ifconfig" and examine the output to insure that you have (1) an IP address, (2) a netmask, (3) data flowing in both directions.
[*]enter "ping -c4 64.233.167.99" and hit ENTER.  You should see 4 pings and ping response information showing either 0% or 100% data loss.
[*]Enter "ping -c 4 google.com" and hit ENTER.  You should see 4 pings and ping response information indicating either 0% or 100% packet loss.
[/LIST]

If you can ping successfully using the IP address, but not ping using a textual URL, then you have DNS configuration problems.  If you cannot ping successfully using a numerical IP address, then you may have DHCP configuration   or DHCP server problems.
_._

---

### Post by davbren on 2007-06-25
Well now I can't even see the wireless option in networks...

---

### Post by davbren on 2007-07-05
I installed Wifi radar, and it sees the network but it can't get the IP, I'm not running two wifi connection things so nothing is conflicting, what can I do?

---

### Post by ewack on 2008-02-28
I know this thread is old, but did you ever figure out an answer?

I just installed ubuntu and it shows that i'm connected to the network but i get the browser error.  I couldn't ping either ip or by name...i believe i'm trying the ping correctly...

I can connect by hardwire just fine.

Any help would be great!

---

