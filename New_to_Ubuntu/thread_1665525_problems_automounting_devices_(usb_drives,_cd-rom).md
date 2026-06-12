---
title: "problems automounting devices (usb drives, cd-rom)"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by japcrword on 2011-01-12
Previously, when I inserted a flash-drive or CD, the media somehow magically got discovered and appeared mounted on Desktop. Now nothing happens when I insert flash or cd. When I click Places->Computer the error message "Nautilus cannot handle "computer" locations" shows up. I can mount usb drive manually using this guide ([http://www.novell.com/coolsolutions/feature/11637.html]("http://www.novell.com/coolsolutions/feature/11637.html")). So, I guess, not everything's lost :)

Can someone give me advice what shall I do to resolve the problem? Automount is really handy for me, I'd like to have it back. Thanks in advance.

---

### Post by khelben1979 on 2011-01-12
When you mean: previously, is that before smaller updates to your Ubuntu system or have you made a big upgrade of the whole system?

I'm not exactly sure why it looks like it does at the present, but it may be that it's permission issue and that the system has been configured with higher security settings thereby not allowing an ordinary user access to these storage mediums.

Each user in Ubuntu have their permissions determined by the superuser or root and you can graphically tick in boxes what the user has rights to do and this can be the cause of the problem, or.. if it's not, then solving this issue would be to use KDE instead of GNOME.

---

### Post by japcrword on 2011-01-13
By 'previously' I meant previous login session. I suspect this might be connected with upgrading GTK+ library and necessary dependencies (GdkPixbuf and glib). I probably messed up something while compiling and installing. Actually, presently I've got a bigger problem: my graphical desktop environment doesn't load to its 100% ([http://ubuntuforums.org/showthread.php?p=10351250#post10351250]("http://ubuntuforums.org/showthread.php?p=10351250#post10351250")). I have to resolve this first till I can do anything else. 

Thanks for the reply. Still can you give me a few hints on how to bring the dialog with user permission settings and especially how can I install KDE instead of GNOME?

---

### Post by khelben1979 on 2011-01-13
```
sudo apt-get install kde
```
installs [KDE]("http://en.wikipedia.org/wiki/Kde").

```
df -h
``` will display if your system have any problems with disk space, it can cause problems with your system. How does it look like?

---

