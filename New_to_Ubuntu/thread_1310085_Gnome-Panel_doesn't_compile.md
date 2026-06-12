---
title: "Gnome-Panel doesn't compile"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Azrael3000 on 2009-11-01
Hi,

I'm currently trying to get the patches mentioned on:
[http://versia.com/2009/09/06/vertical-panel-in-gnome-15-months-later/](http://versia.com/2009/09/06/vertical-panel-in-gnome-15-months-later/)
to run.

I was succeeding with the first one but now I'm on to the second one regarding the notification area. So what I need to do is compile gnome-panel.
The commands I was using are:
```
cd ~
mkdir gnome-panel
cd gnome-panel
apt-get source gnome-panel
wget -O notification.patch http://bugzilla-attachments.gnome.org/attachment.cgi?id=140510
cd gn*
patch -p1 < ../notification.patch
sudo apt-get install gnome-devel
sudo ./configure
sudo make
sudo make install
```./configure ran nicely but during make I got the following error.

```
calendar-window.c:46:42: error: libgnome/gnome-desktop-utils.h: No such file or directory

```So I did some search and came up with pages like [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg643034.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg643034.html)
So it obviously is related to an old version of libgnome-desktop-dev. More precisely it doesn't work for 2.11 but >= 2.26 should be ok. According to Synaptic I have libgnome-desktop-dev version 2.28.1-0ubuntu2 installed which should be fine. However if I look into my /usr/lib I only have a libgnome-desktop-2.so.11.4.2 file. Is this now the correct version? (edit: it should be from what I found out)

If there's any solution to my problem I'd be grateful to know. If you need more information about my system please let me know.

[edit]
Tried the same on a different machine, same result (although I didn't apply the patch, which shouldn't influence that file anyway).
Compiled gnome-desktop by hand, works but still I get the same error when compiling gnome-panel.

[COLOR=red]**Solution #1**[/COLOR]
A quick and dirty hack:
Copy the gnome-desktop-utils.h (from the sources of libgnome-desktop-dev) file into a newly created directory applets/clock/libgnome.
Compile and be happy.

**Bug report:** [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/470757](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/470757)
[/edit]

Thanks,
Arno

P.S: Not directly related but is Alt+Shift+Tab not working anymore? (Cycle through open windows backwards)

---

### Post by jacksonpollack on 2009-11-02
Ah! I was wondering what the heck was wrong when I tried to compile gnome-panel in Karmic in order to get rid of that ugly little black arrow.
Thanks for the info!

Oh, and it would seem that Alt+Shift+Tab is turned off by default. You can turn it back on using the compizconfig settings manager (go to Window Management -> Static Application Switcher).

---

### Post by Azrael3000 on 2009-11-03
Wrong button I looked at. You are right though, thanks.

---

