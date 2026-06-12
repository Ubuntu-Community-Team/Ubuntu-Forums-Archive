---
title: "Error starting apache2"
date: 2019-04-25
forum: Networking &amp; Wireless
---

### Post by wilsoncajisaca on 2019-04-25
At the moment of starting apache2, this error is generated.



*root@srv023017:/etc/apache2# service apache2 status*
*&#9679; apache2.service - The Apache HTTP Server*
*Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)*
*Active: failed (Result: exit-code) since Thu 2019-04-25 19:16:16 CEST; 50s ago*
*Docs: [https://httpd.apache.org/docs/2.4/](https://httpd.apache.org/docs/2.4/)*
*Process: 2663 ExecStart=/usr/sbin/apachectl start (code=exited, status=127)*

*Apr 25 19:16:16 srv023017.srv.com systemd[1]: Stopped The Apache HTTP Server.*
*Apr 25 19:16:16 srv023017.srv.com systemd[1]: Starting The Apache HTTP Server...*
*Apr 25 19:16:16 srv023017.srv.com apachectl[2663]: /usr/sbin/apachectl: 174: /usr/sbin/apachectl: /usr/sbin/apa*
*Apr 25 19:16:16 srv023017.srv.com apachectl[2663]: Action 'start' failed.*
*Apr 25 19:16:16 srv023017.srv.com apachectl[2663]: The Apache error log may have more information.*
*Apr 25 19:16:16 srv023017.srv.com systemd[1]: apache2.service: Control process exited, code=exited status=127*
*Apr 25 19:16:16 srv023017.srv.com systemd[1]: Failed to start The Apache HTTP Server.*
*Apr 25 19:16:16 srv023017.srv.com systemd[1]: apache2.service: Unit entered failed state.*
[SIZE=1][I][SIZE=2]Apr 25 19:16:16 srv023017.srv.com systemd[1]: apache2.service: Failed with result 'exit-code'.
[/SIZE]
[/I][/SIZE]The truth and try uninstalling and reinstalling, changing the port and observing the error log of apache in the latter does not generate any error. I hope to have some solution.

---

### Post by TheFu on 2019-04-25
Did you look at the apache log files?  That's mentioned in the output above.  Usually this sort of error is caused by a bad config file/setting which the error will mention.

---

### Post by wilsoncajisaca on 2019-04-25
If I check [COLOR=#000000]apache log files[/COLOR] but I do not generate any error.

---

### Post by TheFu on 2019-04-25
No need to ever post images here for server stuff.  Linux isn't windows.  text is much preferred.


[https://httpd.apache.org/docs/2.4/programs/apachectl.html](https://httpd.apache.org/docs/2.4/programs/apachectl.html)
**sudo apachectl configtest**?

---

