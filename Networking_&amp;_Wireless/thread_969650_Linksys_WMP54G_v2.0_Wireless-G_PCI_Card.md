---
title: "Linksys WMP54G v2.0 Wireless-G PCI Card"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by hksduhksdu on 2008-11-03
This is my card and I would like to share my experience of installing this card.  The installation is simple and easy, all you need is to connect to internet with wire at first so Restricted Driver Manager can search for you.

Specs:
AMD64 4000+
2GB RAM
MSI Business Platform nVidia 6150 onboard
200GB HD
Linksys WMP54G v2.0 (Broadcom 4306)
Ubuntu 8.10

1. Connect to internet using wired connection.
2. Restart your computer if it is running.
3. Should see Restricted Driver Manager pop up and click it.
4. It should show it detects your card as Broadcom 4306 v2.0 or similar.
5. Activate it.
6. Now go to Network Manager.
7. Create new wireless connection.
8. Make sure your wireless settings are correct.
9. Make sure your router does not restrict your MAC Address.  Or make sure you register your PCI card MAC address in your router if you want MAC filter.
10. Wait for 10 seconds.
11. It should show it is connecting.
12. The first time it may not be able to connect right away so it will ask you for password again.  Simply click okay and open the Network Manager.
13. If you see two entries of the same wireless network you setup in Network Manager, delete the last one.
14. Your wireless should be working now!!!

If you have any question, please post it here and see if I can help.

---

### Post by Newbie447 on 2008-11-18
Tried exactly as you descrobe, it MOSTLY works.:(

The wireless network is detected fine, I can even see it using iwconfig. But when I try to obtain an IP address via DHCP (or entser one manually), nothing. dhclient eventually times out, and all traffic fails. 

Here's how I did things, step by step: (this is an ONBOARD card, btw, so no indicator lights to look at)

> 1. Connect to internet using wired connection.
No Prob. Wired link through the access point is fine.
> 2. Restart your computer if it is running.
Check
> 3. Should see Restricted Driver Manager pop up and click it.
 Check
> 4. It should show it detects your card as Broadcom 4306 v2.0 or similar.
Yep...
> 5. Activate it....
Done...
> 6. Now go to Network Manager.
Ok....
> 7. Create new wireless connection.
Done
> 8. Make sure your wireless settings are correct.
QUADRUPLE checked..... All is correct. essid exactly matches the AP, and all security is disabled on the AP. 
> 9. Make sure your router does not restrict your MAC Address. Or make 
> sure you register your PCI card MAC address in your router if you want 
> MAC filter.
Right. As stated above, no security at all.
> 10. Wait for 10 seconds.
15-20 seconds long enough?
> 11. It should show it is connecting.
[ success ends here]
It shows the connection in network manager, and all looks alright (although I never do get a "connecting" message).

> 12. The first time it may not be able to connect right away so it will 
> ask you for password again. Simply click okay and open the Network 
> Manager.
No password to ask for, so it doesn't. I KNOW wide open isn't safe, but for initial setup it's a HECK of a lot easier!

>13. If you see two entries of the same wireless network you setup in 
> Network Manager, delete the last one.
Only one entry....
> 14. Your wireless should be working now!!!
Nope! dhclient times out. Its not a signal issue because I tested it when I was 2-3 feet from the AP. I'm that far now, but network manager says wlan0 is disconnected.

I tried the "disable wireless" option followed by re-enabling it, no joy.

Help?

---

