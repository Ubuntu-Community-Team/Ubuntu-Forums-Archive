---
title: "Nagios on Ubuntu 6.10- &quot;cgi not found&quot; selinux issue?"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by SuperOmegaSlack on 2007-04-18
I have installed Nagios on Ubuntu 6.10, but am having an issue with the cgi files.  When I connect to nagios through http, everything shows up except I get the following error when I try to go to any of the "Monitoring" links:

The requested URL /usr/local/nagios/cgi-bin//*anyfile*.cgi was not found on this server.

I have double-checked the alias in apache2.conf and it is right, all the configs look good as well.

I have been checking forums and all I have found has to do with disabling SELinux, which I think I have done by adding *selinux=0* to grub (menu.lst) and rebooting, but I am having the same issue...does anyone have any Ideas or another way of disabling selinux?

---

### Post by SuperOmegaSlack on 2007-04-18
My problem  seemed to be a permission issue with apache and cgi, after double checking the documentation and not solving anything, I just turned off authentication in cgi.cfg...Now when I click on any of the links that calls the cgi files, it comes up as gibberish.  It looks like what you get if you try to read a binary file.

Stuck again.

---

