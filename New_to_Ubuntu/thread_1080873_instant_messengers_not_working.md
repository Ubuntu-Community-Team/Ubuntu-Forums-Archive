---
title: "instant messengers not working"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by nynoah on 2009-02-25
Ok this is strange.  I have problems with both Kopete and Pidgin.  I can not get either one to sign onto the net.  Any reason anyone can think why this is happening?

---

### Post by llamabr on 2009-02-25
is it possibly still running in the background?  Run ps aux or top and have a look.

If not, be more explicit -- what is it doing, and not doing, besides not working.

---

### Post by Temposs on 2009-02-25
better yet, open a terminal through Applications->Accessories->Terminal, and then type:

```
pidgin
```

And then just copy and paste here what appears when you press Enter.

---

### Post by nynoah on 2009-02-25
Ok tried typing pidgin...... what happens is pidgin will open.  But NONE of my IM clients will connect.  The strange part is Kopete does the same.

> noah@noah-laptop:~$ pidgin
/usr/share/themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:60: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:61: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:62: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/T-ish-Brushed-bright-Aquastyle/gtk-2.0/gtkrc:63: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.



---

### Post by nynoah on 2009-02-25
Ok changed my theme to another one and I get no errors.  But I still have the same problem.

---

### Post by nynoah on 2009-02-25
Is it possible that I am having some kind of a conflict with ports?

---

### Post by nynoah on 2009-02-25
also I tried rebooting and that did not work.  I tried different kernal and that did not work.  Neither did it not work when I booted into KDE 4.1.  I if td have KDE nightly Neon 4.2 installed but that was removed earlier in the day.  I am not sure that makes a difference.  But I am redoing everything with a fresh install.  Lost a hard drive.

---

### Post by nynoah on 2009-02-25
> [QUOTE]noah@noah-laptop:~$ pidgin

** (gnome-default-applications-properties:20429): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/OSX-theme/gtk-2.0/Tabs/notebook_top_flat.png,
borders don't fit within the image

** (gnome-default-applications-properties:20429): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/OSX-theme/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
noah@noah-laptop:~$ 


[/QUOTE]

any ideas what is going on?

---

### Post by llamabr on 2009-02-25
You messed up some themes.

Look in your ~/.purple, where you'll find prefs.xml, which I think is a file you want to rm.  

I'd tell you to rm your whole .purple, but you'll want to save any contacts first.

Instead, try renaming your ~/.purple then log out, then log in, and see if it starts correctly after that.

---

### Post by nynoah on 2009-02-25
well my contacts are not saved locally.  I can just reput back in the signons from scratch.

---

### Post by llamabr on 2009-02-25
were it me, I'd just nuke my .purple 

But that's not something I'd necessarily advise.

But when you do it, let us know what happens.

---

### Post by nynoah on 2009-02-25
meh......... I will try that I can always reload.  LOL

---

### Post by nynoah on 2009-02-25
Nope that did not work.

---

### Post by llamabr on 2009-02-25
You may have to log in and log out.

And if you run pidgen again, what errors are you getting?

If it's not working with the other program, it could be a problem with your themes, not just the app.

---

### Post by nynoah on 2009-02-25
Ok......... I got it working.  I uninstalled Mobloquer suites and it worked again.  I wonder why that would start giving it a problem now?  huh

---

