---
title: "Firefox middle-click behaves inconsistently"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by benhamill on 2009-01-28
I've got Hardy Heron running on a custom-built desktop machine. I'm not really sure what hardware information might be pertinent, so if someone outlines stuff, I'll be happy to come back and fill that missing information in.

I've got Firefox 3.0.5 installed and the settings such that a middle-click on a link will open a new tab. On my work machine (Windows XP) and my laptop (Vista) this setting also means that middle-clicking on a bookmark opens it in a new tab. However, in Ubuntu, it seems to open it in a new window. Fail.

Anyone else experience this? Any ideas of what I can check or change to fix it? Thanks much in advance, all.


Ben

---

### Post by Zylar on 2009-01-28
Type about:config in the address bar of FF and hit Enter.  Filter for the word 'middle' and see if browser.tabs.opentabfor.middleclick is set to true like mine.  Maybe play with some other settings in there too.

gl,

---

