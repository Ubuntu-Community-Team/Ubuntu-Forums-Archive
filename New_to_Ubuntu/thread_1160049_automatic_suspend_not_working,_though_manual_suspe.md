---
title: "automatic suspend not working, though manual suspend ok"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by mayoban on 2009-05-15
Dear All,

I have no problems when manually suspending of hibernating my laptop using either the power button on gnome panel or the gnome power management gui.

But my laptop **never goes to sleep automatically** after the time specified in the gnome power management gui.

I have laptop-mode enabled in acpi support and that works fine.

Does anyone know what the problem could be?

I found an older thread with the same issue, but the solution seemed rather harsh to me: [http://ubuntuforums.org/showthread.php?t=429949&highlight=manual+suspend+ok%2C+automatic](http://ubuntuforums.org/showthread.php?t=429949&highlight=manual+suspend+ok%2C+automatic)

Do you know, if there are simpler ways?

Cheers, mayoban

---
I am using Ubuntu 9.04, 64-bit version
on a Lenovo Thinkpad R400, Type 7439-A85
Gnome Desktop with Compiz Window Manager and Cairo-Dock

---

### Post by mayoban on 2009-05-20
**Addendum:** Today, I realized by chance, that my laptop does suspend at the configured 30 min when connected to the AC supply.

But it still will not supend when on battery. Is that not strange? All hints are welcome.

Cheers, mayoban

---

### Post by gwhaller on 2009-06-14
Same problem here.

I'm quite sure there's a problem with gnome-screensaver, but with pm-utils.

---

### Post by gwhaller on 2009-06-14
Fixed it!
Gnome-power-manager frontend not showing the truth.
Better go into gconf/apps/gnome-power-manager/actions
sleep-type-battery was set to nothing! -> changed it to suspend

---

### Post by mayoban on 2009-06-15
Hi gwhaller,

Thank you for your reply! I had trouble finding the right directory and file from your description, even when I searched for gnome-power-manager on the whole system. Could you specify the exact path of the directory? That would be great.

If the gnome power management gui is not doing what it says it would, should we file a bug report in this case?

Cheers, mayoban

---

### Post by gwhaller on 2009-06-15
Hi mayoban,


Press Alt-F2 to open the *Run Application *dialog. Type *gconf-editor *and press enter
Navigate to *apps -> gnome-power-manager -> actions*

In my case:
*sleep-type-battery* was set to *nothing*

Dobble-klick and change *nothing *into *suspend*

Hope I could help
Gary

---

### Post by mayoban on 2009-06-24
Hi gwhaller,

That did the trick! Thanks a lot for your help!

Cheers, mayoban

---

