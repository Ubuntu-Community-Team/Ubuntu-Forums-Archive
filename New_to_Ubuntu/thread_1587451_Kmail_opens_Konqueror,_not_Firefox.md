---
title: "Kmail opens Konqueror, not Firefox"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by kallekn on 2010-10-03
I have Firefox set as default browser in Ubuntu, but Kmail insists on opening links in Konqueror. How do I change this?

---

### Post by Silent Warrior on 2010-10-03
I don't have Kmail installed, so I can't say for sure, but you can probably change that in some setting somewhere asking what browser to launch. If it's not available through Kmail, I know I've seen it in Kalternatives. (www-browser-xdg or something; it'll be far down the list, near the bottom.) You'll need root-privileges for this approach, of course.

---

### Post by kallekn on 2010-10-04
What is Kalternatives, and where do I find it in Ubuntu?

---

### Post by andrewthomas on 2010-10-04
```
sudo update-alternatives --config x-www-browser
```

---

### Post by kallekn on 2010-10-04
I have already done that, and selected Firefox. Looks like this:

Det finns 2 val för alternativet x-www-browser (som tillhandahåller /usr/bin/x-www-browser).

  Val          Sökväg            Prioritet  Status
------------------------------------------------------------
  0            /usr/bin/konqueror   100       automatiskt läge
* 1            /usr/bin/firefox     40        manuellt läge
  2            /usr/bin/konqueror   100       manuellt läge


What does "automatic" after Konqueror mean? I suppose it should say "automatic" after Firefox instead, but there is no indication about how to change this.

---

### Post by andrewthomas on 2010-10-04
Ok, you need to open up system settings > default applications > web browser 

then under Default Component click on 
'in the following browser:'  and select firefox from internet menu

---

### Post by kallekn on 2010-10-04
That was the first thing I did. Firefox is selected as default browser, works fine in other programs, not in KMail.

---

### Post by andrewthomas on 2010-10-04
That works fine for me in Kmail.  It took me a while to respond because I had to log into Kubuntu and set up Kmail ( I usually don't use Kmail.)

I would 

```
sudo aptitude purge kmail
```then delete your ~/.kde/share/apps/kmail folder and 

```
sudo aptitude update && sudo aptitude install kmail
```and set it up again.  It should work then.

---

### Post by kallekn on 2010-10-04
Are you sure I need to do that? But why did you need to log into Kubuntu in order to test this? I'm running Ubuntu, don't even know whether there is any Kubuntu left in my system. (Changed from Kubuntu to Ubuntu, because I couldn't get some things running right in Kubuntu.)

---

### Post by andrewthomas on 2010-10-04
> **kallekn said:**
> Are you sure I need to do that? But why did you need to log into Kubuntu in order to test this? I'm running Ubuntu, don't even know whether there is any Kubuntu left in my system. (Changed from Kubuntu to Ubuntu, because I couldn't get some things running right in Kubuntu.)
**Do you have the systemsettings package installed?**

```
aptitude show systemsettings
```
But why did you need to log into Kubuntu in order to test this? 

Because I don't have kmail installed on my ubuntu partition and didn't want to have to install a bunch of dependencies in order to install it

Are you sure I need to do that? No, it could be ~/.kde/share/config/kmailrc that you need to delete although if you are not using the KDE4 system settings package to alter the settings then that may be why it isn't working.

---

### Post by kallekn on 2010-10-04
Hm, there is one more thing that is a bit weird on KMail - when I log in into a running session KMail doesn't react to keyboard input before I have used the keyboard in some other program. Reacts to mouse, though.

Here is the show systemsettings output, it says the systemsettings package is installed.

Paketti: systemsettings
Tila: asennettu
Automaattisesti asennettu: ei
Versio: 4:4.4.2-0ubuntu14
Tärkeys: valinnainen
Ryhmä: kde
Vastuuhenkilö: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Koko purettuna: 1 249k
Riippuvuudet: kdebase-runtime (>= 4:4.4.2), kdelibs5 (>= 4:4.4.2), libc6 (>=
              2.3.4), libfontconfig1 (>= 2.8.0), libplasma3, libqt4-dbus (>=
              4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.6.1),
              libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.1.1), libx11-6 (>= 0)
Korvaavuudet: kde-systemsettings, kdebase-workspace-bin (< 4:4.2.90-0ubuntu2),
              kdebase-workspace-data (< 4:4.2.85)
Kuvaus: KDE 4 System Settings
 System Settings is an improved user interface for configuring the desktop and
 other aspects of the system. 
 
 This package is part of the KDE 4 base workspace module.
Webbplats: [http://www.kde.org/](http://www.kde.org/)

---

### Post by andrewthomas on 2010-10-04
and you are definately using systemsettings to make the change?

---

### Post by kallekn on 2010-10-04
No, I am not. Where do I find that in Ubuntu?? Looks like Kubuntu to me.

---

### Post by andrewthomas on 2010-10-04
type

```
systemsettings
``` in the terminal

---

### Post by kallekn on 2010-10-05
OK. looks like that did it! Why are there so many different places where you can change the default browser, and what is the difference?

---

### Post by Silent Warrior on 2010-10-05
KDE and Gnome read configurations in different places - there's no unified cross-desktop settings-manager. (Well, GTK-libraries are used by a few other desktops and window-managers, but that's the extent of it.) It's as simple as that, really. Changing default browser in Gnome affects Gnome only. Setting the default browser in KDE affects KDE only. Setting the default browser in XFCE affects XFCE only.

---

### Post by kallekn on 2010-10-05
Ok, and when I am running KMail in Ubuntu (Gnome) it is not really running in Gnome, but in KDE, I take it then? A bit confusing, but I suppose it makes sense, as long as one knows which programs are running in which environment... which I don't.

But what other implications does this have, apart from default browsers? Can this be the reason why KMail won't respond to keyboard commands if it is the first program I use after the computer has been in stand by?

---

### Post by Silent Warrior on 2010-10-05
No, you're still using the Gnome-desktop. Kmail and other KDE-apps will just read their configurations from KDE-settings, not Gnome. (Notice how KDE-stuff aren't affect by setting GTK-themes, for example.)
Not sure about the keyboard-thing. It COULD be related, but you aren't running the KDE powermanager in Gnome. (No, REALLY you don't. :) )

---

