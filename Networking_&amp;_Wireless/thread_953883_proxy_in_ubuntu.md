---
title: "proxy in ubuntu"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by davidvandebunte on 2008-10-20
[FONT="Times New Roman"]I'm a relatively new ubuntu user who is trying to add eCos (an embedded operating system) to a system that I have.  I don't have any experience with proxys and was wondering if someone could help me with setting up the following proxy, as asked by the eCos installer.[/FONT]

From Terminal:
Please select GNU tools to download and install: q
Entering /opt/ecos
Retrieving eCos version 2.0

*** wget returned error. Last five lines of wget output:
--16:53:10--  [ftp://mirror.ac.uk/sites/sources.redhat.com/ftp/ecos/releases/ecos-2.0/ecos-2.0.i386linux.tar.bz2](ftp://mirror.ac.uk/sites/sources.redhat.com/ftp/ecos/releases/ecos-2.0/ecos-2.0.i386linux.tar.bz2)
           => `ecos-2.0.i386linux.tar.bz2'
Resolving mirror.ac.uk... failed: Name or service not known.
---------------------------------------------------------
Download failed. Perhaps you need to set a proxy to
connect via a firewall?

Configure a proxy? [Y/n] Y

Proxy hostname:port (e.g. proxy.me.com:3128): 

[FONT="Times New Roman"]
Any suggestions you can give are welcome.[/FONT]

---

### Post by sethvath on 2008-10-20
You do not need a proxy for that. Click on the link yourself, it is down from what I see. The script only suggested you use a proxy because it assumed you're behind a firewall and its blocking access to the site.

---

### Post by davidvandebunte on 2008-10-21
Thanks for the response.  I'm able to download the files separately but this problem is within a tcl script and so I don't really know what to do with the files I download (the script knows all that...).  It looks like the example I put here was one of the broken links in the list of mirrors.  

Added Note: I am doing this connected to my school's network.

For now I'll try to learn how to configure a wgets proxy but having trouble.  If someone knows good guide it would be appreciated, or the real/another solution.

---

### Post by davidvandebunte on 2008-10-21
Problem solved... I was not root... wow...

---

