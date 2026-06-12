---
title: "How do I set the toolbar to display icons only?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by klemperal on 2010-04-29
In previous versions of Ubuntu you could change the toolbar icons / text in the Appearance preferences.  In Lucid however, for whatever reason, they seemed to have removed that from the Appearance menu.  Anyone know another way(s) to set the toolbar to display icons only?

---

### Post by madjr on 2010-04-29
[http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html](http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html)

---

### Post by djchandler on 2010-04-29
> **klemperal said:**
> In previous versions of Ubuntu you could change the toolbar icons / text in the Appearance preferences.  In Lucid however, for whatever reason, they seemed to have removed that from the Appearance menu.  Anyone know another way(s) to set the toolbar to display icons only?

The default is icons only.

I could be wrong about this, but this version of Gnome fundamentally changes the way GUI variables are changed. That key used to be editable with gconf-editor. I don't see that changing this key makes a difference. It could be that setting is now a part of the theme description, which overrides these key settings.

/desktop/gnome/interface/toolbar_style

---

### Post by cb951303 on 2010-04-30
> **madjr said:**
> [http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html](http://www.omgubuntu.co.uk/2010/04/easily-access-missing-interface-tab.html)

ahh, thanks for this. I was going nuts. I knew there was a settings tab but I just couldn't find it.

way to go GNOME developers, you just can't dumb down the UI enough.
I'm waiting for the day where every application in GNOME desktop will only have a button. From what it seems, that's what they are after.

---

### Post by Seq on 2010-04-30
> **cb951303 said:**
> I'm waiting for the day where every application in GNOME desktop will only have a button. From what it seems, that's what they are after.If they can do what I want with one button, why not?

---

### Post by cb951303 on 2010-05-01
> **Seq said:**
> If they can do what I want with one button, why not?

they can't, that's the problem.

---

### Post by Seq on 2010-05-01
> **cb951303 said:**
> they can't, that's the problem.

Which is why we still have more than one button.

---

