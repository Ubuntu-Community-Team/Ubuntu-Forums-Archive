---
title: "Firefox totally messed up - please help"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by abutel on 2009-06-01
Hi,

I'm a newbie to Linux and Ubuntu.  I just setup my laptop to dual boot Ubuntu 9.04 and Vista and that seems to have gone fine.  I logged in to Ubuntu, started up Firefox and downloaded 2 add-ons (gmail manager & hebrew calendar).  Got prompted to restart the browser, i did and everything seemed to be going ok.
Then something popped up saying i need to download a bunch of updates...I said ok and when it was done it said everything installed ok and firefox needed to be restarted since it was updated.  I restarted firefox and now I can't use it - all i see is the top bar (brown color) that says Mozilla Firefox and nothing else - no menu, no address bar, no status bar NOTHING.
In windows I would try to open it in Safe Mode and if that didn't work would uninstall/reinstall.  But I can't seem to figure out how to do either here.

Any help would be greatly appreciated.

TIA

---

### Post by Volt9000 on 2009-06-01
Hello, and welcome to the forums!

You can run Firefox in safe mode in Linux, too. In a terminal window type

```

firefox -safe-mode

```

That will start up Firefox without any of your extensions. If Firefox starts up ok in safe mode then it's a good bet one of your plugins are messing it up.

Would you be able to post a screenshot of what you're seeing?

---

### Post by LewRockwell on 2009-06-01
reboot?

---

### Post by Steelmourne on 2009-06-01
Whenever you update, its probably best if firefox is shut down if a new version is being automatically installed. Go to Synaptic Package Manager in system, administration, then start synaptic and search for firefox. Right click firefox (it will have a shaded green box) and click mark for removal. Once its uninstalled, reboot just in case, and go back to synaptic and re-install it again.

---

### Post by abutel on 2009-06-01
MY SINCERE APOLOGIES....i feel like an idiot....rebooting worked.

thanks for the super fast replies.

The machine i'm using is a laptop with a builtin webcam.  Doing some research online, I came across this:

"Open a terminal window (Applications, Accessories, Terminal) and type:
gstreamer-properties
press Enter. On the resulting screen open the "Video" tab and click the "Test" button. "

When I tried that I couldn't see anything.  Should I start a new thread for that?

Thanks again everyone

---

### Post by Volt9000 on 2009-06-01
Always best to start a new thread for unrelated issues.

---

