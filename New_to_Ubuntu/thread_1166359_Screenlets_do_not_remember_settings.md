---
title: "Screenlets do not remember settings"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-21
The meter and sensors screenlets will not remember their settings and will reset their configuration and position each time I restart. 

If I place them in a certain area again and again, eventually they might remember the position but not the configuration. It was ok a while back but really has been an on and off problem for 1 year.

Anyone else have trouble with screenlets remembering their settings?

Thanks a lot

---

### Post by KhaaL on 2009-05-21
Try this: position the screenlets where you want them, exit the screenlet manager and restart it. maybe they need a "proper" shutdown in order to stick to their place.

I belive this has been an issue with screenlets for a while. I even investigated it when i used screenlets and saw in it's config folder a lot of duplicate setting-files for the screenlets i used. which is a pity, but there are other alternatives

---

### Post by lovinglinux on 2009-05-21
I had the same problem with the sensors screenlets. I did what is suggested in the post above, but exited the manager and restarted it after adding each new sensor screenlet.

---

### Post by Andy06 on 2009-05-21
I'll do that. Could it also be the ext4 acting up and putting its 0s in the config files? Coz I opened them and lo and behold, all the symptoms of the ext4 bug on launchpad.

Also which alternatives were you talking about? I love gadgets and am gutted that Ubuntu/Gnome doesn't have them by default. Mac, Windows and even KDE has them!

gdesklets aren't that great in comparison. Memory hogs, not as pretty, not as functional IMO. adesklets even less so.

Any others I missed? Pls lemme know

---

### Post by lovinglinux on 2009-05-21
> **Andy06 said:**
> I'll do that. Could it also be the ext4 acting up and putting its 0s in the config files? Coz I opened them and lo and behold, all the symptoms of the ext4 bug on launchpad.

I don't think so. This problem only happens with sensors screenlets, including the official, the ring sensors and the circle sensors.

---

