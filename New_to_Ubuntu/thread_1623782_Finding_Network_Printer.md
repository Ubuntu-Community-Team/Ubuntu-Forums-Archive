---
title: "Finding Network Printer"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by jodonald on 2010-11-17
Hey all,
Newbie here looking for some help.  I recently updated to Maverick and am trying to set up my printer again.  I'm using a network printer at my work and can't quite figure it out.  I go to system > administration > printing and expand network printing but no printers are displayed.  I guess this means I need to find the printer but this is where I don't know what to do.  I don't know what the name of the host so I'm not sure how to find the printer.  How can I find out the host name?  I realize this is an amateur question but hey, this is absolute beginner talk.  Thanks.

---

### Post by toekneewood on 2010-11-17
system > administration > printing
Add > Network Printer > Appsocket/HP Jetdirect (Host: 192.168.1.5) <--- This needs to be the IP address of your printer
The host can be the IP address of the printer

---

### Post by jodonald on 2010-11-17
How can I find the ip address for my printer?

---

### Post by toekneewood on 2010-11-17
If you have a HP printer you can get to it from the menu by printing a "configuration page"  from the menu.  Another option is look on your router for DHCP.  when you see the list of IP addresses.  Ping them one at a time until you find the live IP.  Pull the network cable out of the printer then ping it again just to confirm.  Please make sure you do a DHCP reservation for your printer as it could get a different IP address the next time you reboot the printer.  Otherwise your printing will stop working.
Another option is ping the complete range of IP addresses.  Remove the printer network cable and run the fping command again to see what IP did not ping.  You should then have the IP address
```

sudo apt-get install fping
sudo fping -a -q -g 192.168.1.0/24

```

---

