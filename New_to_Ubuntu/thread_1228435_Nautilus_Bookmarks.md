---
title: "Nautilus Bookmarks"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by hayden92 on 2009-07-31
Hello all,

I am having some trouble with the default nautilus bookmarks (not the ones that I can edit under the nautilus bookmarks preferences).

After I trying out "pcmanfm", a lightweight file manager, I decided that I didn't like it so I uninstalled it. Now all my default bookmarks (such as "home", "desktop" and "network") don't work because they are trying to open with pcmanfm.

I have two questions:
   1) Is there a way to edit **all** of Nautilus's bookmarks? I read on a forum that you can set user mode to advanced under Preferences->File Management->Navigation or something like that, but the "Navigation" tab does not seem to exist. The only bookmarks that I have been able to edit are "Documents", "Pictures", et cetera.
 
   2) Is there a way to tell the computer to open all the bookmarks with Nautilus? I'm thinking that there might be an option in gconf-editor, but I haven't had any luck finding it.

Thank you in advance,
Hayden

---

### Post by swoll1980 on 2009-07-31
maybe try purging them both then reinstall nautilus. 

```
sudo dpkg -P nautilus
```

```
sudo dpkg -P pcman
```

```
sudo apt-get install nautilus 
```

worth a try I guess.

---

### Post by 73ckn797 on 2009-07-31
The recommendations of swolla980 are probably the best. When you uninstalled pcmanfm did you designate complete removal?

---

### Post by hayden92 on 2009-08-03
I did try those suggestions, but I got a message something like: "netbook-remix requires this package"

And yes, I did completely remove pcmanfm

---

