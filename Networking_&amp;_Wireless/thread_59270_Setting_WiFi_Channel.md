---
title: "Setting WiFi Channel"
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by menawollas on 2005-08-23
Just run the live CD, and everything was fine, but I don't understand one thing.

When I set up my network card, from the administration menu, I can set my SID, my encryption key, my IP (don't want DHCP) my name server, my gateway...  - much easier than Knoppix.

BUT.

There don't seem anywhere to set the Channel. So I have to open a root shell and type iwconfig ath0 channel 11 before I can connect to my router.

How come channel was missed out in the easy setup ????

---

### Post by Juergen on 2005-08-23
I think the driver should find the right channel itself (it does in my 'normal' installed Ubuntu)
Don't know why this doesn't work for you and the live-CD

---

### Post by poetic_folly on 2005-08-23
Which WiFi adapter are you guys using? I have a Belkin 54g USB 2.0 Wireless adapter (f5d7050) and I have been trying for days to get Ubuntu to recognize it and let me online! 

I am about to go out and just buy a new adapter, and if that doesnt work, head back to XP with my tail between my legs.  :(

---

### Post by s_p_a_r_k_y on 2005-08-24
get an adapter with the prism2 chipset. SOme googling and you'll find some cards that work great with linux.

---

