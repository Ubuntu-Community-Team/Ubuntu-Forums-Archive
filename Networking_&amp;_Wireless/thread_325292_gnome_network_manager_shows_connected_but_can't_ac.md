---
title: "gnome network manager shows connected but can't access internet"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by learning on 2006-12-25
I'm running edgy on a toshiba laptop (A105-s4254).  Everything has been running fine, using gnome network manager.  For some reason though, today it shows connected to my network, but nothing will access the internet (firefox, synaptic, etc).  I can't think of anything changes that have been made recently.

I booted into Windows and wireless works, so I think I must have messed up my configuration somehow.

I have disabled ipv6, and re-installed gnome network manager, but nothing has made any difference.

Any ideas or tests I should run?

Thank you.

---

### Post by learning on 2006-12-26
bump...

any guesses?  My icon shows it is connected.  iwconfig shows:

lo    no wireless extensions

eth0  no wireless extensions

eth1    IEEE 802.11g   ESSID: "xwing"
          Mode: Managed  Frequency:2.462 GHz  Access Point:  00:0F:66:83:BF:34
          Bit Rate: 54 Mb/s  Tx-Power: 14dBm
          Retry limit: 15   RTS  thr:off    Fragment  thr:off
          Power Management: off
          Link Quality=86/100  Signal level=-48  dBm   Noise level=-48  dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0


but firefox,synaptic,etc... will not connect to anything.

---

### Post by scrooge_74 on 2006-12-26
reboot your router, probably  it lost its dns servers, or you can include your owns and not be dependant on the ISP config

---

### Post by learning on 2006-12-27
That did it scrooge!  THanks, I was banging my head against the wall.   I assumed router was fine because everything worked in windows... I guess it provides it's own dns info?

---

### Post by scrooge_74 on 2006-12-27
Good to hear is working for you now.

I manage to get the passwords to get  into my ISP router here at home, and I took the addresses for the DNS servers he uses plus a few extra ones I added to my PC to avoid this kind of trouble.
I suppose from time to time the ISP  has   problems and the router will loose the DNS servers, your router works as a DNS server for you.   

The router itself acts as a DHCP client to the servers of the ISP so he has to get an IP the same way it leases IPs to your network. So when in doubt, reboot :D

Have fun

---

