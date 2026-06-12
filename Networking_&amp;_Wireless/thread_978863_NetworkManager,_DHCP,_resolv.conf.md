---
title: "NetworkManager, DHCP, resolv.conf"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by tomhorsley on 2008-11-11
How on earth do I arrange to edit the /etc/resolv.conf file after NetworkManager creates it? Traditionally this has been the job of /etc/dhcp3/dhclient-exit-hooks (a well documented, though perhaps obscure script). With NetworkManager, the best I could find is to add a script to /etc/NetworkManager/dispatcher.d/, yet when I do that, and log some info to a log file during the script, I find the script is able to edit resolv.conf correctly, then shortly after my dispatcher script runs, someone, somewhere, re-writes the resolv.conf file again. So where the devil do I define a hook that gets run AFTER NetworkManager has had its way? I need to add multiple domains to the search directive, and there is no support for search lists in the DHCP protocol, so a hook of some kind is my only hope.

---

### Post by VHans on 2008-11-19
Same problem here: every time after booting I have to edit resolv.conf manually.
I would like to know how to configure the dns-servers permanently.

Hans

---

### Post by ciscosurfer on 2008-11-19
You (both) should be able to manipulate **/etc/dhcp3/dhclient.conf** to your liking via static calls.  More on the syntax and parameters understood by this file can be found in **dhclient.conf**'s man page```
man dhclient.conf
```

---

### Post by VHans on 2008-11-19
> **ciscosurfer said:**
> You (both) should be able to manipulate **/etc/dhcp3/dhclient.conf** to your liking via static calls.  More on the syntax and parameters understood by this file can be found in **dhclient.conf**'s man page```
man dhclient.conf
```

Great! Problem solved for me.
I added the OpenDNS servers to the dhclient.conf file. The only thing is that it still adds my router as one of the dns-servers. Any idea on how to avoid this?

---

### Post by superprash2003 on 2008-11-19
well it shouldnt be a problem if your router is listed 3rd or 4th in position.. as only the first or at the most 2nd DNS servers would be used..

---

### Post by VHans on 2008-11-20
> **superprash2003 said:**
> well it shouldnt be a problem if your router is listed 3rd or 4th in position.. as only the first or at the most 2nd DNS servers would be used..

Correct, I'll probably leave as it is now. It works.

---

### Post by baz.g on 2011-06-16
It doesn't look like it will help now as you seem to have sorted your problem but I installed webmin for the first time today and very much recommend it. This could also have solved your problem :-)

---

