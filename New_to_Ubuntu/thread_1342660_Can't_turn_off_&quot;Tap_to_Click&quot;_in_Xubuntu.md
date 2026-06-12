---
title: "Can't turn off &quot;Tap to Click&quot; in Xubuntu 9.10"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by nikolas2 on 2009-12-01
Hello,

I am a total 'buntu noob and need some advice. I installed Xubuntu the other day and I can't disable taps on the mouse pad of my laptop. Ubuntu had an option in the menu to do it but I need to stick with X because my hardware is rather dated. 

Any help on this matter would be greatly appreciated.

Thanks,
John

P.S. I don't know how to install anything beyond the "software store" that you just checkmark and download. Any advice on this would be great too :).

---

### Post by PocketDog on 2009-12-01
After 15 minutes checking that this *will* work with Xubuntu, I can confidently say that the following *should* work ;)

Get gconf-editor by running the following command in Terminal 
```
sudo apt-get install gconf-editor
```

Once that's done, run it with the command ```
 gconf-editor 
```

(Don't run with sudo, or it'll change root settings and you won't see any changes on your own account)

In the editor, navigate to ** /desktop/gnome/peripherals/touchpad ** and remove the tick from the box marked '**tap to click**'.

That should be that.

---

