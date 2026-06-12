---
title: "application menu is disappearing"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by degarb on 2010-04-26
I am having problem with ubuntu, when application/prefs by panel at top keeps disappearing.  I don't know how to get it back other than pulling plug on machine and turning back on.

The panels are not disappearing just the three top standard menu items.

---

### Post by conradin on 2010-04-26
try
```

 sudo apt-get install gnome-panel

```
or
```

 sudo service gdm restart

```

---

### Post by _0R10N on 2010-04-26
You could try adding those 3 options (menu bar) on other panel. Just right click on other panel-> add to panel ->menu bar... if this behavior persist then, you should follow the previous post, reinstalling the menu bar can be a lower waste of time!

Kind regards!

_0R10N >>

---

