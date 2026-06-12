---
title: "have compiz always start with loose bindings"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-04-19
instead of having to go into terminal and use compiz --replace --loose-binding and then have to keep the terminal window open , is there a way to have loose binding enabled for compiz all the time , like in a config file?

---

### Post by Perfect Storm on 2009-04-19
Have you tried using the "Session". You can find it under System. With Session you can set up stuff you want to auto-start.

---

### Post by lovinglinux on 2009-04-20
You can also use fusion-icon. Just select "Loose Binding" option from it's context menu and add fusion icon to the Session or create a script to launch it. 

I have a script added to Session that includes the following lines:

```
fusion-icon &
emerald --replace &
```

Obviously you could add the loose binding option in the script, but I prefer to set this through fusion-icon options.

Edit: you can also use fusion-icon to set Indirect Rendering

---

### Post by Perfect Storm on 2009-04-20
> **lovinglinux said:**
> You can also use fusion-icon. Just select "Loose Binding" option from it's context menu and add fusion icon to the Session or create a script to launch it. 

I have a script added to Session that includes the following lines:

```
fusion-icon &
emerald --replace &
```

Obviously you could add the loose binding option in the script, but I prefer to set this through fusion-icon options.

Edit: you can also use fusion-icon to set Indirect Rendering

Wouldn't it be easier to use **sh -c "<commands>"** instead? I'm pretty sure you can do that in session.

```
sh -c "fusion-icon && emerald --replace"
```
or what ever you like.

---

