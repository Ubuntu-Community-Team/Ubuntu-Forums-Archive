---
title: "Main menu shrank?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by benerickson1 on 2010-08-09
Hi. I installed a couple of icon themes from Synaptic, checked them out, then stuck with my original.  I clicked on my main menu and I think the icons/text got smaller.  I never measured it before, but I'm pretty sure my System>Preferences menu extended all the way from the the top of the screen to the bottom.  It just "feels" off.

I went back to Synaptic and removed the new themes to see if it would revert, but the menu is still small.  Anyone have any ideas on resizing it?

---

### Post by martin_legion on 2010-08-23
> **benerickson1 said:**
> Hi. I installed a couple of icon themes from Synaptic, checked them out, then stuck with my original.  I clicked on my main menu and I think the icons/text got smaller.  I never measured it before, but I'm pretty sure my System>Preferences menu extended all the way from the the top of the screen to the bottom.  It just "feels" off.

I went back to Synaptic and removed the new themes to see if it would revert, but the menu is still small.  Anyone have any ideas on resizing it?

First, log off and on again to see if it goes back to normal.
Then, you can try to select some of the default themes and see if they look OK. If they don't, it's possible that you have removed some package containing the default themes.
If this was the case, you can install these two packages to see if it helps:

```
sudo aptitude install gnome-themes-selected gnome-themes-ubuntu
```

---

