---
title: "Resizing Windows and Mouse Issues"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Happyisgood on 2009-03-15
Hey guys,

I'm making my way through the amazing world that is ubuntu and I have experienced two problems recently.

First one should be a quick change.  Resizing my firefox window.  Right now it takes up my entire screen blocking my taskbar (Bottom bar... I dont know what its called on linux) and my top bar (I call it menu bar)

** SECOND PROBLEM SOLVED **
The other one is my mouse.  I copied and pasted from the macbook instructions the code for my trackpad. My problem is that if I two finger tap it gives me a third mouse button click, if I three finger tap it gives me a right click.  I want this reversed.

Right now my /etc/hal/fdi/policy/trackpad.fdi is...
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

**

---

### Post by Happyisgood on 2009-03-15
Anyone?

---

### Post by Happyisgood on 2009-03-15
Help?

---

### Post by Happyisgood on 2009-03-16
Oh, my profile's not updated, I'm back on 8.10, this is NOT a 9.04 issue!

---

### Post by Happyisgood on 2009-03-16
Ok, mouse issue solved, I actually just forgot a > in the code (which ironically I added in when I posted my code to ask you guys for help.  Now I'm only having the Firefox resize issue!

---

### Post by Dynaflow on 2009-03-16
When Firefox oversteps its bounds, press F11 twice.

Solve it permanently like this:  [http://ubuntuforums.org/showpost.php?p=6144457&postcount=21](http://ubuntuforums.org/showpost.php?p=6144457&postcount=21)

---

### Post by The Cog on 2009-03-16
I copied my firefox settings from a laptop to a netbook once, and had terrible problems with firefox dialogs and windows filling the entire screen, covering the taskbars (gnome-panels). I couldn't use F11 to get them back down to size. My solution was to delete ~/.mozilla/firefox/default.gjv/localstore.rdf which stores all the window sizes. Firefox just created another one when it started.

---

### Post by Happyisgood on 2009-03-16
Thanks so much for the help guys, my problem has been solved. I'm not quite sure what did it, a combination of pressing F11 and clicking things... but the issue is gone, every-time I open Firefox it loads properly and now my right click is working great!

---

