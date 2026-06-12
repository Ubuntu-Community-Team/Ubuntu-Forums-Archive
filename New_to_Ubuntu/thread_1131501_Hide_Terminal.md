---
title: "Hide Terminal"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by wespawloski on 2009-04-20
I did a quick search through the forum, and didn't come up with anything...

I am running a simple command routing through wine to open an application.
```
 #!/bin/bash
wine /wes/.wine/drive_c/'Program Files'/TheSage/TheSage.exe 
```

The resulting program runs fine, but also creates a static terminal that ties to the life of the application. I would rather not clutter myself with this terminal, and I enjoy running the app through terminal in such a manner. Is there a way I can get rid of this terminal, ghost it, or something? When the application runs through the wine launcher, it requires no terminal.

---

### Post by juancarlospaco on 2009-04-20
#!/bin/bash
wine /wes/.wine/drive_c/'Program Files'/TheSage/TheSage.exe **[COLOR="Blue"]&[/COLOR]**

---

### Post by wespawloski on 2009-04-20
Thank you so much! Now, adding 'exit' on the next line does not cause the terminal to exit, is there a separate code for that? I'm just shakey on what actually needs to happen for the program to initialize correctly :/ thank you.

---

### Post by llamabr on 2009-04-20
You can use the nohup command to keep the app from being killed when you close the terminal.  The & symbol runs it in the background, but will not keep it alive when you close the terminal.

---

