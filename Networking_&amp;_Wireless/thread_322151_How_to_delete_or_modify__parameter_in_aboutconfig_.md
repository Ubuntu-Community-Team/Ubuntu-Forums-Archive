---
title: "How to delete or modify  parameter in about:config  of  firefox"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Stupid kid on 2006-12-20
to make the ed2k extend between firefox and amule ,

i enter[COLOR="Red"]about:config[/COLOR] in firefox
and then 

```
New->boolean->network.protocol-handler.external.ed2k ->true
New->boolean->network.protocol-handler.app.ed2k    #this is just the mistake i made,

```

i want to modify the second boolean to string but i don't know how i can do with it!

if some one can help me ?

---

### Post by yabbadabbadont on 2006-12-20
Look in your firefox profile directory tree for a file called prefs.js.  Make sure that you don't have firefox running, then edit that file with the text editor of your choice.  Search for the messed up entry you created.  When you find it, delete the line.  (or if you feel adventurous, just change it to the correct type there).  Save the file and exit your editor.  Start firefox and create the entry properly in about:config again.  (unless you just changed it in the prefs.js file, in which case verify that it is correct)

---

### Post by Stupid kid on 2006-12-20
thank you very much and i have corrected it!

---

