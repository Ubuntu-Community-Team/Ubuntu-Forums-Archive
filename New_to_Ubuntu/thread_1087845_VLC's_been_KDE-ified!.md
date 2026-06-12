---
title: "VLC's been KDE-ified!"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by Kareeser on 2009-03-05
So.

I decided to try KDE for fun last night.

```
sudo apt-get install kubuntu-desktop
```

Great! Except now, when I run VLC in a GNOME session, the window is... erm... KDE-ified.

Single-click now opens a folder, menu decorations are reminiscent of KDE..

Agh! How do I change it back!!

---

### Post by cc8balla on 2009-03-05
Do you not want KDE anymore?

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

If you want to keep it, go to your home folder, show all hidden files, then go to .config. Delete the VLC folder, and VLC should make a new default config when it starts up next.

---

### Post by bobbob1016 on 2009-03-05
I tried KDE the same way.  KDE sets everything to KDE automatically, the bootup screen, and file associations.  That means when you open a folder, you are using dolphin (KDE's file manager) not nautilus (gnome's file manager).  I wasn't able to find a way to have one set of associations for KDE and another for Gnome.

Basically, you have to open a terminal, type "nautilus" without quotes, and press enter.
Then right click any folder, and click properties.  Select "Open With" and change it from dolphin to nautilus (might be called "Open Folder" with a orange-brown folder) then click Close.

Not sure about how to get VLC to be Gnomed and not KDE-ed anymore.

---

### Post by Kareeser on 2009-03-05
I was hoping that GNOME and KDE would co-exist peacefully, but I guess that's a pipe dream :)

Thanks for the help, both of you. Uninstalling KDE now. It's a shame.. it's a neat DE. Perhaps I'll give 4.2 a try in a new install :)

---

### Post by gandaran on 2009-03-05
> **Kareeser said:**
> So.

I decided to try KDE for fun last night.

```
sudo apt-get install kubuntu-desktop
```

Great! Except now, when I run VLC in a GNOME session, the window is... erm... KDE-ified.

Single-click now opens a folder, menu decorations are reminiscent of KDE..

Agh! How do I change it back!!
VLC is and always has been a KDE application, thats why I will never use it, only GTK applications on my beloved gnome!

---

### Post by Kareeser on 2009-03-05
You're right.

VLC's been marred, now it has no theme at all. *sigh*

---

### Post by marco123 on 2009-03-05
> **Kareeser said:**
> I was hoping that GNOME and KDE would co-exist peacefully, but I guess that's a pipe dream :)

Thanks for the help, both of you. Uninstalling KDE now. It's a shame.. it's a neat DE. Perhaps I'll give 4.2 a try in a new install :)

Just install kde-core instead of the whole Kubuntu desktop.

Cheers, Marco.

---

### Post by maybeway36 on 2009-03-05
It might be in the .qtrc or .config/Trolltech.conf. VirtualBox did this to me too. They both use Qt, and KDE sets its Qt theme to be your default Qt theme for all your apps.

---

### Post by Simian Man on 2009-03-05
> **marco123 said:**
> Just install kde-core instead of the whole Kubuntu desktop.

Cheers, Marco.

QFT.  Why do people insist on telling people to install _buntu-desktop just to install a new DE??

---

### Post by SuperSonic4 on 2009-03-05
> **marco123 said:**
> Just install kde-core instead of the whole Kubuntu desktop.

Cheers, Marco.

Seconded, kde-core is far lighter than the whole desktop and saves having two apps for every purpose

---

### Post by hammad1337 on 2009-03-08
Just writing to confirm what I think.

Istalling kde-core means, just getting the kde 4 desktop without the kde apps and app settings? true?

If it is, i cant wait to try kde...

woohoo!!

someone, please confirm  what i said above, really is the case.

---

### Post by billgoldberg on 2009-03-08
> **gandaran said:**
> VLC is and always has been a KDE application, thats why I will never use it, only GTK applications on my beloved gnome!

No it has not.

The newest version is QT.

The previous versions used Wxwidgets.

---

### Post by billgoldberg on 2009-03-08
> **hammad1337 said:**
> Just writing to confirm what I think.

Istalling kde-core means, just getting the kde 4 desktop without the kde apps and app settings? true?

If it is, i cant wait to try kde...

woohoo!!

someone, please confirm  what i said above, really is the case.

Yes, hence the word "core".

---

### Post by Kareeser on 2009-03-15
Supposedly true, but the file dialogue in VLC used KDE's file management settings... (one click = execute, instead of select)..

---

