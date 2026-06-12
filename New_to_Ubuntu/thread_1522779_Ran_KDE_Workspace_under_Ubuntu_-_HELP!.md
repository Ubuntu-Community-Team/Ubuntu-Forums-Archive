---
title: "Ran KDE Workspace under Ubuntu - HELP!"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-07-02
Hi guys

I followed [this guide]("http://digitizor.com/2010/01/01/how-to-get-kde-plasma-workspace-ubuntu-9-10/") to see what the KDE workspaces were like.  During installation it asked whether I wanted to use GDM or KDM and I chose 'KDM'.

While it all worked, I've decided I don't want it and want to revert back to GDM and remove all traces of KDE from my machine.  The guide said that to do this I would simply need to click on the gnome-desktop.sh file on the desktop, however I am still getting a KDE login screen whenever I boot up.

Reading through the guide again, I went back to gconf-editor, re-opened **desktop** -> **gnome**  -> **session** -> **required_components** and re-added the **gnome-panel** value.   I also moved the gnome-desktop.sh and plasma-desktop.sh files to the trash bin.

What else must I do to restore my machine to a pre-KDE state? :-?

Edit: I used command "sudo dpkg-reconfigure gdm" and changed back to GDM, which appears to have got rid of the KDE login screen.  However I would still appreciate if someone more Linux-savvy than myself could glance over that guide and tell me whether there's anything else I need to do to restore my machine to the way it was, as a number of things were installed and tweaked 'under the bonnet'.

---

### Post by Chame_Wizard on 2010-07-02
You have to remove the entire KDE4 desktop(including KDE-base).:popcorn:

---

### Post by sandyd on 2010-07-02
remove every libqt* entry in synaptic.

---

### Post by lkjoel on 2010-07-02
If for some reason, both packages gets mixed up, try LinuxEssentials in my sig.
Extract it then type:
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```
Hope that helps!

---

### Post by danielgrosvenor on 2010-07-02
Thanks for your replies.  Much appreciated. :)

I went into Synaptic Package Manager, did a search for "libqt" and marked every installed entry for Complete Removal.

Is there anything else I ought to do, or some test I can perform to check there's nothing KDE-ish remaining?

---

### Post by lkjoel on 2010-07-03
To be sure that KDE is uninstalled, log out, then when you log back in, check your sessions.
There should be no trace of KDE.

If you want to be sure that KDE is completely uninstalled, try going in the synaptic, search for KDE, then in the package "kde", check its dependencies.

I do not recommend you uninstall "libqt". KDE did not make it, and Qt is a programming language, and many packages depend on it.

---

### Post by -humanaut- on 2010-07-03
sudo apt-get purge kubuntu-desktop

that should get rid of everything including the configuration files.

---

### Post by danielgrosvenor on 2010-07-03
Thanks very much for your help, guys.  That *sudo apt-get purge* command was particularly useful - I'll have to remember that one!

---

### Post by wojox on 2010-07-03
You could also see here [PureGnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by lkjoel on 2010-07-03
> **wojox said:**
> You could also see here [PureGnome]("http://www.psychocats.net/ubuntu/puregnome")
Interesting, but that will conflict any OSS installation, if he did install it.

---

