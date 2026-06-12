---
title: "ssh X11 GUI file browser"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by rohams on 2011-05-05
Hey!

I can run firefox from a server through ssh (X11 enabled), by just running the code "firefox&",  I was wondering if there is a shortcut to call a graphical file browser as well to browse the server's hard-drive. 

I am new to Ubuntu and command line. 

Thanks

---

### Post by HermanAB on 2011-05-05
nautilus

---

### Post by nothingspecial on 2011-05-05
If you just type nautilus you may get the whole desktop, depending on which version you are using.

If that happens launch it like this

```
nautilus --no-desktop
```

Then you'll just get the browser. Might not matter in 11.04. I think compiz handles the desktop, but I could be wrong..........

---

### Post by The Cog on 2011-05-05
And you will find that firefox will open a new local firefox window if firefox is already running locally. To be sure of getting a remote firefox process, use
> firefox --no-remote &

---

### Post by rohams on 2011-05-05
Thanks for your help.

---

