---
title: "Dragging windows onto workspaces"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by da burger on 2010-04-30
In karmic I could drag a window off the side of the screen and it would appear in the next workspace. This doesn't appear to happen in lucid so does any one know how to turn it on?

---

### Post by swoll1980 on 2010-04-30
> **da burger said:**
> In karmic I could drag a window off the side of the screen and it would appear in the next workspace. This doesn't appear to happen in lucid so does any one know how to turn it on?

install compiz settings manager. You can adjust all your compiz setting there. 
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by tonsil on 2010-04-30
Great question. I was thinking about the same thing today. The only way I figured how to do it is to click top left of the software and choose "move to workspace right". But it was definetely easier in Karmic. Perhaps it's possible under 10.04?

---

### Post by derande on 2010-04-30
System > Preferences > CompizConfig Settings Manager > Desktop > Desktop Wall > Edge Flipping Tab > Select "Edge Flip Move"

---

### Post by da burger on 2010-04-30
> **swoll1980 said:**
> install compiz settings manager. You can adjust all your compiz setting there. 
```
sudo apt-get install compizconfig-settings-manager
```

I had a look but I didn't see a plugin that looked like it would help. Could you be more specific?

EDIT:

> **derande said:**
> System > Preferences > CompizConfig Settings Manager > Desktop > Desktop Wall > Edge Flipping Tab > Select "Edge Flip Move"

Thanks a lot that worked perfectly.

---

### Post by tonsil on 2010-04-30
I'm searching for this function at compizconfig settings but couldn't find which one it is. Well, which one is it?

---

### Post by tonsil on 2010-04-30
Thanks!!

---

### Post by JokarMan on 2010-05-01
I was looking for the same issue, Thanks a lot :)

---

### Post by sunbird on 2010-05-01
I've followed these instructions but still can't drag to neighboring workspaces... Any help appreciated...

thx!

**Edit** Never mind. I had been running cfsm as root. Duh!

---

### Post by pjones0404 on 2010-05-03
Worked like a champ. Thanks for the tip.

---

