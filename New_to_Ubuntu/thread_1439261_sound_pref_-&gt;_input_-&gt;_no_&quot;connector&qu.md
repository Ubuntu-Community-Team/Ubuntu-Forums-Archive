---
title: "sound pref -&gt; input -&gt; no &quot;connector&quot; option"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by earthpigg on 2010-03-26
hi,

fairly fresh ubuntu 9.10 install.

[IMG]http://www.blog.arun-prabha.com/wp-content/uploads/2008/05/Sound-Preferences.png[/IMG]

see that circled part next to 'connector'?

i don't seem to have it. over on the 'hardware' tab, i tried all the different options. no avail.

the objective is to get the mic working - it's plugged into the normal old-fashoned speaker/mic jack on the mobo.

ive also tried all the various options in gstreamer-connections, as well.

edit: possibly related -- alsamixer returns "alsamixer: function snd_mixer_load failed: Invalid argument"

---

### Post by earthpigg on 2010-03-26
bump

---

### Post by empty_spaces on 2010-03-26
I also had a similar issue where the regular kernels for 9.10 (2.6.31) would display the connector, but it would disappear for kernel 2.6.33 as well as for Lucid (Beta - 2.6.32)

The following worked for me. Refer to the following link, post #1.
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

In my case, my model description was ALC268, so I added 
**options snd-hda-intel model=toshiba** to /etc/modprobe.d/alsa-base.conf. Rebooted and connectors were all displayed.

Find which model applies to you from that post.

---

