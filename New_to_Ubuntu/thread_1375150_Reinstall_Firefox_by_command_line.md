---
title: "Reinstall Firefox by command line"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-01-07
I'm trying to uninstall and then reinstall firefox 3.5 on another computer. the bookmarks have all been erased and the google search bar no longer works. i can't import bookmarks from a .html so i was going to reinstall it. i tried from SPM but i'm more confident using CL for this stuff, what are the proper commands to uninstall and then reinstall firefox?

---

### Post by pastalavista on 2010-01-07
On 9.04```
sudo apt-get purge firefox-3.5 && sudo apt-get install firefox-3.5
```

On 9.10 change "firefox-3.5" to just "firefox"

---

### Post by wojox on 2010-01-07
Try this:

```
sudo apt-get update && sudo apt-get --reinstall install firefox-3.5
```

---

### Post by bodhi.zazen on 2010-01-07
> **Messyhair42 said:**
> I'm trying to uninstall and then reinstall firefox 3.5 on another computer. the bookmarks have all been erased and the google search bar no longer works. i can't import bookmarks from a .html so i was going to reinstall it. i tried from SPM but i'm more confident using CL for this stuff, what are the proper commands to uninstall and then reinstall firefox?

You probably do not need to re-install firefox, just make a new profile (or delete the old one in ~/.mozilla/firefox ).

[http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

Take care , removing firefox is not such a good idea, you can open synaptic and mark it for re-installation.

---

### Post by Messyhair42 on 2010-01-07
> **pastalavista said:**
> On 9.04```
sudo apt-get purge firefox-3.5 && sudo apt-get install firefox-3.5
```

On 9.10 change "firefox-3.5" to just "firefox"

actually it's still 8.10

---

### Post by SaintDanBert on 2010-04-11
> **bodhi.zazen said:**
> You probably do not need to re-install firefox, just make a new profile (or delete the old one in ~/.mozilla/firefox ).

[http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

Take care , removing firefox is not such a good idea, you can open synaptic and mark it for re-installation.

Firefox "quit responding".  When I restart, I get the "... embarrassing" dialog.
If I start a new session, my four home pages load, but I cannot open them.
The mouse will move over the tab, but a click on the tab -- or any other active
item within firefox does nothing.  When I click [X] to close the application, I get the
"force quit" dialog.

I've tried the mark re-install dance without success.  I've tried similar from the command line and still nothing happens. Suggestions?

~~~ 0;-Dan

---

### Post by WinterRain on 2010-04-11
Go back to synaptic and completely remove firefox. Then go to your home folder and do Ctrl-H. You will then be able to see your hidden config files. Delete the **.mozilla** folder.

Then open a terminal and do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then go back to synaptic and reinstall firefox.

---

