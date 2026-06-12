---
title: "Ubuntu Software Centre not starting"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by julz87 on 2010-07-22
Hi Guys, i've got a problem with my computer. Its a lenovo x60s laptop with a pretty fresh install of Ubunto 10.04. Previously the software centre was working, now when i click it i just see the icon at the bottom of the screen and it disappears shortly after. Any ideas on how i can get it to work?

---

### Post by ubunterooster on 2010-07-22
Start it in the terminal by typing ```
/usr/bin/software-center
```

If it crashes, it will likely give info, which you can paste below

---

### Post by julz87 on 2010-07-23
> **ubunterooster said:**
> Start it in the terminal by typing ```
/usr/bin/software-center
```

If it crashes, it will likely give info, which you can paste below

Thanks for the reply
Here is what the terminal says..
julian@julian-laptop:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment

---

### Post by julz87 on 2010-07-25
anyone?

---

### Post by crutch on 2010-07-25
Hi, I'm not sure what is going on here, (aside from the fact that a varible is somehow being referenced before its assignment). Could you check if  synaptic still works as it's supposed to (under system>administration)

---

### Post by julz87 on 2010-07-25
Hey guys, just ran the update manager and i guess it must have fixed something because it works now. 
thanks

---

### Post by SunnyRabbiera on 2010-07-25
Indeed, synaptic should be easy enough to use anyway if you are famillair with the software center.
But do make sure you are not running an update in the background

> **julz87 said:**
> Hey guys, just ran the update manager and i guess it must have fixed something because it works now. 
thanks

It might have been this update that was causing your issue, keep synaptic in mind in the future, ubuntu software center is good for beginners but synaptic does offer a bit more.

---

