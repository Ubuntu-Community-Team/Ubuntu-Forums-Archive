---
title: "[SOLVED] Switching keyboard layout in xubuntu"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by putanitsa on 2008-12-10
I just installed xubuntu, and I would like to be able to swtich between us, canadian multilingual, russian and persian keyboards. How do I do that?

I have been to settings->keyboard preferences->layout . There, I can uncheck "Use X Configuration" and add the layouts I want. But then I don't know how to switch between them.

I have found other threads that touch upon this topic, but I don't understand them:
[http://ubuntuforums.org/showthread.php?t=66115&highlight=xubuntu+keyboard](http://ubuntuforums.org/showthread.php?t=66115&highlight=xubuntu+keyboard)
[http://ubuntuforums.org/showthread.php?t=879480&highlight=xubuntu+keyboard](http://ubuntuforums.org/showthread.php?t=879480&highlight=xubuntu+keyboard)
[http://ubuntuforums.org/showthread.php?t=290021](http://ubuntuforums.org/showthread.php?t=290021)

Is there any way of changing the layouts through the GUI?

Thank you.

---

### Post by Michael.Godawski on 2008-12-10
> Alternatively, you should be able to enable the two keyboard layouts by going to System > Preferences > Keyboard, clicking over the the Layout tab, and using the "Add" button.
> 
but with that simple instructions you gave me and later adding the language bar on the upper task bar I was able to change between keyboard layouts with no problem.

Try this as suggested in the first quote, and then add the language bar to the upper task bar by right-clicking on it, selecting add to panel ( or similar, don't have a running xubuntu system now).

---

### Post by billgoldberg on 2008-12-10
> **putanitsa said:**
> I just installed xubuntu, and I would like to be able to swtich between us, canadian multilingual, russian and persian keyboards. How do I do that?

I have been to settings->keyboard preferences->layout . There, I can uncheck "Use X Configuration" and add the layouts I want. But then I don't know how to switch between them.

I have found other threads that touch upon this topic, but I don't understand them:
[http://ubuntuforums.org/showthread.php?t=66115&highlight=xubuntu+keyboard](http://ubuntuforums.org/showthread.php?t=66115&highlight=xubuntu+keyboard)
[http://ubuntuforums.org/showthread.php?t=879480&highlight=xubuntu+keyboard](http://ubuntuforums.org/showthread.php?t=879480&highlight=xubuntu+keyboard)
[http://ubuntuforums.org/showthread.php?t=290021](http://ubuntuforums.org/showthread.php?t=290021)

Is there any way of changing the layouts through the GUI?

Thank you.

I use the command

```
setxkbmap be
```

be is the layout I use.

The American would be "us".

---

### Post by putanitsa on 2008-12-10
Thank you, it worked. I had previously installed the keyboard switching icon *before* adding keyboard layouts in the settings and that's why I couldn't switch. I deleted the keyboard switcher, then I added the layouts and then I added the keyboard switcher and it worked.

---

