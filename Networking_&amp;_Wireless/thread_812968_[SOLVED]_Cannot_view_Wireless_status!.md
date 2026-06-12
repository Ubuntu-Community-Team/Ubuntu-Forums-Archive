---
title: "[SOLVED] Cannot view Wireless status!"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by HawkST on 2008-05-30
I accidentally deleted my top panel in Ubuntu, and have got it back the way I like it (with a few additions) - minus the wireless status icon.

I added the Network Manager item to the panel, but that isnt how it looked before... it used to be an icon with four bars which indicated the wireless strength, now its just two computers with a sort of power bar next to it... How can I get the original back?

Edit* Amarok wont show up either when its minimized - what will bring this back?

---

### Post by HawkST on 2008-05-31
I hate to "bump" this topic but its really given me issues, especially the amarok part as now i can only close it in the task manager equivelant.. really need some help here guys

---

### Post by prshah on 2008-05-31
> **HawkST said:**
> I accidentally deleted my top panel in Ubuntu,

I added the Network Manager item to the panel, but that isnt how it looked before... it used to be an icon with four bars which indicated the wireless strength,How can I get the original back?
Edit* Amarok wont show up either when its minimized - what will bring this back?

Looks like you have deleted the "notification area" plugin. Right click your (top) bar, then choose "Add to panel..." then choose the "Notification area" plugin. 

Your amarok (if running) and wireless signal bars should appear instantly. If the signal bars (or equivalent) don't appear, press Alt+F2, then give the command ```
nm-applet
```

---

### Post by HawkST on 2008-05-31
Excellent! Thank you so much! All works fine now - cheers!

---

### Post by prshah on 2008-06-01
> **HawkST said:**
> Excellent! Thank you so much! All works fine now - cheers!

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

