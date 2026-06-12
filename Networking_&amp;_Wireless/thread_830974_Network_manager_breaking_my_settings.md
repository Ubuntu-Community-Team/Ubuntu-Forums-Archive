---
title: "Network manager breaking my settings"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by stuckdoingwork on 2008-06-16
Hi,

I have a laptop (Dell latitude D620) running Ubuntu 8.04 (Gnome) with all the latest and greatest updates, but the network manager is being a bit mischievous.  It keeps changing my settings, and not in a good way!

At work I have a static IP wired connection which needs a gateway and DNS servers, etc.  I also have a wireless card which I use with DHCP both at work, and also when I bring the laptop home.  When everything is configured properly, everything works just fine.

BUT:

If I bring the laptop home and switch on the wireless, my DNS server is automatically set to 192.168.1.1, which is correct for my router.  But this removes my static DNS servers required for my wired connection, and when I bring my laptop back to work, I no longer can connect and have to reset the DNS manually.

Then it seems like every time I change something in the network manager (like re-adding the DNS servers), it tries to 'fix' my hostname/domain/aliases.  My hostname is nlinfit and domain is mit.edu, so I believe my /etc/hosts should read something like:

127.0.0.1 localhost nlinfit.mit.edu
127.0.1.1 nlinfit

If I don't have at least one alias as 'nlinfit' and one as 'nlinfit.mit.edu' then Gnome gets slow and things like 'sudo' seem to hang.  But after I mess around in the network manager, it replaces every single 'nlinfit' alias with 'nlinfit.mit.edu' and I'm stuck with a broken computer again, until I manually edit /etc/hosts.

Any ideas?  Thanks!

---

### Post by superprash2003 on 2008-06-16
to permanently set DNS servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. opendns servers used in this example!!

---

