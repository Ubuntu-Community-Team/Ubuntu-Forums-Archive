---
title: "Finding a GAL with DIG :)"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by darknomel on 2011-02-21
Hi All,

I'm in the process of testing Evolution and Thunderbird for use as a replacement for Outlook. I've basically got everything setup but I can't find my companies global address list? I remember there was a way to get it with DIG using a couple of switches, does anyone know it?

Thank you,
Michael

---

### Post by An Sanct on 2011-02-21
That was a slightly misleading thread name :)


[LIST=1]
[*]First off, get your Global Address Book server name. In Outlook,  Tools > Address Book. Then right-click on "Global Address List" that  appears in a drop-down menu and select "Properties". Copy the server  name under "The current server is:".
[*]In Thunderbird, Tools > Address Book
[*]File > new > LDAP Directory
[*]In the General tab, name it whatever you want to, and paste the server name into the "Hostname" area.
[*]Base DN is going to be the stuff after junk separated by commas  and set equal to dc. For example, using junk.work.com as your server  name it would be dc=work,dc=com
[*]Port number = 389 (default) then ok.
[/LIST]
also, don't be afraid to ask your admin for details, ports and other settings may vary...

---

### Post by darknomel on 2011-02-23
Thank you, that sorted it :) Apologies for the misleading thread name :)

---

