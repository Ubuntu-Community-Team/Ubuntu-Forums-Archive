---
title: "replace pcmanfm with thunar lxde"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by dzon65 on 2010-03-10
What am I doing wrong here?Trying to replace pcmanfm with thunar in lxde,using this command:killall pcmanfm -d && thunar &   but nothing happens.Probably the wrong command I guess?

---

### Post by arochester on 2010-03-10
Permanently?

Why not?
sudo apt-get remove pcmanfm
sudo apt-get install thunar

---

### Post by dzon65 on 2010-03-10
If you do it like that,lxde core will be removed as well.Thunar's already installed.

---

### Post by kerry_s on 2010-03-10
> **dzon65 said:**
> What am I doing wrong here?Trying to replace pcmanfm with thunar in lxde,using this command:killall pcmanfm -d && thunar &   but nothing happens.Probably the wrong command I guess?

just "killall pcmanfm" thunar does not need to be started cause it does not manage the desktop. you can however still run "thunar --daemon &" in your startup, to keep it in the background for speed, like preloading it.

---

### Post by dzon65 on 2010-03-10
Hi there Kerry.It is set in startup,but I really need thunar to take care of all files.Desktop stuff I can do wih idesk or something similar.The main problem with pcmanfm in the "latest" lxde releases is that it's impossible to set defaults.I've googled my a.. off to finally discover it's a bug.Many people who tried lxde reported this,and finally aborted lx.Not only in lxde but in lubuntu as well.I know you have that tab to set whatever prog to be the default one.Not so in the latest.Tried debian lenny+lxde>same thing.Which makes lxde practically unusable.You can imagine opening each file being asked to open with what makes one nuts.If all pcmanfm does with the desktop is to enable downloads to be downloaded to the desktop I can pretty much do without it.unless there's something more it does,which brings me back to say that lxde is unusable.
Edit:Strange thing is,I've downloaded the live cd and everything works fine but it's uninstallable.That is,there's an icon on the desktop to install,but doesn't work.

---

### Post by undecim on 2010-03-10
You could always try this:
```
sudo mv /usr/bin/pcmanfm /usr/bin/pcmanfm.bak
sudo ln -s /usr/bin/thunar /usr/bin/pcmanfm
```

That will make pcmanfm a link to thunar. Only problem is you will have to repeat this each time you upgrade pcmanfm.

---

### Post by dzon65 on 2010-03-11
Yes.For now in order to avoid pcmanfm's "weirdness" I start everything with thunar file manager.It takes one extra click but avoids the above mentioned probs.Like Kerry said,keep it "sleeping".It's not ideal but what can you do.Hopefully the developers of lxde will have this fixed soon.Thanks for all the replies.
Kind regards,J.

---

### Post by PCMan on 2010-03-15
1. This is NOT the bug of pcmanfm. People at freedesktop.org changed some specs and file formats, and hence break backward compatibility, so pcmanfm stop working due to their changes.
2. This issue was already fixed long time ago. Maybe the fix is not available in ubuntu yet.
3. The latest Lubuntu doesn't have this issue.

---

