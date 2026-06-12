---
title: "How do I add exceptions to maximus?"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Tykin on 2009-05-29
I recently installed UNR on my Dell mini 9 and I absolutely love it. The whole setup maximizes my viewing space and allows me to efficiently navigate through my applications. 

There is one tiny annoyance. Maximus automatically expands almost every application to full screen, which is usually nice. But for other programs it is unnecessary. 

Some programs such as skype and pidgin are not automatically expanded to fullscreen, which means there must be a way to add exceptions to maximus. Does anyone know how I can add exceptions for programs such as empathy and vlc so that the window is not maximized automatically when launched? 
If possible, please dumb it down for me; I'm still a Linux newbie.

Thank you for the help!

---

### Post by Tykin on 2009-05-29
bump

---

### Post by DeonS on 2009-05-30
You can add an application to the exceptions list for maximus. To do this you need to add the WM_CLASS string for the app to /apps/maximus/exclude_class using gconf-editor

For instance, to find out the WM_CLASS string, start the app, then start a terminal - unmaximise the terminal so that it's on top of the app you want to alter, and type:

```
xprop |grep WM_CLASS
```

Click on the window of the app you want to identify.
An example of the output will look something like this.

```
deons@shadow-blade:~$ xprop |grep WM_CLASS
WM_CLASS(STRING) = "totem", "Totem"
```
Copy the string id inside the quotes. e.g. Totem

Add that (without the quotes) using gconf-editor to /apps/maximus/exclude_class (double-click on the key, and choose Add"

It should start working straight away without logging off or rebooting...

---

### Post by Tykin on 2009-06-06
Thanks for the help! What you described worked perfectly!

---

### Post by puttux on 2009-08-05
This has been a great help. Thanks a lot.

---

### Post by Peacepunk on 2010-09-16
Note (to self, actually):

gconf-editor doesn't require root/sudo rights. Just edit the gconf value from your user account, with normal privileges.


Otherwise, well, you'll just give the root account a special value that the normal user will never benefit from.


Dumb me.

):P

---

