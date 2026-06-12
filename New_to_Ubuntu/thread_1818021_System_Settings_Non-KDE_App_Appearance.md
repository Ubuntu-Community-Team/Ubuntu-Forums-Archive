---
title: "System Settings Non-KDE App Appearance"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by Syndacate on 2011-08-04
Hey,

In the system settings, in Kubuntu, I was wondering if it was at all possible to change the appearance of non-KDE applications.

As it stands, the non-KDE applications, such as Firefox, or Pidgin, look like they were rendered on the original X, while all the KDE apps have the smooth Oxygen theme.  Anybody know how to change it?

TIA

---

### Post by james_xxx on 2011-08-04
Syndacate,

Surprised that in 10 hours you had no responses.

To change the appearance of GTK apps in KDE, go to System Settings > Application Appearance > GTK+ Appearance.

I have my GTK+ widget style set to use QtCurve. If you would happen to want to use that widget style, you may need to first install gtk2-engines-qtcurve.

---

### Post by Syndacate on 2011-08-05
> **james_xxx said:**
> Syndacate,

Surprised that in 10 hours you had no responses.

To change the appearance of GTK apps in KDE, go to System Settings > Application Appearance > GTK+ Appearance.

I have my GTK+ widget style set to use QtCurve. If you would happen to want to use that widget style, you may need to first install gtk2-engines-qtcurve.

Yeah, answers for KDE seem more rare.  Nobody really uses it comparatively.  Especially since 4.X.

I'd love to see KDE 4 debloated, personally.  Take all the **** that makes it feel sluggish, I heard KDEMod4 (the Arch Linux modified version) was on the right track, but I haven't checked up on it in awhile.

Anyway, as for KDE on my system...I don't have that "section" - I assume you're talking about on the left hand side of the window...but all I have there is style, colors, icons, fonts, emoticons..and the only thing under style are the Applications/Fine Tuning tabs.

There must be an app you installed to give the GTK+ style functionality to the KDE settings manager.

You're using KWin?

---

### Post by Syndacate on 2011-08-05
I looked into the kde-config-gtk package with no luck - no category shown in the settings.

I also heard of gtk-qt-engine and gtk-qt-engine, can't find either in the repos...or at all on Natty for some reason.

---

### Post by Syndacate on 2011-08-05
I restarted and got the options in the settings manager.

It doesn't seem to matter much because changing the GTK+ theme and hitting apply does absolutely nothing.

---

