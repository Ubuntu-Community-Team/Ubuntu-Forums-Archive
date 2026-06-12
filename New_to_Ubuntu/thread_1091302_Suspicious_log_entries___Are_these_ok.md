---
title: "Suspicious log entries ?  Are these ok ?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-09
Im 100% sure that noone was at the computer when this was logged...but it concerns me.  Are these logs something I should worry about?


Mar  9 07:44:15 MWServer sudo:     root : TTY=unknown ; PWD=/ ; USER=engineer ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Mar  9 07:44:16 MWServer sudo:     root : TTY=unknown ; PWD=/ ; USER=engineer ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Mar  9 07:44:16 MWServer sudo:     root : TTY=unknown ; PWD=/ ; USER=engineer ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port


My login is engineer by the way but I did NOT do these changes indicated by the logs

---

### Post by binbash on 2009-03-09
Are you using proxy?These logs are ok

---

### Post by mistypotato on 2009-03-09
As far as I know,

I am NOT using proxy

---

### Post by binbash on 2009-03-09
First one checks if you are using a proxy or not
The other ones are pulling the proxy host and port

alt+f2 and write gconf-editor and when it opens ;

go to system/http_proxy

and check if they are ok

---

