---
title: "Panel application is crazy"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by am65 on 2009-12-18
Hello,

I was playing a bit with the panels of the deskop (created a new panel, changed its properties) and I don't know what I did that the panel application got crazy:

The top bar (with the applications menu, logoff button, etc...) is gray and shows no button or menu.

The bottom bar (with the show destop button) is not visible neither.

I thought, ok I restart the system and everything it will be fixed. Before restarting I got a message saying: "Panel application is not responding..." or something like that. Anyway I went on with the restarting.

But for my surprise the same thing happens again. I cannot see the top and bottom bars and so I cannot use any application. And this panel application seems to be 100% on the CPU because the ventilator is working like crazy. I could launch the Firefox because I created a launcher in the destkop. If I want to shut down I have to do it with the hardware button.

If I login as root everything works.

How can I fix this?

Many thanks.

---

### Post by joes7 on 2009-12-18
[for xubuntu]
Open a terminal and write:
```

xfce4-panel

```
Panels should be visible. DO NOT CLOSE THE TERMINAL and shut down, making sure that you tick "Save session".

Voila.

---

### Post by Extract_Here on 2009-12-18
are you using Karmic or juanty?

---

### Post by mikodo on 2009-12-18
Here's another thread with similar concerns. Maybe it can shed some light for you; I think it helped me in the end.

[http://ubuntuforums.org/showthread.php?t=1353223](http://ubuntuforums.org/showthread.php?t=1353223)

Mike

---

### Post by UbuntuNerd on 2009-12-18
> **am65 said:**
> Hello,

I was playing a bit with the panels of the deskop (created a new panel, changed its properties) and I don't know what I did that the panel application got crazy:

The top bar (with the applications menu, logoff button, etc...) is gray and shows no button or menu.

The bottom bar (with the show destop button) is not visible neither.

I thought, ok I restart the system and everything it will be fixed. Before restarting I got a message saying: "Panel application is not responding..." or something like that. Anyway I went on with the restarting.

But for my surprise the same thing happens again. I cannot see the top and bottom bars and so I cannot use any application. And this panel application seems to be 100% on the CPU because the ventilator is working like crazy. I could launch the Firefox because I created a launcher in the destkop. If I want to shut down I have to do it with the hardware button.

If I login as root everything works.

How can I fix this?

Many thanks.

if you don't mind can you try making another launcher only this time make it for a "terminal" and type this code:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
it should reset and restart your panels, then restart to see if it work.

---

### Post by joes7 on 2009-12-18
Hmm. So the problem persists. Well, I suggest you use my guide (I guess we can call it a guide). Click on the following link.
```

http://ubuntuforums.org/showthread.php?t=1349997

```

---

### Post by mikodo on 2009-12-18
> **joes7 said:**
> Hmm. So the problem persists. Well, I suggest you use my guide (I guess we can call it a guide). Click on the following link.
```

http://ubuntuforums.org/showthread.php?t=1349997

```

How do we get to this thread? 

Answer: Copy it and enter in the address bar of your browser.

Mike

---

### Post by mikodo on 2009-12-18
> **UbuntuNerd said:**
> if you don't mind can you try making another launcher only this time make it for a "terminal" and type this code:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
it should reset and restart your panels, then restart to see if it work.


This is interesting. To make sure I understand this, I should right click on the desktop, create a launcher for terminal to run this code. The next time I loose my panels I can use this launcher icon on my desktop to run the reset panel code, then reboot to finish the fix.

Is this correct?

Mike

---

### Post by joes7 on 2009-12-18
> **mikodo said:**
> How do we get to this thread? 

Answer: Copy it and enter in the address bar of your browser.

Mike

I hope you are joking.

---

### Post by am65 on 2009-12-19
In the end I logged on as root and then I deleted everything in the folder of the problematic user:

/home/.../.gconf/apps/panel

I logged again as normal user and the problem was gone. Gone were also many other things, but life is risk.

Thanks to all for your help.

---

### Post by Pierrot Lafouine on 2009-12-23
> **UbuntuNerd said:**
> 
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```


Thanks, this works for me, I had a similar menu problem.

---

