---
title: "Middle Click Suddenly Not Working In Firefox Only?"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by Davinss on 2011-09-07
Hey I have been using Ubuntu for a few months now and I am having a pretty annoying issue. Middle clicking to open a link in firefox suddenly doesn't work correctly. I can not use the middle click to open a link in a new window. However using the middle click on the tab bar to close tabs works fine...

I am using Ubuntu 11.04 and Firefox 6.0.2.

browser.tabs.opentabfor.middleclick is set to TRUE

Xinput test shows the mouse is working fine. Here is my xinput list:
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Reclusa Keyboard                      id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Razer Reclusa Keyboard                      id=8    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=10    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=12    [slave  keyboard (3)]

```

---

### Post by Ms_Angel_D on 2011-09-07
I had this issue, turns out it was something to do with the tab mix plus extension. I uninstalled it and then re-installed it and now the middle click is working like it's supposed to again.

---

### Post by JigmeDatse on 2011-09-08
I'm not sure if this is your issue or not, but there is a conflict with the approved versions of Tab Mix Plus and Greasemonkey that broke the middle click feature on at least Windows 7 and OS X.6, this seems to be a cross OS issue.  If you go to [https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) you can install version 0.9.11 of Greasemonkey that seems to have fixed it (that's the version I installed from the Greasemonkey site, as automatic updating didn't install it, but it might not have been pushed out when I last started Firefox).  Hope this helps.

It seems someone else has responded with similar information.  I hope you find a solution soon.  I'm sorry, I'm not on my Mint Linux box to be able to tell you that this or any solution will work.

---

### Post by Davinss on 2011-09-08
Awesome! Big thanks! All it took was restarting firefox with addons disabled and then reenabling them manually.

---

### Post by fuzzyangel on 2011-09-08
Disabling GreaseMonkey also worked for me, thanks!!!

---

### Post by me13221 on 2012-02-07
> **fuzzyangel said:**
> Disabling GreaseMonkey also worked for me, thanks!!!

Um, how do you disable greasemonkey?  thanks.

---

