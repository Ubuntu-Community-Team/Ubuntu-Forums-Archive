---
title: "Problem with my DNS file"
date: 2014-11-08
forum: Networking &amp; Wireless
---

### Post by Waheed_Rafiq on 2014-11-08
Hi guys as part of my practical exam next week we have to configure DNS in Linux 

for some reason my  db file is giving me errors

here is what it looks like 

;Zone definition
bostin-t-party.com. IN SOA server.bostin-t-party.com.
waheedrafiq.bostin-t-party.com (
;Do not modify the following lines!
1 ; Serial number
28800  ; Refresh (seconds)
3600 ; Retry (seconds)
604800 ; Expiry (seconds)
38400 ; Negative caching TTL (seconds)
)
;Special records for same servers etc.
bostin-t-party.com. IN NS server.bostin-t-party.com.
bostin-t-party.com. IN MX 10 server.bostin-t-party.com.
; host records
server IN A 192.168.1.5
fred IN A 192.168.1.31


can you spot the error , I can't as I follow my lecture instructors. 

any help would be very much appreciated

---

### Post by Waheed_Rafiq on 2014-11-08
the lastest error message 

[EMAIL="root@server:/etc/bind/zones"]root@server:/etc/bind/zones[/EMAIL]# named-checkzone bostin-t-party.com /etc/bind/zones/bostin-t-party.com.db
/etc/bind/zones/bostin-t-party.com.db:3: unknown RR type 'bostin-t-party.com.'
/etc/bind/zones/bostin-t-party.com.db:4: unknown RR type 'waheedrafiq.bostin-t-party.com'
/etc/bind/zones/bostin-t-party.com.db:13: unknown RR type 'bostin-t-party.com.'
/etc/bind/zones/bostin-t-party.com.db:14: unknown RR type 'bostin-t-party.com.'
/etc/bind/zones/bostin-t-party.com.db:18: unknown RR type 'server'
/etc/bind/zones/bostin-t-party.com.db:19: unknown RR type 'fred'
zone bostin-t-party.com/IN: loading from master file /etc/bind/zones/bostin-t-party.com.db failed: unknown class/type
zone bostin-t-party.com/IN: not loaded due to errors

---

### Post by wildmanne39 on 2014-11-08
Hi, > While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.
Thanks

---

