---
title: "MIssing Buttons"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by tybrownintn on 2011-02-18
I googled this and found one answer that simply does not work well for me.  The min, max and close buttons are missing from all my windows.  I had installed the emerald theme manager and all was fine.  Restarted a few times with no trouble.

Now the buttons are missing.  One suggestion I saw was 
```
metacity --replace   
```which works but seems to mess up compiz as the awn window navigator got all 2d and ugly.

I am running Ubuntu 10.10.  What I would like to do is just forget about emerald (which I uninstalled to no effect) but have compiz running and also some nice buttons...left or right, makes no difference to me which side they are on.

---

### Post by tybrownintn on 2011-02-18
It is definitely compiz that is the issue.  Uninstalled compiz and rebooted, looked nice.  Then reinstalled, still ok but when I go in the effects settings from "none" to "normal" the buttons disappear.  Does this help narrow down the issue?

---

### Post by sikander3786 on 2011-02-18
Yes it is definitely compiz. Compiz is known to have some issues like these. You can simply try reloading compiz or can install fusion-icon.

```
compiz --replace
```

Install compiz-fusion icon.

Applications > Accessories > Terminal:

```
sudo apt-get install fusion-icon
```

Start from Applications > System Tools > Fusion Icon and use from system tray. Right click and choose your Windows manager, theme manager etc. You can use it to reload the current one i.e, compiz incase it starts acting weird.

---

### Post by tybrownintn on 2011-02-18
Hmmmm....I thought this had fixed it. but logged out and back in and now the buttons are gone again.  I did this via software center.  Let me try via terminal following your instructions.

---

### Post by tybrownintn on 2011-02-18
maybe compiz did not install at all:

> $ sudo compiz --replace

Couldn't find a perfect decorator match; trying all decorators
Starting kde4-window-decorator
Error: "/var/tmp/kdecache-ty" is owned by uid 1000 instead of uid 0.
kde-window-decorator(4827) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
/usr/bin/kde4-window-decorator: Could not enable decorations on display ":0.0"




let me try one more time.

---

### Post by sikander3786 on 2011-02-18
Which desktop environment is there? GNOME or KDE?

---

### Post by tybrownintn on 2011-02-18
fusion-icon is installed but there is no icon.  I think something is borked with the panel to.  I had unchecked "expand" at one point and then all the icons rearranged themselves.

If anyone else has ideas let me know.  I guess I will just reinstall later.

---

### Post by tybrownintn on 2011-02-18
this is gnome.  I have never had kde on here.  no idea where that message is coming from.

---

### Post by sikander3786 on 2011-02-18
You don't need to run compiz --replace with a sudo prefix. You need to run it as a normal user.

```
compiz --replace
```

---

### Post by tybrownintn on 2011-02-18
I had tried to do it without sudo.  Thought I needed sudo due to the message I got:

> libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Starting kde4-window-decorator
kde-window-decorator(2120) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
/usr/bin/kde4-window-decorator: Could not enable decorations on display ":0.0"






this looks like the same message but this time I was not using sudo. I found the fusion-icon though.  It was under "applications>system tools  so I will play around with that.

---

### Post by tybrownintn on 2011-02-18
I see the fusion icon is right where you said it would be. sorry.  Ok so right clicking and compiz is selected as window manager.  reloading window manager does not do anything. choosing metacity and then going back to compiz does not work, though under metacity the buttons are there at least.

---

### Post by sikander3786 on 2011-02-18
It has something to do with KDE themes and KDE window decorator which I don't know how it got there on GNOME. Might be you accidentally installed it along with emerald.

You may want to try purging and re-install compiz and removing the KDE packages but I am not sure on that one. You can wait for some experienced guy on that. I never had good relations with KDE ;-)

---

### Post by tybrownintn on 2011-02-18
Well, I noticed in synaptic a LOT of kde packages installed.  No idea why.  I deleted all but the libraries and then did ```
compiz --replace
```

which led to this message:

```
/bin/sh: /usr/bin/emerald: not found


```

so somehow a configuration file exists that is telling it to use emerald even though I uninstalled it.  Now I am reinstalling emerald to see what happens.

---

### Post by tybrownintn on 2011-02-18
And that is the issue.  I reinstalled emerald and it is now with buttons though the emerald theme moves them to the right.  I don't like this theme, though.  I think the other one may have created the problems.  My question is though, how can I uninstall emerald and not screw up the buttons?

---

### Post by tybrownintn on 2011-02-18
uninstalled emerald and the buttons are still there.  Maybe it was the emerald theme manager which I had not uninstalled.  anyway, thanks for your help.,

---

