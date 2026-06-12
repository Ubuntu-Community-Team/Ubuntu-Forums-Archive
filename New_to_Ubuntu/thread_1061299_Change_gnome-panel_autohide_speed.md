---
title: "Change gnome-panel autohide speed"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by SentientFluid on 2009-02-05
I have one of my gnome-panels set to autohide but I would like to adjust the speed at which it hides and un-hides. Is there a way I can do this?

---

### Post by drs305 on 2009-02-05
Open up gconf-editor and then go to /apps/panel/toplevels/
Find the panel you want to change and alter the "hide_delay" value.

You can open gconf-editor and just do a Edit > Find search for "hide_delay" to get to the settings. (Tick 'also search in key names').

To open gconf-editor:
```

gconf-editor

```

---

### Post by SentientFluid on 2009-02-05
Thanks drs305! That's exactly what I was looking for, I should have thought of looking in there!

---

### Post by karatedog on 2010-02-13
> **SentientFluid said:**
> Thanks drs305! That's exactly what I was looking for, I should have thought of looking in there!

This solution doesn't work for me (Ubuntu 10.04). 
First the path is /apps/panel/default_setup/toplevels/bottom_panel and .../top_panel.
No matter what value I set into "hide_delay" fields, nothing changes. 

Strange, but if I set the panel's height to 23 by right-clicking the panel and setting it in the panel properties, I couldn't find this value in gconf-editor...

---

### Post by chewearn on 2010-02-13
> **karatedog said:**
> This solution doesn't work for me (Ubuntu 10.04). 
First the path is /apps/panel/default_setup/toplevels/bottom_panel and .../top_panel.
No matter what value I set into "hide_delay" fields, nothing changes. 

Strange, but if I set the panel's height to 23 by right-clicking the panel and setting it in the panel properties, I couldn't find this value in gconf-editor...

Since it's 10.04 / alpha development version, I suggest file a bug in launchpad.

---

### Post by drs305 on 2010-02-13
> **karatedog said:**
> This solution doesn't work for me (Ubuntu 10.04). 
First the path is /apps/panel/default_setup/toplevels/bottom_panel and .../top_panel.
No matter what value I set into "hide_delay" fields, nothing changes. 

I believe the path is correct. There *is* a /apps/panel/default_setup but there is also an /apps/panel/toplevels. Go to the top_panel_screen0  or change the value in the command below. I believe if you make the delay change in that section it will work if autohide is enabled.

```
gconftool-2 --type integer --set /apps/panel/toplevels/top_panel_screen0/hide_delay 2000
```

---

