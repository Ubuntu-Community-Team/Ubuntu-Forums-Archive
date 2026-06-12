---
title: "[SOLVED] ubuntu doen't see other ubuntu's samba shares"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by eotakos on 2008-10-18
obviously, it's either that, or i don't know how to do it! :-)

actually, i'm putting it this way because i have a vista pc that works fine with both printer and "home directory" samba shares.

at first, -with the client ubuntu system- i would go to places->network and it wouldn't show me the ubuntu "server" system (by the way, neither windows would show me the server by browsing - but with the ip worked just fine).

To continue with the ubuntu client, then i clicked places->connect to server, then chose "windows share", then put in the ip of the server but no luck.

now, in the client machine, i altered the workgroup in the /etc/samba/smb.conf to match the name of the server, and when i went to places->network and click the "windows network" icon, the gnome freezes :-(  and i have to kill it from tty2

any idea what i'm doing wrong?? 


 maybe someone can also post a link where i can read about the carious network setups (i.e. workgroups, domains etc) because i have kind of mixed them up in my mind and i'd like to have a more clear idea about what's going on...

thanks in advance

---

### Post by eotakos on 2008-10-18
ok - the thing that i did wrong is that i didn't specify the share when i was trying to "connect to server"... so if the share is the home directory, you put the user name in the share querry

---

