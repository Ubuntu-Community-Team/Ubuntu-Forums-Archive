---
title: "How do you clear recently used documents in OOo3 ?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by crjackson on 2009-01-14
The title says it all.  I already know how to remove the context from the menu, but I would like to know how to reset the data in the recently used documents of Open Office 3.

TIA

---

### Post by Terl on 2009-01-14
This [thread in the OO forums]("http://www.oooforum.org/forum/viewtopic.phtml?t=65992") may have the solution.   :D

---

### Post by crjackson on 2009-01-14
> **Terl said:**
> This [thread in the OO forums]("http://www.oooforum.org/forum/viewtopic.phtml?t=65992") may have the solution.   :D

Thanks Terl, nothing there worked so far...

---

### Post by Terl on 2009-01-14
I found this posting in another thread over there:

```
I figured it had to be easier, so after a little while of playing around, I found that all I had to do was to go into Tools Menu:Customize, remove the Recent Documents item, then re-add a new one.

I'm not good with programming in OpenOffice, so I'll have to just do it manually when I need to. 
```

I am on a windows machine without OO right now so I can't check it...

EDIT:  Just found [This link, this may help better]("http://www.oooninja.com/2009/01/recent-documents-clean-erase-delete.html")

And a manual way from that site:

```
Manual

To manually remove the recent documents history, first close OpenOffice.org. Then edit the Common.xcu file in your OpenOffice.org user profile directory. The OpenOffice.org user profile path differs, but for OpenOffice.org 3, it's most commonly either:

    * Linux: ~/.openoffice.org/3/user/registry/data/org/openoffice/Office/Common.xcu
    * Windows XP: C:\Documents and Settings\{username}\Application Data\OpenOffice.org\user\registry\data\org\openoffice\Office\Common.xcu
    * Windows Vista: C:\Users\{username}\AppData\Roaming\OpenOffice.org\user\registry\data\org\openoffice\Office\Common.xcu

Edit Common.xcu and remove the XML node History. Alternatively, you can delete the whole file, but you will lose a bit of information such as whether you registered OpenOffice.org.

Finally, delete the corresponding cache file org.openoffice.Office.Common.dat in the /user/registry/cache/ directory, or you can re-run OpenOffice.org to regenerate the cache.
```

---

### Post by crjackson on 2009-01-14
I'll give it a try in a day or two. I alread have BleachBit installed and it doesn't do the job. I'll try the entension and if that doesn't work I'll try editing the mentioned files.

It's not a great big deal, but it does annoy me.

---

### Post by crjackson on 2009-01-15
History Manager did the trick. You have to exit everything including quickstarter applet and then when you restard OOo, the history is gone.

---

### Post by crjackson on 2009-01-15
Seems I spoke too soon. It worked ONCE only. I guess I'll just forget about it.

---

