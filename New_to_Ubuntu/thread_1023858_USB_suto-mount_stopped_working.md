---
title: "USB suto-mount stopped working"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by silkstone on 2008-12-28
USB drives and sticks are no longer auto-mounted. They appear in the Nautilus sidebar and will mount if I click on them, and then they work as normal.

This started to happen a few days ago (after the last updates?) and I haven't changed fstab or anything else.

Any ideas for a solution?

Thanks.

EDIT/ Sorry - should have said that this is with 8.04 Hardy.

---

### Post by mister_pink on 2008-12-28
Not sure I quite follow - if they appear and work as normal when you click on them, then what more do you expect?

---

### Post by silkstone on 2008-12-28
When I plugged them in they used to auto-mount, the drive icon would appear on the desktop and Nautilus would open to display the contents.

Now they do not mount when I plug them in. They have to be mounted manually - from the terminal or the Nautilus sidebar.

---

### Post by drs305 on 2008-12-28
Try running these commands to set the automount option (the first for drives, the second for other media):
```

gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives "true"
gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_media "true"
```

---

### Post by silkstone on 2008-12-28
Thanks for the suggestion, but USB still doesn't auto-mount.

The strange thing is that I have changed nothing - it just stopped working.

---

### Post by drs305 on 2008-12-28
Rereading your post #3 about nautilus automatically opening once the device mounts, these are two commands that influence how nautilus reacts to inserted devices:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'true'
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open 'true'


```

---

### Post by silkstone on 2008-12-28
Sorry - that hasn't worked either. Do you have to reboot for it to take effect?

Also, in your first message you have "true" and in the second 'true'. Does that matter?

---

### Post by drs305 on 2008-12-28
> **silkstone said:**
> Sorry - that hasn't worked either. Do you have to reboot for it to take effect?

Also, in your first message you have "true" and in the second 'true'. Does that matter?

No, it doesn't make a difference whether you single or double quotes. In some instances, there is a difference between 'straight' quotes and 'fancy' quotes that angle in but I don't think that applies in this case.

Most changes to gconf take effect immediately so a restart should not be required. In this case, if you are starting with the USB devices mounted rebooting will ensure a normal umount and allow you to see if the changes made a difference.

Having said that, reboots often reset things if the problem has not persisted over multiple boots.

---

### Post by silkstone on 2008-12-28
I inserted a USB stick and for good measure also inserted a CF card in the card reader. Both showed in Places (and the Nautilus sidebar) but didn't auto-mount. I clicked on each of them and they mounted immediately.

I then rebooted with the cards mounted, but they still didn't auto-mount.

Many thanks for trying to help with this - it is a real puzzle. At least there's an easy workaround, but I'd still like to know what stopped it working.

Maybe I should do a distribution upgrade to Intrepid!

---

