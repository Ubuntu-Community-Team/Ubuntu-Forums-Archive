---
title: "X11 Pointer Themes &gt; 8.04.1"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Kvothe on 2009-05-13
I've downloaded several x11 themes from gnome-look.org and can't get them to work. I tried copying the extracted .tar.gz's into /home/name/.icons with no result. Any recommendations? I tried the root directory as well. Everything I've looked up has told me this is how to install them, and it's not helping. Thanks for your time.

---

### Post by hw-tph on 2009-05-13
You also need to tell X11 to use the cursor theme you want. You can do this by editing your ~/.Xdefaults file (note capital X). Create one if you don't have it already. You set the cursor theme like this:
```
Xcursor.theme: name-of-theme
```
Log out and log in again and you should have the new cursors in all applications.

---

### Post by Kvothe on 2009-05-13
> **hw-tph said:**
> You also need to tell X11 to use the cursor theme you want. You can do this by editing your ~/.Xdefaults file (note capital X). Create one if you don't have it already. You set the cursor theme like this:
```
Xcursor.theme: name-of-theme
```Log out and log in again and you should have the new cursors in all applications.
This would be in the home directory? And what do I put in place of "Xcursor.theme: name-of-theme"? The file path or the name of the file/folder itself? Sorry, I just want to be sure before I go chasing another shadow.

---

### Post by hw-tph on 2009-05-14
> **Kvothe said:**
> This would be in the home directory? And what do I put in place of "Xcursor.theme: name-of-theme"? The file path or the name of the file/folder itself? Sorry, I just want to be sure before I go chasing another shadow.

The tilde character ("~") is shorthand for user's home directory, so yes, the .Xdefaults file lives in your home directory.

Instead of name-of-theme use the name of the theme directory. If the theme is installed as /usr/share/icons/redglass/ or ~/icons/redglass/, use "redglass" (without the quotes).

In the Gnomish way you can set the cursor theme in System / Preferences / Appearance. Select Customize and then the Pointer tab.

---

### Post by Kvothe on 2009-05-14
> **hw-tph said:**
> The tilde character ("~") is shorthand for user's home directory, so yes, the .Xdefaults file lives in your home directory.

Instead of name-of-theme use the name of the theme directory. If the theme is installed as /usr/share/icons/redglass/ or ~/icons/redglass/, use "redglass" (without the quotes).

In the Gnomish way you can set the cursor theme in System / Preferences / Appearance. Select Customize and then the Pointer tab.
I did this, and it seemed to work. I saw the cursor I wanted right after login, and then gnome loaded and it went back to normal. I don't see the theme as an option in the pointer tab. ?

EDIT: It appears that this theme in particular is the problem. Thank you for your help.

---

