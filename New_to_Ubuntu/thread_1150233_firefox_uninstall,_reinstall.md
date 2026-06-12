---
title: "firefox uninstall, reinstall"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-05-05
I don't know what I did, but I screwed up firefox. My problem would be solved by a simple uninstall then reinstall. My problem is that I uninstalled it with the add/remove tool, then reinstalled it, and it was basically restored to the previous state. I want to remove it and all of it's plug-ins...

Any ideas?

---

### Post by Jive Turkey on 2009-05-05
The settings for firefox are inthe ~/.mozilla directory along with your plugins, themes and bookmarks.

You can trythis in a terminal:
```
$ cp ~/.mozilla ~/.old-mozilla && rm -r ~/.mozilla
```
This should backup your original settings folder and remove it.  Then start firefox.  If you have even more problems after this you can undo it by running:
```
$ cp ~/.old-mozilla ~/.mozilla
```

---

### Post by Didius Falco on 2009-05-05
> **chilimac02 said:**
> I don't know what I did, but I screwed up firefox. My problem would be solved by a simple uninstall then reinstall. My problem is that I uninstalled it with the add/remove tool, then reinstalled it, and it was basically restored to the previous state. I want to remove it and all of it's plug-ins...

Any ideas?

If it's just the extensions and plug-ins giving you problems, you can go to the **Tools/Addons** menu in Firefox. From there you can disable all your plug-ins and then re -enable them one at a time to see which one is causing problems. Then you can uninstall that one. You can also remove Themes, and disable/remove plug-ins.

That's one option - if you really want to blow it out of the water:  

Remove it using the Synaptic Package Manager in **System/Administration/Synaptic**. Choose the **Mark for Complete Removal** option and it will delete everything. 

Be warned, though, you'll lose your bookmarks as well.

Use these instructions if you want to back up your bookmarks first, so you can import them back in after you've removed and restored Firefox.

[http://support.mozilla.com/en-US/kb/Exporting+bookmarks+to+an+HTML+file](http://support.mozilla.com/en-US/kb/Exporting+bookmarks+to+an+HTML+file)

---

### Post by chilimac02 on 2009-05-06
tried the above ^ and it left firefox on my Applications->Internet menu, and still ran...

---

### Post by llamabr on 2009-05-06
> **chilimac02 said:**
> tried the above ^ and it left firefox on my Applications->Internet menu, and still ran...

did you try 

```
rm -rf .mozilla
```

?

---

### Post by chilimac02 on 2009-05-06
Ironically when I executed the above command ^ things worked. Firefox was NOT un-installed, but when I opened it everything was back to default. while the goal was not actually reached, i would consider this solved.

---

