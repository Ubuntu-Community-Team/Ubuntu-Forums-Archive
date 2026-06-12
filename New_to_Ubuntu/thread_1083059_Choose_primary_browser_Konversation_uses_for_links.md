---
title: "Choose primary browser Konversation uses for links"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by dorseye on 2009-02-28
In IRC Konversation, when I click a link Opera comes up, but I want it to be Firefox.

Under Preferred Applications my browser is Firefox.

I know that Konversation is a KDE application, so that is probably the reason behind this behavior? So I guess my questions comes down to, how do you interact with a KDE programs functionality from Gnome?

I am running 8.10 Ibex.

---

### Post by snova on 2009-02-28
> **dorseye said:**
> I know that Konversation is a KDE application, so that is probably the reason behind this behavior?

It *is* a KDE program- but a KDE 3 one. It hasn't been ported to KDE 4 yet, so I would guess the settings don't operate over version boundaries.

> So I guess my questions comes down to, how do you interact with a KDE programs functionality from Gnome?

Normally.

Either way, it can be set from Konversation itself. Open Settings -> Configure Konversation, Behavior -> General, and try putting

```
firefox '%u'
```

in 'Use custom web browser'. (The command may be slightly different, I don't know.)

---

