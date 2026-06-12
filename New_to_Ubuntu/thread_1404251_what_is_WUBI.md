---
title: "what is WUBI?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by karthick87 on 2010-02-11
I am not much familiar with  linux...Can some one say me about WUBI?What is it?

---

### Post by doas777 on 2010-02-11
wubi is a really stupid (imho) installer for ubuntu that runs within windows. it installs like an applicaiton, so it is theoretically easy to uninstall. that said, it's really hard to turn it into a "full ubuntu" system, since windows is required, and it has some unpredictable support idiosyncrasies.

don't get me wrong, it fits the purpose for which it was designed, but it seems like a kludge to me.

---

### Post by wobin77 on 2010-02-11
> Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by muteXe on 2010-02-11
Imo, it's only a bit better than just trying the Live CD,  but no where near as great a full blown installation.

---

### Post by bumanie on 2010-02-11
Wubi is basically an installer for windows - wubi installs ubuntu inside windows a bit like virtualised disc (but not quite the same) - windows sees the wubi install like it sees any other installed programs and it can be uninstalled via add/remove/uninstall program etc. Probably the easiest method these days is to use the wubi installer method - see [here]("http://wubi-installer.org/")If you like ubuntu, you can later move it to it's own dedicated partition - see [here]("http://lubi.sourceforge.net/lvpm.html")It's really a chance for a new user to see what ubuntu is about without needing to partition ones hard drive

---

### Post by karthick87 on 2010-02-11
Thanks a lot..

---

### Post by 3rdalbum on 2010-02-11
Don't get me wrong, it's useful if you want to install Ubuntu as a trial run before deciding whether to keep it, because there's no need to partition your drive to use Wubi.

However, if you decide you want to keep Ubuntu, you'd need to remove the Wubi installation and boot from the CD and partition your hard disk.

Due to technical reasons, if Windows crashes and won't boot up anymore, you also won't be able to get into your Wubi Ubuntu until you've managed to get Windows to start up again. A regular dual-boot installation of Ubuntu doesn't have this limitation.

---

### Post by Lull on 2010-02-11
Hi,

I'm new to Ubuntu as well, and I used Wubi to install it.
Now I can't locate the .emacs file, could this have anything to do with the fact that I used Wubi for the installation?

I looked in the home directory and tried to search for ".emacs" from the file system.

Thanks,
-Louise

---

### Post by muteXe on 2010-02-11
Open a terminal go to your home folder and type "ls -a". is it there?

---

### Post by philinux on 2010-02-11
> **Lull said:**
> Hi,

I'm new to Ubuntu as well, and I used Wubi to install it.
Now I can't locate the .emacs file, could this have anything to do with the fact that I used Wubi for the installation?

I looked in the home directory and tried to search for ".emacs" from the file system.

Thanks,
-Louise

You need to press ctrl h or View>show hidden files.

Config folders start with a "." which hides them from normal view.

By the way, it's best to start your own threads. It can get confusing otherwise.

---

### Post by Lull on 2010-02-11
Hi,

Sorry I should have said I already did that.
There is still no .emacs file.

All there is in the home directory when using ls -a is:

.
..
.bash_history
.bash_logout
.bashrc
.cache
.config
.dbus
Desktop
.dmrc
Documents
Downloads
.emacs.d
.esd_auth
examples.desktop
.fontconfig
.gconf
.gconfd
.gksu.lock
.gnome2
.gnome2_private
.gnupg
.gstreamer-0.10
.gtk-bookmarks
.gvfs
.ICEauthority
.local
.mozilla
Music
.nautilus
Pictures
.profile
Public
.pulse
.pulse-cookie
.recently-used.xbel
.ssh
.sudo_as_admin_successful
Templates
test.txt
text.txt
.thumbnails
.update-manager-core
.update-notifier
Videos
.xsession-errors
.xsession-errors.old

Thanks,
-Louise

---

### Post by philinux on 2010-02-11
[http://devcraft.wordpress.com/2009/07/19/emacs-configuration-in-github/](http://devcraft.wordpress.com/2009/07/19/emacs-configuration-in-github/)

---

### Post by Lull on 2010-02-11
Hi,

Ahhh now I got it, according to:

[http://www.gnu.org/software/emacs/windows/Installing-Emacs.html#Installing-Emacs](http://www.gnu.org/software/emacs/windows/Installing-Emacs.html#Installing-Emacs)

"the .emacs file may be called _emacs for backward compatibility with DOS and FAT filesystems "

And as I have Windows 7 and have installed Ubuntu via Wubi...

So I searched for a _emacs file instead, which did the trick.

Thank you for helping,
-Louise

---

