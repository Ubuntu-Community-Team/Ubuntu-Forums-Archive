---
title: "I have NO minimize,close and enlarge buttons on Firefox"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-05-29
Since upgrading to Ubuntu 10.04,Firefox now has no controls in the upper right!And also,I cant do anything on the desktop,except change the background.Right clicking on it does nothing,and I can't put any icons or anything on the desktop.Any ideas?

---

### Post by Andrew_Grant on 2010-05-29
Try this thread [http://ubuntuforums.org/showthread.php?t=1469937](http://ubuntuforums.org/showthread.php?t=1469937)

---

### Post by Ben_222 on 2010-05-29
I did the metacity replace command,but nothing happened.......

---

### Post by lidex on 2010-05-29
Using a Terminal="Applications->Accessories->Terminal"
enter ```
nautilus
``` and press enter. Post the terminal output here.

---

### Post by Ben_222 on 2010-05-29
Ok, I entered nautilus in the terminal,hit enter,and the file browser came with the home folder contents

---

### Post by HermanAB on 2010-05-30
It sounds like your Window Manager failed to run.

---

### Post by lidex on 2010-05-30
> **Ben_222 said:**
> Ok, I entered nautilus in the terminal,hit enter,and the file browser came with the home folder contents

Did your icons appear?

---

### Post by Andrew_Grant on 2010-05-30
Just a thought, so cannot guarantee anything, but it could be worth having a peer at ./.gconf/apps/metacity/general/%gconf.xml

It should read something like this:

<?xml version="1.0"?>
<gconf>
        <entry name="theme" mtime="1275064121" type="string">
                <stringvalue>Ambiance</stringvalue>
        </entry>
        <entry name="button_layout" mtime="1275063309" type="string">
                <stringvalue>menu:minimize,maximize,close</stringvalue>
        </entry>
</gconf>

If any of these values are missing the menu buttons disappear.  Just tried it.
Other than this I can only assume that the gdm has been affected by Compiz.  
Andrew

---

