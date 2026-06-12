---
title: "Cannot connect to Google anymore"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by cpcgm on 2008-09-22
Since yesterday I can no longer access Google. Neither through VPN to Germany nor directly from China. All Google Sites seem to be affected (google.com, google.de, google.cn, gmail.com, mail.google.com, ...).

If I click on a mail in my already opened Gmail it takes several minutes until it loads. I think it has nothing to do with the router because another (Windows) computer has no problems. Because I can't even access Google via wget (or at least it takes very long) I also think it has nothing to do with DNS. Trying to open the IP in the browser also fails.

```

$ wget -S www.google.com
--18:35:31--  http://www.google.com/
           => `index.html.1'
Auflösen des Hostnamen »www.google.com«.... 66.249.89.104, 66.249.89.147, 66.249.89.99
Verbindungsaufbau zu www.google.com|66.249.89.104|:80... fehlgeschlagen: Connection timed out.
Verbindungsaufbau zu www.google.com|66.249.89.147|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 
  HTTP/1.0 200 OK
  Cache-Control: private, max-age=0
  Date: Mon, 22 Sep 2008 10:38:40 GMT
  Expires: -1
  Content-Type: text/html; charset=ISO-8859-1
  Set-Cookie: PREF=ID=b8579ab8e246ee1c:NW=1:TM=1222079920:LM=1222079920:S=9c_itd5qLaLB_i-S; expires=Wed, 22-Sep-2010 10:38:40 GMT; path=/; domain=.google.com
  Server: gws
  Connection: Close
Länge: nicht spezifiziert [text/html]

    [ <=>                                 ] 5.902         --.--K/s             

18:38:40 (140.76 KB/s) - »index.html.1« gespeichert [5902]

```

---

### Post by cpcgm on 2008-10-03
Does no one have any ideas? The problem disappeared about one week ago and now started again.

---

