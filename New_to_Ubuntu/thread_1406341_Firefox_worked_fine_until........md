---
title: "Firefox worked fine until......."
date: 2010-02-13
forum: New to Ubuntu
---

### Post by SocoJoe87 on 2010-02-13
It updated recently and now it wants me to use Namoroka (firefox beta) as the browser for Firefox now. Which would be all fine and dandy if it actually opened, but when I click on it, it just says "starting Namoroka" then after a few seconds disappears and it never opens. I have done everything on this page:

[http://ubuntuforums.org/showthread.php?t=1347288](http://ubuntuforums.org/showthread.php?t=1347288)


And it worked the first time but whenever I closed Firefox (Namoroka) it would do the same thing as I previously mentioned. I have un-installed then re-installed Firefox and it still is doing the same thing. Can anyone tell me why it is doing this and how to fix it? I have downloaded the Epiphany web browser to post this but I REALLY don't like the simplicity of this browser, I need my Firefox back. So any one that can help I will appreciate it!

---

### Post by luckydeveloper on 2010-02-13
First remove any other firefox variant (we can install them later after our firefox works properly) use synaptic to install the default firefox with the default version number that comes with ubuntu.

---

### Post by SocoJoe87 on 2010-02-13
> **luckydeveloper said:**
> First remove any other firefox variant (we can install them later after our firefox works properly) use synaptic to install the default firefox with the default version number that comes with ubuntu.

sudo apt-get remove firefox && sudo apt-get autoremove

I used that to remove any firefox variant correct?

Once I did that I went into synaptic and installed firefox 3.6.2 and then tryed to open Namoroka and it still does the same thing.

What's next?

---

### Post by lovinglinux on 2010-02-13
> **SocoJoe87 said:**
> sudo apt-get remove firefox && sudo apt-get autoremove

I used that to remove any firefox variant correct?

Once I did that I went into synaptic and installed firefox 3.6.2 and then tryed to open Namoroka and it still does the same thing.

What's next?

No. First you need to disable the ubuntu-mozilla-daily ppa from the Software Sources >> Other Software. Then you go to Synpatic Package Manager, select firefox and firefox-3.5 and mark them for re-installation, then click apply. This should restore the default Firefox.

If you want to install Firefox 3.6 with proper branding see the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Either, if you still can't load Firefox after restoring the default or installing FF 3.6 with one of the methods from my tutorial, then you might have a profile issue.

So, make sure firefox and firfefox-bin are not running using the System Monitor or running these commands:

```
killall firefox
killall firefox-bin
```

Then start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it. If it works, then you probably have a corrupt file on your profile, sub-optimal settings or an extension preventing FF form starting.

To find if it's an add-on, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem.

---

### Post by SocoJoe87 on 2010-02-14
> **lovinglinux said:**
> No. First you need to disable the ubuntu-mozilla-daily ppa from the Software Sources >> Other Software. Then you go to Synpatic Package Manager, select firefox and firefox-3.5 and mark them for re-installation, then click apply. This should restore the default Firefox.

If you want to install Firefox 3.6 with proper branding see the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Either, if you still can't load Firefox after restoring the default or installing FF 3.6 with one of the methods from my tutorial, then you might have a profile issue.

So, make sure firefox and firfefox-bin are not running using the System Monitor or running these commands:

```
killall firefox
killall firefox-bin
```

Then start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it. If it works, then you probably have a corrupt file on your profile, sub-optimal settings or an extension preventing FF form starting.

To find if it's an add-on, close Firefox and start your default profile with this command:

```
firefox -safe-mode
```

If that works, then you need to find which add-on is causing the problem.

Thank you the first part seemed to work and actually installed firefox 3.5, which I don't mind. It seems once it tryed to update the latest of firefox, which made me use Namoroka, is when the problems started. Now it's the actual firefox icon under apps->internet


Thank you for the help!

---

### Post by lovinglinux on 2010-02-14
> **SocoJoe87 said:**
> Thank you the first part seemed to work and actually installed firefox 3.5, which I don't mind. It seems once it tryed to update the latest of firefox, which made me use Namoroka, is when the problems started. Now it's the actual firefox icon under apps->internet


Thank you for the help!

If you still want the 3.6 version and are using 32bit Ubuntu, see [this](http://lovinglinux.megabyet.net/?page_id=220##2---Automatic-installation-of-fresh-final-releases-from-Ubuntuzilla-3). If you are using 64bit, then see [this](http://lovinglinux.megabyet.net/?page_id=220##3---Installation-from-PPA-repositories-3).

To fix the icon issue, try to reboot. If it doesn't work, then go to "System >> Preferences >> Main Menu" and edit it there.

---

