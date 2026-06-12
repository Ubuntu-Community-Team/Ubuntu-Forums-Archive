---
title: "Battery and Wireless Icons MISSING!"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-24
Okay, so I accidentally deleted the wireless icon while editing the panels and the battery icon has never shown up! How do I add these?

---

### Post by jrothwell97 on 2010-07-24
Right-click the panel and select "Add to panel..."

In the list of available applets, there should be one called "notification area". Click on its entry, and drag it out to where it should be on the panel - all being well, it should appear.

Good luck.

---

### Post by adamjkok on 2010-07-24
> **jrothwell97 said:**
> Right-click the panel and select "Add to panel..."

In the list of available applets, there should be one called "notification area". Click on its entry, and drag it out to where it should be on the panel - all being well, it should appear.

Good luck.
I got my wireless and BT icons back, but the battery icon is still missing (see screenshot). Suggestions?

---

### Post by jrothwell97 on 2010-07-24
Your best bet is to try logging in and out.

---

### Post by adamjkok on 2010-07-24
> **jrothwell97 said:**
> Your best bet is to try logging in and out.
Just gave your idea three trials (like in science class ;)) and it didn't work. Is there any third-party software that would fill this gap? Do I need to do something as drastic as reinstalling Ubuntu?

---

### Post by RJ12 on 2010-07-24
Do you have your laptop plugged in right now? Ubuntu automatically hides the Battery Indicator as soon as the battery is full, it will reappear when you unplug your laptop from the charger / adapter

---

### Post by Jive Turkey on 2010-07-24
I'm having a similar problem where I deleted the volume control icon by accident.  It now refuses to appear in new instances of the notification area as well.  I have not been able to locate where the notification area stores its configuration.

---

### Post by Anuovis on 2010-07-24
@adamjkok
You might check the settings for the battery icon in *System>Preferences>Power Management*.

Open the general tab and look what is checked there. It might not show because the battery is not charging, depending on the default settings. I use an AC plug so I turned off my icon entirely.

---

### Post by adamjkok on 2010-07-25
> **RJ12 said:**
> Do you have your laptop plugged in right now? Ubuntu automatically hides the Battery Indicator as soon as the battery is full, it will reappear when you unplug your laptop from the charger / adapter
Thanks, that problem's solved. Just realized that the volume icon is also gone though. What do I do about that?

---

### Post by Jive Turkey on 2010-07-25
For me, I needed to add the "Indicator-Applet" from the "add to panel" dialog in order to get the volume icon back.

---

