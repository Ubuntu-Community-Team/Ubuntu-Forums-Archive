---
title: "Linux-Windows network not working"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by linux50 on 2007-05-21
Greetings all, I've checked but can't see my exact problem replicated on the forum - so here goes;)

Wanting to share documents between Ubuntu and Windows, I've set up a shared folder in Ub and also in Windows I can see the Ubuntu pc - however when I go to access the Windows Network and the Ub folder I get a message that I don't have network permissions to access the Ub pc - aghhhhh I've looked around the options but just can't see the way to give access to Ub from the Windows pc - when I try to access MSHOME which appears on the Ub pc it just says "sorry unable to show all the folders on the network resource...."

I would be very grateful for any ideas or urls for dummies that can be provided, thanks:D

---

### Post by ym4546 on 2007-05-21
perhaps a copy of your smb.conf would be helpful... what version of samba are you using.

---

### Post by RawMustard on 2007-05-21
Are you using the same username and password on both machines when you login?

---

### Post by adewale on 2007-05-21
i've had a similar problem. i tried connecting two windows pcs together. on the pc i could view the laptop's files, but the laptop couldn't view mine so i kept playing around until i disable firewalls and intrusion prevention  but still the laptop couldn't see the pc so i decided un enter the pc's shared folder address in the explorer bar on the laptop and it worked

---

