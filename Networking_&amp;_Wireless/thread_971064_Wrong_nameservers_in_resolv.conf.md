---
title: "Wrong nameservers in resolv.conf"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Tycho_ on 2008-11-04
Hi all.

I recently installed Kubuntu 8.10 from scratch on my Dell inspiron 1525 laptop. I started experiencing problems with my connection as firefox and other applications were very slow at resolving domainnames. This was regardless of whether i was plugged in via my ethernet or wireless card, whether i was at home or at my university and whether i let knetwork-manager handle the connection or i did it manually.

The culprit seems to be resolv.conf as, apparently, it gets updated with incorrect nameservers when i connect to a network. The odd thing is that 2 of the 3 nameservers listed are always the same and seems to point to my university, even though i am not connected to their servers directly from home (or from anywhere else for that matter). The third nameserver seems valid and when i remove everything else from the file, the long lookups vanish. Still, i have to do this every time i connect to a new network.

I'm quite baffled at why the nameservers of my university somehow end up in the resolv.conf file, no matter where i am. Any suggestions as to what could causing this would be greatly appreciated.

Cheers

---

### Post by adieb on 2009-01-26
exactly the same problem here! always need to cut the frist two entries from /etc/resolv.conf.

Any solution yet?

---

### Post by Iowan on 2009-01-26
If you're using DHCP to get an address, check contents of /etc/dhcp3/dhclient.conf.  **dhclient** *requests* DNS servers from DHCP server.  This behavior can be modified by editing the "prepend" line in that file.

---

### Post by adieb on 2009-01-27
well, i thx for the dhclient thing. but it correctly adds the new dns entries. that works. but it didn´t override the old ones.
I searched trough the /etc files and i found /etc/resolvconf/run/interface/* there were these wrong addresses hardcoded. i deleted the wrong entries and now it seams to work.

It was written in eth0 and NetworkManager.

---

### Post by Iowan on 2009-01-27
Glad you found it! Gotta admit, I probably wouldn't have looked there.

---

### Post by adieb on 2009-01-28
very strange indeed. what do you think? is worth a bug report? the problem might be the difficult recreation of the false entry-situation....

---

### Post by jevel on 2009-02-01
I had the same problems and this solution worked for me as well.

-KJ

---

### Post by jimtristate on 2009-02-01
I have what I think is a related issue just after upgrading from 8.04 to 8.10.  My Network Manager applet seems to record and store the correct manual setup info, but on reboot the system uses dhcp anyway (and hangs for a long looonnngg time on bootup at the "configuring network" step). 
I'm going to check the above mentioned files.

I can ping an address but not a domain name.

---

### Post by wlraider70 on 2009-02-03
Maybe someone can help me figure this out or make sure that I have it straight. 

I use the /etc/network/interfaces to over ride the GUI network manager.

However, the file /etc/resolv.conf file is overriding my interfaces by taking a DNS address from my network manager? the message that says generated from network manger, right?

So I need to fix this by editing /etc/resolvconf/run/interface/???
i think.

---

### Post by pdtpatrick on 2009-02-04
you are editing /etc/network/interfaces because you want it to be DHCP or static? if its going to be DHCP then you dont need to edit the file since its going to query your DHCP and get an IP upon bootup. However if you are using static then once you have correct setup the /etc/network/interfaces, it will stick to that ip and look in /etc/resolv.conf for your dns servers.

---

### Post by donchichi on 2009-09-16
I have this issue in 9.04 Jaunty as well. Really weird. My DNS were going to 193.x.x.x I don't even know that DNS server. 

I had a problem where I could go to all the sites except for [www.youtube.com](www.youtube.com) I thought it was an ISP problem but after a week only I started looking into this. 

Thanks, this post helped me find the issue faster.

cheers

---

