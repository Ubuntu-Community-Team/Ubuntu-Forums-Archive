---
title: "cups not working"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by deck on 2008-03-16
I posted in the Dell Support Forum late last night when my brain was a bit fuzzy.  After re-reading, I think this forum is a better place to post.

Here is the issue.  I just upgraded my wife's laptop from the 7.04 from the factory to 7.10.  Now the her computer will not print.  It sees the printers in applications programs but cannot select one to print on. It sees the printers in the  Administration>Printing program.  However, when I try to select one it gives an error that there is a problem with the server.  When I use the CUPS admin through localhost:631/admin to try to print a test page, I get an error page that the server cannot be reached. 

I have 7.10 running on my workstation which is also the print server.  I changed nothing other than accepting some of the security updates to CUPS.   I can print just fine to a Cannon Pixma MP780 and a Brother HL-1240.  Here is the latest cupsd.conf for the sharing of printers

# Enable printer sharing and shared printers.
  Browsing On
  BrowseOrder allow,deny
  BrowseAllow from 192.168.xx
  BrowseAddress @LOCAL
  BrowsePort 631
# DefaultAuthType Basic

I remarked out the authentication line.  I have completely reinstalled CUPS.  I don't have any idea of what is going wrong at this point.

---

### Post by debian-potato on 2008-03-17
Type (in a terminal)

sudo aa-complain cupsd

Enter the user password when asked. This assumes your default user has sudo permissions.

---

