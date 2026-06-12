---
title: "KDE hates my keyboard"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by GepettoBR on 2009-05-04
This seems to be a general problem with KDE applications running in a GNOME session, for some reason they refuse to correctly input my "special" characters. They recognize my keyboard layout just fine (Brazil - QWERTY) but won't input characters with accents, like ó, ê or à. It recognizes ç, which has its own key, but nothing that requires me to hit first the accent key and then the letter key. How do I solve this?

I uninstalled SCIM, but this merely propagated the problem to my other apps as well, so I reinstalled it. Configuring it through SKIM didn't work either. I have language-pack-kde-pt and language-pack-kde-pt-base installed (in fact, every package that includes language-pack and pt is installed).

I have confirmed this problem in Amarok 2, Kopete, QTPFSGUI and the file manager windows within these programs, though I don't really know if it's Dolphin or Konqueror.

Running Jaunty x64 with the KDE apps installed individually (not as part of any DE metapackage). The only X session available to me is GNOME.

---

### Post by GepettoBR on 2009-07-03
Two-month bump, this is still a problem.

---

### Post by kellemes on 2009-07-04
> **GepettoBR said:**
> This seems to be a general problem with KDE applications running in a GNOME session, for some reason they refuse to correctly input my "special" characters. They recognize my keyboard layout just fine (Brazil - QWERTY) but won't input characters with accents, like ó, ê or à. It recognizes ç, which has its own key, but nothing that requires me to hit first the accent key and then the letter key. How do I solve this?

I uninstalled SCIM, but this merely propagated the problem to my other apps as well, so I reinstalled it. Configuring it through SKIM didn't work either. I have language-pack-kde-pt and language-pack-kde-pt-base installed (in fact, every package that includes language-pack and pt is installed).

I have confirmed this problem in Amarok 2, Kopete, QTPFSGUI and the file manager windows within these programs, though I don't really know if it's Dolphin or Konqueror.

Running Jaunty x64 with the KDE apps installed individually (not as part of any DE metapackage). The only X session available to me is GNOME.

Hi,
  I have no Gnome available, working from KDE.
I've looking into the keyboard conf-screen of KDE and am able to select Brazilian with dead-keys (this is what you want).
One problem.. dead-keys are not working.. (bug?) Maybe.. because when I select Brazilian **without** dead-keys it works fine!

Anyway.. try from CLI one or both and see if this works for you:
```
setxkbmap -model pc104 -layout us,br -variant intl
```
```
setxkbmap -model pc104 -layout us,br -variant intl,nodeadkeys
```
Last command enables dead keys for me.. strangely enough.

---

### Post by GepettoBR on 2009-07-04
> **kellemes said:**
> Hi,
  I have no Gnome available, working from KDE.
I've looking into the keyboard conf-screen of KDE and am able to select Brazilian with dead-keys (this is what you want).
One problem.. dead-keys are not working.. (bug?) Maybe.. because when I select Brazilian **without** dead-keys it works fine!

Anyway.. try from CLI one or both and see if this works for you:
```
setxkbmap -model pc104 -layout us,br -variant intl
```
```
setxkbmap -model pc104 -layout us,br -variant intl,nodeadkeys
```
Last command enables dead keys for me.. strangely enough.

This didn't work, though it did manage to switch all of my accent keys around. This also affected my GNOME apps. Using the GNOME keyboard configuration GUI, I returned to my previous condition, but KDE apps still don't recognize my input correctly.

Thanks anyways, I appreciate you taking the time to try helping me out.

---

