---
title: "using gnome, want to try kde and xfce"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by aBitLater on 2009-02-02
Hi, 
I would like to try KDE and XFCE, but I don't want my Gnome to get messed up (so I can revert back whenever I want)... what is the easiest way to accomplish this

Also, how should I go about removing KDE later (assuming I don't like it) and all applications that are only used in KDE - and the same with XFCE.

Thirdly, I want to try KDE 4 - the screenshots look nice, but is it stable?  Are the apps that run on it stable, for the most part?

Many thanks

---

### Post by owenll on 2009-02-02
Try this for starters: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by dawynn on 2009-02-02
Here's a thought:

> deborphan -a > filename.txt

This gives you a listed snapshot of exactly what your system currently has installed.  It won't list all the packages (use dpkg -l > filename2.txt for that), just the packages that have no packages that depend on them.

To try out other GUI's, do the following:

For XFCE, go to your favorite package manager and install xubuntu-desktop.

For KDE, go to your favorite package manager and install kubuntu-desktop.  For Hardy and earlier releases, this will install a version of KDE 3.  For Intrepid and later releases, this will install a version of KDE 4.  Hardy may have something like a kubuntu4-desktop.  KDE 4 was not available (except perhaps in backports repositories) for earlier releases than Hardy.

Side note: As I understand it, KDE 4 has been rushed out to the masses.  4.0 was really more or less a Beta.  4.1 really laid a lot of the groundwork, but still had a lot of rough edges.  It's my understanding that KDE 4 series is supposed to "mature" with 4.2.  Note that even Linus Torvalds has switched away from the KDE 4 series during this transitional time period.

If you choose to remove any of these other desktop options, remove the '-desktop' package, remove any automatically installed components, and run a new deborphan report, comparing it against your original report.  Anything new that you don't recognize was likely installed by the package manager, even if it wasn't marked as an auto-install.

These -desktop options should be able to live side by side.  If they don't, try going into "aptitude" (yes, it's a command-line tool) and just selecting the majority of packages that the '-desktop' module depends upon, avoiding any that cause conflict with packages already on your system.

You'll choose your GUI for each session at your logon tool (gdm, kdm, xdm).  I have found that some GUI's do not work as well if they are not using their own native login tool.  Primarily, this affects shutdown options.  So, for example, using gdm with KDE, and asking for a "shutdown" from KDE may grop you back to a login instead of shutting down the system (OK -- so this might not be the magic combination, but I have had issues like this in the past.  Nothing breaks, but its an annoyance to have to ask twice for "shutdown".)

Note that some settings get established by a fresh install that are not applied by upgrades like these.  If you decide that you prefer a different GUI, consider doing a fresh install of the GUI the next time you upgrade to a new release.

Many tools leave behind user options in your personal home storage area.  So, after "flushing" a GUI, it's worth going back into your $HOME/user area with a file manager and looking at all the hidden files.  Removing any that pertain to the flushed system will cause the system to build new default config files the next time you use that piece of software.

It's worth noting that each user typically finds a few tools that they like that don't belong with the GUI.  For instance, I liked Synaptic (a gtk-based tool) even when I was still using KDE.  Now that I've moved over to Gnome, and more recently XFCE, I still prefer Kdevelop and Soundkonverter to their Gnome counterparts.  And each GUI can run the tools for the other GUI's just fine (that was hashed out years ago).  Don't be afraid to experiment with tools from the other GUI's.

---

### Post by aBitLater on 2009-02-04
thank you dawynn for your very thorough response.

I didn't even bother with trying to get to KDE 4.2 after seeing how bad kubuntu's KDE 4.1 is.  I wanted to love it.  I really did.  It looks really promising.  Too bad that just about every part of it is broken !!

---

