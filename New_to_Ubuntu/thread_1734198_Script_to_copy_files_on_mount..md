---
title: "Script to copy files on mount."
date: 2011-04-20
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-04-20
I would like to automatically copy the contents of a device when it mounts.

The drive is named "FreeAgent".  I currently run rsync and copy the files to "/markn/Back_ups/FreeAgent_BU/"

Can I automatically run rsync, or execute a copy command when the device "auto mounts"?

Thanks,
MarkN

---

### Post by rosencrantz on 2011-04-20
According to [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB), you should be able to configure automount actions in Gnome with System ->Preferences->Removable Drives and Media.
However, I couldn't find that item on my Natty Sandbox, maybe because they've apparently ditched HAL in the meantime. 
Edit: I found the automount config settings in the Media tab of Nautilus' Preferences. However, this can only match by device type.

For what it's worth, this might be a KDE solution: 
Right click on Device Notifier->Settings->Device Actions,
create a new action that matches your disk label and runs a bash script on connection.
The bash script contains the necessary rsync code.

---

### Post by rosencrantz on 2011-04-20
I haven't tried this yet, but you could try setting an udev rule as described here:
[https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia_only_if_the_partition_has_a_label](https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia_only_if_the_partition_has_a_label)
Change ENV{ID_FS_LABEL}=="" to ENV{ID_FS_LABEL}!="YOURLABEL", and add (I suppose) a RUN+="/somepath/yourrsyncscript.sh" after the mount commands.

---

### Post by mn_voyageur on 2011-04-20
I will read up on both of these today and see what I can try.

Thanks for the ideas.

MarkN

---

