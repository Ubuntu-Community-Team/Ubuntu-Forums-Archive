---
title: "Changing NTP server"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by kirsche on 2006-11-20
Hello,

I'm running Ubuntu 6.0.6.
I've tried to add a NTP server to the list of time sources.
Apparently, the added server isn't saved, since after re-opening the time-admin it's gone again.
Tried running sudo time-admin and adding it this way - same result.

Did someone successfully add a new time server?

Thanks

---

### Post by am4c130d on 2006-11-30
edit /etc/ntp.conf

sudo vi /etc/ntp.conf

or whatever your preferred editing tool is, and add a line similar to 

server ntp_server_source.com

where ntp_server_source.com is your ntp source.

If you are looking for a source I'd recommend using the ntp pool servers as this helps distribute the demand for NTP sources across hundreds of publicly available sources.  They are listed at [http://www.pool.ntp.org/](http://www.pool.ntp.org/) choose multiple that best suit your requirements - geography is a good criteria - though not for any special reason, ntp is designed to cope with link delays.  

The pool uses DNS round robin (I believe) to spread the load, so something like

server 0.us.pool.ntp.org
server 1.us.pool.ntp.org

etc.

Hope that helps.

---

