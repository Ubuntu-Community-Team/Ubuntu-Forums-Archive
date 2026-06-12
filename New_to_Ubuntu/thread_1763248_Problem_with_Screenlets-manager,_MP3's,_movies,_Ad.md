---
title: "Problem with: Screenlets-manager, MP3's, movies, Adobe Flash."
date: 2011-05-20
forum: New to Ubuntu
---

### Post by andrei90 on 2011-05-20
Greetings,

I have a few problems:
1. **Screenlets-manager won't open**, I installed and look what it says:
```
andrei@ubuntu:~$ cd /usr/local/share
andrei@ubuntu:/usr/local/share$ screenlets-manager
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 29, in <module>
    from screenlets import utils,install
ImportError: cannot import name install
```

2. **MP3 won't work**, I don't have the plug-ins or drivers, I don't know how to install them.

3. I **can't play any movie** I have in my PC, I don't have the drivers, where can I find them and how can I install them?

4. **Adobe flash**, when I click on a YouTube vid, it's not working, I downloaded the flash archive and I didn't knew how to install it.

I am using:
```
andrei@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

Thank you in advance!

---

### Post by andrei90 on 2011-05-20
I managed to fix 2,3 and 4 I found the command for drivers.
But the screenlets is still annoying, I rebooted and still no answer from it..

---

### Post by coffeecat on 2011-05-20
I can't help you with 1, but for 2,3 and 4, install the package xubuntu-restricted-extras. This will bring in most of the audio/video codecs you will need, flash, java and microsoft core fonts.

When you say "movie", do you mean a DVD? If you want to play a commercial DVD you need the libdvdcss2 library installed. Two ways:

1 - Go to [http://medibuntu.org/](http://medibuntu.org/) and enable the repository as described under the Repository Howto tab and then you will be able to install libdvdcss2 from whatever package manager you use in Xubuntu.

Or...

2 - Do this only after installing xubuntu-restricted-extras. If you haven't installed libdvdread4 which comes as a dependency of the restricted-extras package this command won't work. Open a terminal, and:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

**EDIT**: OK, I see you found the answer to 2,3,4 while I was posting.

---

### Post by andrei90 on 2011-05-20
Thank you!
No not DVD's, I was reffering to normal formats: avi, mpeg etc
But I'm really curious, can I play Blu-rays with restricted-extras drivers?

---

### Post by coffeecat on 2011-05-20
Ah. Blu-Ray! I take the easy way out and use my Sony PS3 to play Blurays, so I know next to little about Blu-Ray on Ubuntu. Here's a link for you:

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I notice it hasn't been updated since December last and I seem to remember that there was something new about Blu-Rays in Natty, but I can't remember what that was. Whatever - that link might be a bit out-of-date, but it has some useful information.

---

### Post by andrei90 on 2011-05-20
Thank you.
I've checked screenlets again and I thought it has something to do with python, but apparently it doesn't:
```
andrei@ubuntu:~$ apt-cache show screenlets | grep Depends
[COLOR="Red"]Depends:[/COLOR] python (>= 2.4), python-support (>= 0.90.0), python-gobject, python-gtk2, python-gnome2, python-dbus, python-cairo, python-wnck | python-gnome2-desktop, python-gst0.10, python-xdg, python-gconf
[COLOR="red"]Depends:[/COLOR] gconf2 (>= 2.28.1-2), python (>= 2.4), python-support (>= 0.90.0), python-gobject, python-gtk2, python-gnome2, python-dbus, python-cairo, python-wnck | python-gnome2-desktop, python-gst0.10, python-xdg, python-gconf
```

---

