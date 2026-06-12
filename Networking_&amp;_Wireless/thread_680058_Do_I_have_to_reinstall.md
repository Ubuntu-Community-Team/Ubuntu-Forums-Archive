---
title: "Do I have to reinstall??"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by ncreek on 2008-01-27
I have been having fits trying to network to a win workgroup. in all my thrashing and trashing around yesterday I somehow deleted all the hosts that used to show in my network icon in the panel. Now my printer which is set up as a network printer, even though I haven't got the network functioning yet, isn't working. I am not sure how all the hosts that where there before are now gone, but they are. Bottom line am I in trouble? Can I simply reset/reinstall the network portion of Ubuntu or is a complete install needed?

---

### Post by Mikecore on 2008-01-27
most likely you can just reinstall ( samba ) which is what you use for networking with a windows network. Just make sure you remove all the old configuration files after removing samba they are located in "/etc/samba" 

in a terminal type 

```

sudo rm -fr /etc/samba

```

then re-install samba. using your add/remove programs tool.

---

