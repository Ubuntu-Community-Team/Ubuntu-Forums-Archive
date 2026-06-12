---
title: "Can't use &lt;Ctrl&gt;+&lt;Alt&gt;+Arrows"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Bourlog on 2009-07-10
Hello guys! I think it was after i installed Compiz that the switching between desktop's stoped to work. Anyone got any idea why that might be?

Ive tried unchecking all the effects in Compiz but still wont work.

Thanks.

---

### Post by nothingspecial on 2009-07-10
You need to increase the number of desktops in compiz.


```
sudo apt-get install compizconfig-settings-manager 
```

Then go system > preferences > compizconfig settings manager and in the general settings somewhere is the option to increase the number of workspaces. I think its horizontal size or something like that.

Sorry got bored of compiz a while back.

---

### Post by Bourlog on 2009-07-10
Thanks man! :) 

Is there any way to remove compiz? Cus i don't really use it or need it.

---

### Post by nothingspecial on 2009-07-10
```
sudo apt-get remove compiz
```

---

### Post by drs305 on 2009-07-10
> **Bourlog said:**
> Thanks man! :) 

Is there any way to remove compiz? Cus i don't really use it or need it.

You can just run the following to get out of compiz: (System, Preferences, Appearance, Visual Effects tab: None) or in terminal: 
```

metacity --replace

```

If you want you can uninstall compiz with Synaptic.

---

### Post by Bourlog on 2009-07-10
Thanks guys! 

What would you do without these forums? :)

---

