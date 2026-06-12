---
title: "Firefox Addons Are Leaving Settings in about:config"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-06-05
When I remove a firefox addon it leaves settings in about:config

How do I uninstall all the settings it changed in about:config?

Thanks in advance.

---

### Post by GMachine_24 on 2009-06-05
the url disappeared

---

### Post by pluckypigeon on 2009-06-05
> **GMachine_24 said:**
> [http://kb.mozillazine.org/About:config#Opening_about:config](http://kb.mozillazine.org/About:config#Opening_about:config)

Thanks but that's not what I'm looking for.

I want to remove the addons with the about:config entries it leaves behind

---

### Post by pluckypigeon on 2009-06-05
One addon I uninstalled left Firefox full of crap in about:config

It also effects the way firefox utilises google search.

---

### Post by GMachine_24 on 2009-06-05
Hi: I'm not sure if there is a way to remove everything that a plug-in or add-on changed.

This is a general how-to but Mozilla says you might not remove all changes created when the add-on was installed:

[http://kb.mozillazine.org/Uninstalling_extensions](http://kb.mozillazine.org/Uninstalling_extensions)

You can try to reset the settings...

[http://kb.mozillazine.org/Resetting_preferences](http://kb.mozillazine.org/Resetting_preferences)

but I'm not sure if that's what you want to do.

--gm

---

### Post by kerry_s on 2009-06-05
in about: config just right click> reset

if theres a lot i go straight for the ~/.mozilla/firefox/*/prefs.js
just open it with your editor and delete the lines you don't want.

---

### Post by pluckypigeon on 2009-06-05
Thanks everyone. 

What I did was rename user.js and pref.js

about:config is now clear of all the old addons and firefox seems to be running smoother.

Nothing much changed on the reload, as far as I can see, apart from noscript settings.

Thanks!!

---

