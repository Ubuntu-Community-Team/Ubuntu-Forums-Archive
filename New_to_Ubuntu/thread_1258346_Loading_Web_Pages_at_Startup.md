---
title: "Loading Web Pages at Startup"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-09-04
Loading web pages at startup. 

At startup I would like Firefox to open two webpages.

My home page on one workspace.
Rhapsody  on the adjacent workspace.

Is there a way to do this with Startup Applications?

Thanks

---

### Post by Vaphell on 2009-09-04
homepage stuff -
in ff config (Edit->Preferences->General) enter in the home page field: ```
http://page1 | http://page2
```

just set FF to start in startup apps

edit: scratch that, thinking :)

```
firefox -no-remote http://www.google.com
``` should do the trick
no-remote tells to open new window, but i had error that ff is already running :/

in theory you could run 2 firefox instances from startup apps, if not directly you can always write small scripts
but i have no idea how to assign them to proper workspaces

---

