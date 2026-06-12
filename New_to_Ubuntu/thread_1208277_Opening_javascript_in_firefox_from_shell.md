---
title: "Opening javascript in firefox from shell"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by nealh149 on 2009-07-09
If you run

firefox google.com

in the shell, firefox opens google.  I'd like to do something similar to

firefox javascript:void(open('http://mail.google.com/mail/#compose','gmail',     'toolbar=no,width=700,height=700'))

Is this possible?

---

### Post by Temposs on 2009-07-09
I don't believe you can do inline javascript like that. If you want to load javascript code, you need to make your own webpage and open that with firefox as it opens, like as your homepage. You could probably hack something like you want to do, then.

The other way to manipulate firefox programmatically is creating an add-on. That's not done with javascript, though.

---

### Post by lovinglinux on 2009-07-09
Why don't you use Prism and launch it using a command?

When you create a prism application you can choose to save a desktop shortcut. Just copy the command from the shortcut. It looks like this:

```

"prism" -override "/home/yourself/.webapps/gmail@prism.app/override.ini" -webapp gmail@prism.app
```

---

