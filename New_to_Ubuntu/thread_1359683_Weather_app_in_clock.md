---
title: "Weather app in clock"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Riaku on 2009-12-20
For the past few days I have been trying to get the weather app the usually shows up with the clock to work. When I click it go to locations and click edit then add my location and click close I see the clock expand slightly. One fix was to expand locations and click set, which I did and it still won't work. All my settings are right I believe.

---

### Post by Riaku on 2009-12-20
For the past few days I have been trying to get the weather app the usually shows up with the clock to work. When I click it go to locations and click edit then add my location and click close I see the clock expand slightly. One fix was to expand locations and click set, which I did and it still won't work. All my settings are right I believe.

---

### Post by TransitMan on 2009-12-20
On the general tab, did you tick "show weather" and "show temperature"? 
If not, this is why it is not showing.

---

### Post by Riaku on 2009-12-20
yes, it still doesn't show up

---

### Post by cariboo on 2009-12-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Riaku on 2009-12-20
bump

---

### Post by TransitMan on 2009-12-20
Based on your attched pics, I went and put Columbia into my calender/clock and it came up showing the current temp of 52 and cloudy skies.
Not sure why it won't show for you.
Have you tried another nearby town/city to see if they show up?

---

### Post by freesitebuilder on 2009-12-20
Mine doesn't show weather either, only time. I'm in the UK, so I assume it may not be able to access weather info for UK.

Edit: yes it does, it's suddenly appeared after a few minutes!

---

### Post by rCXer on 2009-12-20
This is probably related to [this bug](https://bugs.launchpad.net/ubuntu/+source/libsoup2.4/+bug/372647).  A workaround, as suggested in comment #20 of the bug report, is to rename "~/.gconf/system/" to "~/.gconf/system.bak/" and then restart Ubuntu.  This will allowing the system to make a new "~/.gconf/system/" directory.  The only snag with this method is that you will have to reenter your wireless keys again.

---

### Post by fatcrab on 2009-12-20
I used add to panel.
Sorry,did not see "in the clock"

---

