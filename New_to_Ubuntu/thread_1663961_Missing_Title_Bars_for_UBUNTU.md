---
title: "Missing Title Bars for UBUNTU"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Its_Rishi on 2011-01-10
Unexpectedly i removed compiz,metacity & window manager from 

system>preferenes>main menu>others

Now after restart no title bars were displaying and not minimizing,maximizing, not working show windows
and it displays the following error;

"Your window manager does not support the show desktop button,or you are not running a window manager.

---

### Post by oldos2er on 2011-01-10
Try ```
metacity --replace
```

---

### Post by Its_Rishi on 2011-01-10
> **oldos2er said:**
> Try ```
metacity --replace
```

I did that but no use...

---

### Post by [Snc] on 2011-01-10
I had the same problem a while ago..., reinstalling metacity helped. (or any other "decorator" you might use)

1. Reinstall metacity ```
apt-get install --reinstall metacity
```2. run 
```
metacity --replace
```3. reboot machine

note: if at any point you cannot access to the menu: 

you can get to the terminal with 
```
Ctrl + Alt + t
```or run a command/application with
```
Alt + F2
```

---

### Post by Its_Rishi on 2011-01-10
> **'[Snc] said:**
> I had the same problem a while ago..., reinstalling metacity helped. (or any other "decorator" you might use)

1. Reinstall metacity ```
apt-get install --reinstall metacity
```2. run 
```
metacity --replace
```3. reboot machine

note: if at any point you cannot access to the menu: 

you can get to the terminal with 
```
Ctrl + Alt + t
```or run a command/application with
```
Alt + F2
```

I Can't understand but i tried it doesn't working...

---

### Post by [Snc] on 2011-01-10
Ok, please read through this article: 
[http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html](http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html)

See if it can help.

ps. i allready PMed you to tell me what kind of error you get.

---

### Post by Its_Rishi on 2011-01-10
Nothing is working after reboot everything will be gone
im activating by right click on the empty desktop>change desktop background>visual effects>extra
then it will download drivers every time and the previous effects will be enabling this is all for temporary only not for permanent :(

---

