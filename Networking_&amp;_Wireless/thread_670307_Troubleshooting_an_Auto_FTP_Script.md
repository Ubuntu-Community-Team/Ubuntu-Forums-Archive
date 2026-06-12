---
title: "Troubleshooting an Auto FTP Script"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by driggins on 2008-01-17
Greetings,

I'm attempting to create a script with copious help from forum users that will automatically upload a specific file to my personal domain. Here are the full contents of the script file:
> #!/bin/sh
HOST=(the IP of my personal domain)
USERNAME=(my user name)
PASSWORD=(my password)
cd /media/data/Shared/CampBrain/
ftp -n $HOST <<EOD
quote user $USERNAME
quote $PASSWORD
cd public_html/campbrain/
put /media/data/Shared/CampBrain/chestnut_ridge2008.mdb
quit
EOD
exit 0

The script has real values for the items in ()'s above.
When I execute this script from Terminal, I get:
> Syntax error, command unrecognized.
Login first, then I might let you do that.
Login first, then I might let you do that.
Login first, then I might let you do that.
ftp: bind: Address already in use

When I step through the script and enter the commands one at a time, I see that the ftp command yields just a ">" symbol. It does not appear to connect to my domain. If I remove "<<EOD" from the ftp command, it does connect to my domain, but the rest of the script pauses. In other words, it does not attempt to automatically login using the user name and password I provided. Any ideas on how to tweak the ftp command?

Thanks,
daryl

---

