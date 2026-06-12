---
title: "No video in movie player"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by jfreak_ on 2011-04-14
Well , a friend just installed 9.10 (yes you heard that right) and he called me over to install the nvidia driver. He was watching a movie when I entered and I then installed the driver and activated the eye-candy. Now there is no video in any of the players (totem,vlc,smplayer) but audio can be heard. Help!

---

### Post by Joe of loath on 2011-04-14
Well, the obvious thing is to update to a newer version, see if that fixes the bug. 9.10 has approximately two weeks of support left ;)

---

### Post by jfreak_ on 2011-04-14
I know, but my friend has a copy of windows on his hd and some expensive software as well so he is reluctant to do anything which might mess up things.( and i lack the expertise to clean up the mess)  :-/

---

### Post by Joe of loath on 2011-04-14
Surely if he just installed 9.10, it won't hurt to uninstall and replace it with 10.04 or 10.10?

---

### Post by searchfgold6789 on 2011-04-14
[SIZE=1]Behind me?! EEK! gasp gasp. No one there.[/SIZE]

I'm gonna also suggest the upgrade.
An upgrade will not even touch the Windows partition, the most it will do that even has to do with the Windows partition would probably be gently updating grub.

I would be only slightly more worried about the Ubuntu OS, but 99% of the time the upgrade goes OK. Especially if it is a recent install.

According to me, having the video fixed would highly outweigh the risks that go along with an upgrade.

---

### Post by 3rdalbum on 2011-04-14
The Nvidia driver has a delightful bug that causes some models of graphics card to not be able to use certain video output modules. Nvidia's engineers never actually fix the bug, they just move it to different cards for a couple of versions.

You need to change the video output module to X11, or if it's already X11, change it to X-Video. VLC and Gnome Mplayer make it easy to do, but for Gstreamer-based programs (such as Pitivi Video Editor and Totem Movie Player) you need to take a trip to Gconf-editor.

---

### Post by SeijiSensei on 2011-04-14
Did you install the proprietary driver from the "Hardware Drivers" applet in Ubuntu?  If the video card is an NVIDIA 8xxx or newer, you might want to try VDPAU.  First, check that the libraries exist by looking to see if /usr/lib/libvdpau.so.1 is present.  If so, use smplayer and go to Tools > Preferences > General (I think that's right) and click the video tab.  Choose VDPAU as the driver from the drop-down box at the top of the dialog box.

If you're comfortable with the command line, you can try:

```
mplayer -vo vdpau /path/to/video/file
``` 

and see what happens.  If it doesn't work, mplayer will spit back a lot of information that will help you diagnose the problem.

---

