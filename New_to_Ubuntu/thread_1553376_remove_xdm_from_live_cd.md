---
title: "remove xdm from live cd"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by midcommander on 2010-08-15
HOW TO REMOVE XDM FROM LIVE CD.

What i know to remove xdm (when it's fail) using this command:

```
[FONT=courier new]**# update-rc.d -f xdm remove**[/FONT]
```

but the problem is, in recovery menu I can not select netroot option (see my thread [http://ubuntuforums.org/showthread.php?t=1553370](http://ubuntuforums.org/showthread.php?t=1553370) )

either I find the solution for that problem (for the future, i need recovery mode also) or remove xdm by using live cd and install gdm again.

Perhaps my problem start because i do combination of this in the same session

first, I remove the splash screen form ```
*gedit/etc/default/grub*
``` then i change the file ```
/etc/gdm/custom.conf
``` to enable xdmcp from this thread [http://ubuntuforums.org/showthread.php?t=1471703](http://ubuntuforums.org/showthread.php?t=1471703), then i installed nxserver. the result: fatal!

the only one left that I can not fix is remove the xdm (because in recovery mode/menu i can not select netroot)

pls help :(

---

