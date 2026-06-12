---
title: "switching back to roaming mode"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2007-08-04
Hi,

In Kubuntu - how do I get the "roaming mode" back, the mode where when you rightclick in shows all the avaliable AP's. All I get now is manual config?

Thanks for any help,

Rudolf

---

### Post by noob12 on 2007-08-04
Is this a new install or you were getting it before?

I'm assuming it is not a new installation and you were getting it before.  I'm also assuming you didn't set up any specific NM profile and that your wireless device is enabled at the hardware switch level.


Try this:  Check the hardware switch has wireless enabled.  Make sure you don't have a stanza for your wireless interface in **/etc/network/interfaces**.  Remove it or comment it out.  (I don't know where the System | Administration | Network panel is in KDE, but that should have the roaming checkbox too.  Editing the file is equivalent and works across gnome and kde.)

Then right-click and Enable Wireless.

---

