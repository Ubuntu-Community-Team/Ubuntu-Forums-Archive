---
title: "Go.Google.com"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Amani.S on 2011-04-29
I have a problem with firefox
facebook.com redirects to google.com
and some other website also redirects to its mobile page

after searching I found out it's a worm called "Go.Google.com"
I couldn't find how to remove it on ubuntu
any help ?

---

### Post by sandyd on 2011-04-29
> **Amani.S said:**
> I have a problem with firefox
facebook.com redirects to google.com
and some other website also redirects to its mobile page

after searching I found out it's a worm called "Go.Google.com"
I couldn't find how to remove it on ubuntu
any help ?
Its a firefox worm. You will have to generate a new firefox profile
Essentially, you will start with a blank clean new firefox.
#note, after creating a new profile, **all the data you have stored in firefox will be lost!** **This means all your extensions, bookmarks, history, firefox settings will be gone!**
 
a) backup your bookmarks and other data you want to keep.
b) open a terminal and type
```

rm -rf ~/.mozilla/firefox
rm -rf ~/.mozilla/extensions

```

---

### Post by Amani.S on 2011-04-29
I just found out that if I change my user agent to a new user agent 
using User-Agent switcher add-on for firefox 
it doesn't redirect anymore !
Interesting!

---

