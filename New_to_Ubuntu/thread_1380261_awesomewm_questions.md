---
title: "awesomewm questions"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by UnsafeData on 2010-01-13
[http://pastebin.com/d45723b09](http://pastebin.com/d45723b09)

```
line "192" awful.spawn("slock")
```

WIN+SHIFT+Z doesn't work. Any idea why?

Also I want to map commands such as 'XF86AudioLowerVolume' to the volume wheel on my laptop. How can I do this?

***_EDIT_*****:**

***_awesome_ -k*** checks out fine.

---

### Post by DestructionsRightHand on 2010-01-13
System-Preferences-Keyboard Shortcuts

---

### Post by UnsafeData on 2010-01-13
> **DestructionsRightHand said:**
> System-Preferences-Keyboard Shortcuts

I'm using awesome not Gnome

---

### Post by UnsafeData on 2010-01-13
Bump.

---

### Post by DestructionsRightHand on 2010-01-13
Sorry mast have ran right past it.

This has always helped me,
[http://www.notesmine.com/awesome_keyboard_shortcuts](http://www.notesmine.com/awesome_keyboard_shortcuts)

---

### Post by UnsafeData on 2010-01-13
> **DestructionsRightHand said:**
> Sorry mast have ran right past it.

This has always helped me,
[http://www.notesmine.com/awesome_keyboard_shortcuts](http://www.notesmine.com/awesome_keyboard_shortcuts)

That's not what I want to do actually. I want to create a shortcut

---

### Post by UnsafeData on 2010-01-13
Bump.

---

### Post by UnsafeData on 2010-01-13
Bump.

---

### Post by lisati on 2010-01-13
I don't have an answer for you, but please try to be patient. Bumping more than once in 24 hours and starting a duplicate thread aren't needed often.....

---

### Post by falconindy on 2010-01-13
I'm don't use Awesome (DWM rather), but it looks to me like 'awful.spawn()' should be 'awful.util.spawn()' as its used on line 209.

The following post gives some insight into how you might be able to map multimedia keys to do stuff. You can find out the #nnn numbers by using xev (the number you're interested in is the keycode).

[http://ubuntuforums.org/showpost.php?p=5962447&postcount=128](http://ubuntuforums.org/showpost.php?p=5962447&postcount=128)

My only concern is the date on the post, knowing how Awesome's author practices the not-so-awesome art of making major API changes because he feels like it. Hopefully it's some help to you.

---

