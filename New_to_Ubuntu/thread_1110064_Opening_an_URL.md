---
title: "Opening an URL"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Ugluk on 2009-03-29
How can I open some URL in default browser (if such concept exists in Ubuntu)? If there's no default one, what is the best way to find out the installed browser?

---

### Post by Lisa Y on 2009-03-29
Now sure what exactly you mean....

but are you talking about a ...default homepage? 

And as for browsers installed Application> Internet (shows your browsers)

---

### Post by Sarai the Geek on 2009-03-29
Ubuntu ships with firefox as the default browser. You can change that or reset it by going to System>Preferences>Preferred Applications.

---

### Post by Ugluk on 2009-03-29
Basically, if you type 'http://something' some (default) browser will open with given URL. I would like to know how to know the name of default browser present in the system, being it Firefox, Epiphany, Konqueror, Lynx, whatever the user had somehow select.

---

### Post by Sarai the Geek on 2009-03-29
> **Ugluk said:**
> Basically, if you type 'http://something' some (default) browser will open with given URL. I would like to know how to know the name of default browser present in the system, being it Firefox, Epiphany, Konqueror, Lynx, whatever the user had somehow select.

For Ubuntu, the default browser is Firefox. Kubuntu comes with Konqueror.

---

### Post by Ugluk on 2009-03-29
No, that won't do. User may uninstall Firefox and use the other browser. Is there the concept of 'default browser' or 'http protocol handler' at all in Ubuntu?

---

### Post by Sarai the Geek on 2009-03-29
> **Ugluk said:**
> No, that won't do. User may uninstall Firefox and use the other browser. Is there the concept of 'default browser' or 'http protocol handler' at all in Ubuntu?

To check the current default browser, whatever it may be, go to System>Preferences>Preferred Applications. In the dialogue box that pops up, web browser is the first option.

Are you looking for a CLI command to do this?

---

### Post by Ugluk on 2009-03-29
Yes, of course. The name and parameters of browser executable which system use to open URLs.

---

### Post by _Purple_ on 2009-03-29
In the terminal, type:

```
sudo update-alternatives --config x-www-browser
```

This will show the list of available browsers as well as the current default browser. You can keep the previous one or choose a new default browser from the list.

---

