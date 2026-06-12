---
title: "Sound options in 9.10"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Lvcoyote on 2009-11-11
Where are all the sound options in 9.10, and where are all the system sound files stored??  Is this an add on package or something??  I know in earlier versions you could go to system/preferences/sounds and set all your sounds and events there, in 9.10 when you go there all you get are hardware options.

---

### Post by atomkind on 2009-11-11
Bump

---

### Post by Ekin9.10 on 2009-11-11
I have the same question about Ubuntu 9.10., I couldn't find anywhere to change my sound options freely, does anyone now this thing? I'm new at ubuntu I used other one at school but they have different sound options please someone answer =(

---

### Post by mpe on 2009-11-11
dito problem here.
ubuntu-sounds is already installed, but it does not seem to allow configuration. 

Relevant Launchpad bugs direct to problem to the GNOME project, apparently there was some dialog-tab lost after merging packages. Note that System -> Preferences -> Startup Applications => GNOME Login Sound may help a bit (untested).

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/442763](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/442763)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429)

Update: tested and works but logoff sound is unaffected.

See also: [http://ubuntuforums.org/showthread.php?t=1305749](http://ubuntuforums.org/showthread.php?t=1305749)

---

### Post by Lvcoyote on 2009-11-11
Sometimes you just have to shake your head and wonder just what the heck these developers are thinking......LOL

---

### Post by pi.boy.travis on 2009-11-11
I don't understand the question, what options are you looking for that aren't in the new pulseaudio configuration window?  Sound effects can be configured on the very first tab, on the left.

---

### Post by Lvcoyote on 2009-11-11
The ability to manipulate the system sounds, like login, logoff, mail notification, alert sounds, etc....... What exactly are you calling the pulse audio config window??  If I right click on the sound icon in the taskbar, or go to system/preferences/sound I get the same window that opens, no system sound options are available there.

---

### Post by pi.boy.travis on 2009-11-11
Ah yes, the new sound preferences windows is missing some of it's latent customisability.  You can follow the bug [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700").

---

### Post by Lvcoyote on 2009-11-11
Yea, been there done that......

---

### Post by mpe on 2009-11-11
> **Lvcoyote said:**
> Sometimes you just have to shake your head and wonder just what the heck these developers are thinking......LOL

Sometimes doing is more important than considering all the facts, especialy on large projects imho. 

> **pi.boy.travis said:**
> I don't understand the question, what options are you looking for that aren't in the new pulseaudio configuration window?  Sound effects can be configured on the very first tab, on the left.

It has to do with sound theme, not hardware/abstraction-layer settings.

Refer to
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700) for screen shots. 

Upstream bug report for GNOME:
[https://bugzilla.gnome.org/show_bug.cgi?id=597731](https://bugzilla.gnome.org/show_bug.cgi?id=597731)

Personally, my issue is with the login/logoff sounds which to me seem superfluous as appossed to the various attention and warning sounds. But mileage may vary for different persons. The point is previous dialogs allowed customizing the sound theme at the event level.

---

