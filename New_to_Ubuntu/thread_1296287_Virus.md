---
title: "Virus"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by windows hater on 2009-10-20
**** so my problem is i was mainly using windows to play games however i suspected i might have a virus. When I was playing source everything locked up so i just did a reboot and now every time I boot into safe mode the windows logo loads and then it restarts and so then i booted into ubuntu and everything is fine so i was wondering if there is a program within ubuntu that scans the hard drive for virus. reinstall is an option i really dont want to do.

    THANK YOU

---

### Post by donkyhotay on 2009-10-20
clamav is the only one that comes to mind. It's a linux virus scanner that scans primarily for windows viruses.

---

### Post by martrn on 2009-10-20
[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html")

```
sudo apt-get install clamav
sudo apt-get install clamtk
```

You could search the internet for clam Anti-Virus, as there are lots of front ends, but only one engine or back-end for anti-virus on ubuntu.

This will only remove anti-virus from windows or cedega/wine installations and will not remove root-kits or Trojans from linux systems.

---

### Post by desperado665 on 2009-10-20
> **donkyhotay said:**
> clamav is the only one that comes to mind. It's a linux virus scanner that scans primarily for windows viruses.
+1
You can boot ubuntu and run ClamAV on your windows partition. It will pick up any present viruses there.

But it sounds to me like your boot file system may be corrupt. You might try booting your windows disc and choose repair windows.

---

### Post by rustutzman on 2009-10-20
What Windows version? More than likely you'll need to run a repair in Windows. If you do it will probably overwrite grub so be prepared to reinstall grub to get back to your Ubuntu install.

Russ

---

### Post by Nostalos on 2009-10-20
While Annoying, that does not sound like a virus.  Sounds more like corrupted boot/system files and a windows repair is more likely going to be your only recourse.

---

### Post by XxionxX on 2009-10-20
"Just re-install Windows" the eternal bane of using Windows.

---

### Post by bacardiandwatermelon on 2009-10-20
Running..
```
chkdsk /R
```In the windows recovery console will probably fix your prob.. Failing that you can just do a repair..

---

### Post by MelDJ on 2009-10-21
see: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) for more antivirus software

---

### Post by 3rdalbum on 2009-10-21
If Windows is rebooting on startup, then it usually means that it has "blue-screened". The default setting in Windows is to reboot instead of displaying the blue screen.

Viruses don't cause system crashes and they don't cause BSODs on startup, unless they are extremely buggy viruses. My intuition says that this isn't a virus, this is just a regular Windows self-destruct and you'll need to "repair install" or just plain reinstall Windows.

---

### Post by Onesimus on 2009-10-21
If you think you have a virus on your Windows partition why don't you just run a virus scan from Windows.  There are many free virus scanners for Windows (e.g. [http://www.avast.com]("http://www.avast.com"))

I am not sure why you are wanting to complicate matters by doing it from Ubuntu.

---

### Post by 3rdalbum on 2009-10-21
> **Onesimus said:**
> If you think you have a virus on your Windows partition why don't you just run a virus scan from Windows.

Re-read the original post.

---

### Post by wobin77 on 2009-10-21
in windows repair:

```
chkdsk /r
```
edit: someone posted this already...

---

