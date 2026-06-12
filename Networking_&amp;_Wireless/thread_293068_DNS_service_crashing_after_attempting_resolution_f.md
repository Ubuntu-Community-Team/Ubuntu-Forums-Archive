---
title: "DNS service crashing after attempting resolution from Ubuntu workstation"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by revisrev on 2006-11-04
I've done a few Google searches and searched this forum for an answer to this question but keep coming up short.

I am running Ubuntu Edgy, fully updated, on my Dell Inspiron 6400 Notebook.  It works really well at home, but, when I go to the shop, where we are running a Windows Server 2003 Network with dns and dhcp services I constantly crash the dns service on the server causing a need for a restart of the services.  Even after restarting the services the problem persists.

Here's what happens.  I connect to the network and receive an address no problem.  Then I open up firefox and go to Google.  Google comes up all right usually.  Then I attempt to go to a second domain, like MSN or Yahoo.  At this point I get an error that says it can't find the site.  When I go to a Windows Workstation right afterwards it too cannot access anymore websites unless I type the IP address instead of the domain.  Then I go to the server and try to ping these domains.  The address that it is resolving for them is 0.0.0.1, I believe.  So, then I go to services and restart DNS Server and DNS Client on the server machine.  At this point I can go back to one of the Windows workstations and surf the net no problem, until I go back to my Ubuntu machine and try again, at which point the DNS service crashes again and we start over.

I'm really scratching my head on this one and hope that somebody could help me out.  Thanks in advance for any help.

---

### Post by stream303 on 2006-11-13
warning: Total Speculation on my part:

I wonder if the same problem exists when using only IPV4 instead of IPV6?  (In firefox, about:config in url bar, filter for IPV6, toggle boolean state to TRUE, restart firefox)

Maybe try global IPV6 disable:
Create /etc/modprobe.d/bad_list
with only one line in it:
alias net-pf-10 off

restart networking

again, this is just crystal-ball on my part...

---

