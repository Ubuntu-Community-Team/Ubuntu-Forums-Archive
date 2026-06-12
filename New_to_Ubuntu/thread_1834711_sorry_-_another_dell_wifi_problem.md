---
title: "sorry - another dell wifi problem"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by soon on 2011-08-28
hiya

sorry..this is my 2nd time asking for a bit of help with this. My wifi for my old dell 131l has stopped working again....its all greyed out in the menu in top of screen. im using unity. I have the correct drivers. rfkill suggests wireless is being blocked but  - rfkill unblock wifi - does not work...it used to.

```
 dmin1@admin1-Latitude-131L:~$ rfkill list0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
admin1@admin1-Latitude-131L:~$ rfkill unblock wifi
admin1@admin1-Latitude-131L:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```I have also used - sudo gedit /etc/rc.local - and the extra rfkill command that i typed earlier to get wifi working permanently  is still there. Does anyone have any other ideas or should i just reinstall unity?

thank, soon

---

