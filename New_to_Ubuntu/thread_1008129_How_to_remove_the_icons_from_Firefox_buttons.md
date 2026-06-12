---
title: "How to remove the icons from Firefox buttons?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by jay li on 2008-12-11
Hello!

There is another post talking about ["[COLOR="Blue"]**_How can I remove all button icons_**[/COLOR]?"]("http://ubuntuforums.org/showthread.php?t=405453") and I would like to do it with Firefox buttons too? 
I don't want to use another theme to get this result, I like the original one. 
So it is impossible doing it?

Thank you guys.

---

### Post by Michael.Godawski on 2008-12-11
Don't really know... but perhaps there is some hidden option to disable them. Type
```
about:config
```
into the url field, and check the entries provided there. But be careful, aks before changing something. :p

---

### Post by jay li on 2008-12-11
Thanks Michael.Godawski I'm going to check your tip.

---

### Post by frank002 on 2008-12-11
Right click on the taskbar  and click Customize. On the bottom left you will see where it gives you the options of icons and text, icons only or text only.

---

### Post by jay li on 2008-12-11
Hi frank002,

Well I kind meant to the "Close" "Help" etc. Buttons like in this image:

---

### Post by Pappy1911 on 2008-12-11
> **frank002 said:**
> Right click on the taskbar  and click Customize. On the bottom left you will see where it gives you the options of icons and text, icons only or text only.

Just as Frank said.....works for me..

---

### Post by frank002 on 2008-12-11
I don't believe you can remove those. However, if someone knows of a way, I am sure he or she will post it. Good Luck.

---

### Post by jay li on 2008-12-12
I am sure there must be a way.
If I could do that with Ubuntu GUI, Firefox must have this feature too. 
The problem is I don't know how to do it.

---

### Post by jay li on 2009-06-12
> **jay li said:**
> I am sure there must be a way.
If I could do that with Ubuntu GUI, Firefox must have this feature too. 
The problem is I don't know how to do it.

To do it, open your hidden "userChrome.css" file in the path /home/USER_NAME/.mozilla/PROFILE_FOLDER/chrome/userChrome.css (if not exist, create one), and add the following rule: ```
/* Remove icons from buttons. */
button:not(#navigator-throbber) > .button-box > .button-icon {
  display: none !important;
}
```

---

