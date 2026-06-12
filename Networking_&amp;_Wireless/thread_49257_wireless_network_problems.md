---
title: "wireless network problems"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by Lancey Lot Link on 2005-07-15
Ok, I have a linksys wireless router and a linksys wireless bridge. I want to get this computer wirelessly connected to the router, but I just cant figure it out. Can someone please just explain to me, as if i were a child, what i need to do.  ](*,)

---

### Post by Lunde on 2005-07-15
What's the full model description of your wireless card?

---

### Post by Lancey Lot Link on 2005-07-15
I've got this Linksys WET11 wireless-B ethernet bridge.

---

### Post by Lunde on 2005-07-15
And this is just plugged into your network adapter right? This should according to Linksys not need any special drivers. Are you able to see your Network adapter in ifconfig?

In terminal just type **ifconfig** and press **Enter**

If you can see your network card (**lan0** or similar, not the **lo**) then try to open 
Gnome menu: **System -> Administration -> Networking**

Choose your network connection and probably set it to **DHCP** and click **Activate**

---

