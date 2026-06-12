---
title: "Problem to connect to ssh"
date: 2014-11-20
forum: Networking &amp; Wireless
---

### Post by tho4 on 2014-11-20
Hi everyone,

I am very new to Ubuntu so I seek here for help. I try to connect to CIPRES (Cyberinfrastructure for Phylogenetic Research), following these instructions: [http://www.phylo.org/sub_sections/sge_info](http://www.phylo.org/sub_sections/sge_info)
I don't really understand how it should work, as I cannot connect to the remote server using the command [COLOR=green]ssh cipres1.sdsc.edu[/COLOR]

Could someone help me to understand it ?

Thank you

---

### Post by irv on 2014-11-20
Try this if your user name is cipres1 and the server name is sdsc.edu.
```
ssh cipres1@sdsc.edu
```
If this is correct you should be asked for your password and it will connect.

---

