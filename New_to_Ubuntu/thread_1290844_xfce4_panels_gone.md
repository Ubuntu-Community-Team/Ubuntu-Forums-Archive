---
title: "xfce4 panels gone"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by IX_9 on 2009-10-14
I seem to have an issue with xfce panels disappearing in xubuntu. I hadn't done anything special, they were just gone when I  booted up my machine today. I noticed several old threads that suggested opening a virtual console (ctrl+alt+f2-6) and then running:

```
xfce4-panel
```

I tried this, however, my computer gave me an error reading: 

xfce4-panel: cannot open display:

I also tried to run the command with sudo, just in case there was some sort of permissions issue. It didn't help, I get the same error.

I understand that the issue is that xfce saves it's settings on logout and that now that panels are gone it automatically saves them as not being there. What I'm not sure about is: A) Why they went away in the first place and B) how to get them back. Any help would be greatly appreciated.

Also I'm running Jaunty 9.04

---

### Post by anonymous_user on 2009-10-14
Press Alt+F2 and run xfce4-panel

---

### Post by IX_9 on 2009-10-17
> Press Alt+F2 and run xfce4-panel

Thanks that worked like a charm.

Everything seems to be back to normal except the places menu is gone (and I can't add it back by right clicking and choosing add new items) and the logout button no longer asks me whether I want to logout, shutdown, etc. It just automatically logs me out. This isn't a major issue since I can shutdown from the login screen, but it is annoying.

Any ideas on either of those? Help would be much appreciated.

---

### Post by anonymous_user on 2009-10-17
Make sure "xfce4-places-plugin" is installed. If it already is, try uninstalling then reinstalling.

---

### Post by linux phreak on 2009-10-18
Hello.For your logout problem,make sure that "prompt on logout" is checked.It's in Applications>Settings>Sessions and Startup>General tab.

---

### Post by IX_9 on 2009-10-18
Thanks everyone
> Make sure "xfce4-places-plugin" is installed.

and 

> make sure that "prompt on logout" is checked.It's in Applications>Settings>Sessions and Startup>General tab

fixed everything up. Thanks for the help!

---

