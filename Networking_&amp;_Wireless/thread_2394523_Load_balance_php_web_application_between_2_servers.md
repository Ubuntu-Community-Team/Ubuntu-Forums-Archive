---
title: "Load balance php web application between 2 servers + 1 MariaDB server"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by karentutor1 on 2018-06-18
Hi,

 [COLOR=#454545][FONT=&quot]I would like to try hosting my php web app on 2 servers with Apache behind an nginx reverse proxy and a third server with my MariaDB database.[/FONT][/COLOR][COLOR=#454545][FONT=&quot][FONT=&quot]It is a php website with log in sessions.

[/FONT][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][FONT=&quot]I am a little unclear - do I just have the exact same files on 2 different servers with some session tracking (sticky) load balancing by nginx?[/FONT][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][FONT=&quot]
How do I divide my files?

[/FONT][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][FONT=&quot]Also anyone have any reading suggestions on this? (Server configurations?)

[/FONT][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][FONT=&quot]Thanks![/FONT][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][FONT=&quot]Karen[/FONT][/FONT][/COLOR]

---

### Post by SeijiSensei on 2018-06-18
They will need to share the database so updates in one session are visible to both. Any other content can be duplicated. Alternatively you can have one copy of the content that is shared between the servers vis NFS. You could put the content on the database server and have the web servers both share the files. That does facilitate backups, though it's obviously not redundant.

---

