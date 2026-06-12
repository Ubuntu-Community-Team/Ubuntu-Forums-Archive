---
title: "Feisty GNOME XP WRT300N networking issue"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by PsyNeo on 2007-06-02
Here's the deal.
I was using a WRT54G. When I was, there were no issues viewing my Windows XP shares. I had not yet attempted creating samba shares in linux.

Now I am using the WRT300N.
WinXP sees WinXP and SAMBA shares flawlessly.
When I attempt to browse to my WinXP shares, I get as far as the list of workgroups, but can't view any hosts or shares, including the samba server on the box I'm on.

I get:

The folder contents could not be displayed.

Sorry, couldn't display all the contents of
"Windows network: <WorkgroupName>".

If I open up pyNeighborhood, I can see the hosts within the workgroups and the shares within the hosts, but I can't mount them.

BUT if I leave pyNeighborhood type in smb://<The IP of the host>, I can see my shares within said host and use them with no trouble.

Anybody know what's going on?

---

