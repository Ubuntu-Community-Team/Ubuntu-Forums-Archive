---
title: "grub network submenu source code"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by synhedionn on 2013-12-12
hi,
With normal boot, I've no network
But if Recovery Mode>network : sucessful network
So do you know what is the source code under the Network submenus?

---

### Post by chili555 on 2013-12-12
I am fairly confident that networking is called up by *nm-cli* in rescue mode and by Network Manager when you boot normally; unless, of course, you have removed Network Manager. The fact that it starts normally in rescue mode but not otherwise suggests, pretty clearly, a misconfiguration in the settings for Network Manager. 

When you right-click the NM icon and select 'Edit Connections,' are there settings you have set up manually? Ordinarily, NM will handle all these details for us without any outside intervention.

Is 'Connect automatically' checked? 

Are there any clues here?```
cat /etc/network/interfaces
cat /var/log/syslog | grep etwork | tail -n20
```Are you having trouble with wired or wireless?

---

### Post by synhedionn on 2013-12-16
Thank you for your clues.
I'll investigate further on them. It's easy to have source of packages, but not on boot CDs!Pity!
In fact : I have to strike dhclient -r ; dhclient to have the network.

---

