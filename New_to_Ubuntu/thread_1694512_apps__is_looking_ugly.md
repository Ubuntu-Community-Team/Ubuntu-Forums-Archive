---
title: "apps  is looking ugly"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by ajaykumar.b on 2011-02-24
I am using ubuntu 10.10 ,and installed kubuntu on it.In kde4.6 the apps are looking very ugly.Some thing is wrong.I am attaching the snapshots.
can some one help me to fix this

Thank you
Ajay

---

### Post by _0R10N on 2011-02-24
Is this a fresh installation? In that case try disabling special visual effects. You can also check what driver Ubuntu has enabled for your graphic card.

---

### Post by james_xxx on 2011-02-24
The apps that are not looking to you as they should are all GTK apps. To change the appearance of GTK apps, go to System Settings>Application Appearance>GTK+ Appearance, then select QtCurve (or whatever you want), then click 'apply'. That should rectify things for GTK apps that are not needing root permission to run. Normally this is the default behavior.

Also, why in the world are you using Compiz in Kubuntu?

KDE4 has it's own, native compositing windows manager.

---

### Post by clhsharky on 2011-02-24
ajaykumar.b

Compiz is not native to KDE, mixing Gtk apps in KDE(Qt)dont alway mix well in looks.
Kwin is default compositor in KDE not compiz. and considered superior by many.
To each his own.

Sharky

---

### Post by ankspo71 on 2011-02-25
Hi,
Kubuntu only installs one gtk theme engine for KDE by default. It is called Raleigh, and that is what is making your GTK apps look Win98-ish.

I recommend to install the "Oxygen GTK" debian (deb) package from here:
[http://kde-look.org/content/show.php/?content=136216](http://kde-look.org/content/show.php/?content=136216)
This will give you a matching GTK theme engine for the Oxygen theme.

Or there is another called Oxygen-Molecule. It can be found in the repositories. 

Another option is to install QtCurve. It's an entirely different theme engine (in both appearance and configuration) for KDE and GTK applications.

After you install another GTK theme engine for KDE, you can go to System Settings > Application Appearance > GTK+ Appearance > Widget Style: Then choose your prefered gtk theme engine from the small dropdown menu.

Hope this helps.

---

