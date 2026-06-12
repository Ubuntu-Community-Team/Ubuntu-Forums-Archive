---
title: "Likewise command with sudo"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by adwatkin19 on 2008-07-01
Hi all

At my work at the moment we are experimenting with Likewise and authentication to the Active directory. We have got it to authenticate the user and log on, but now we wish to use the command:

domainjoin-cli query

to retrieve the details of the Occupational Unit etc, as this is the intention of this command. However we can not not run this command as the user is not part of sudoers. Is there a way (as we dont want to give sudo privilages to all) to run this command just once to put these details into a file that can then be read to mount drives according to the information returned from this. 

Hope someone can help

Adam

---

