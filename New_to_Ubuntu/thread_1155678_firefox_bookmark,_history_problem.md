---
title: "firefox bookmark, history problem"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by Hutom on 2009-05-11
Dear friends, I am having the following problems -

1) My firefox browser does not allow me to bookmark any page.

2) If I click the show all history it opens a blank window, with no history at all.

3) In the address bar there is no drop down menu. It does not suggest any previously visited link. 

I am using Ubuntu Hardy. I have uninstalled and reinstalled firefox twice using Synaptic package manager. It did not fix the problem. Can anybody suggest a way out?

---

### Post by Dill on 2009-05-11
What happens when you start in Safe Mode? Try opening a Terminal and enter

```
firefox -safe-mode
```

You can also try creating a new Profile by launching the Profile Manager:

```
firefox -profilemanager
```

Cheers,
Dylan

---

### Post by Hutom on 2009-05-11
It's all the same with safe mode. Problems prevail. However, when I closed firefox the following words appeared in the terminal; I am posting it, if that helps.

```
(firefox:6669): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6669): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6669): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:6669): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

```

---

### Post by Dill on 2009-05-11
I believe those messages relate to Flash, and probably aren't the root of the problem. Did you try creating a new Profile to see if that worked? Also, did you make any changes to FF before this started happening?

---

### Post by Hutom on 2009-05-12
Many thanks Dill. Creating a new profile fixed the problem.

---

