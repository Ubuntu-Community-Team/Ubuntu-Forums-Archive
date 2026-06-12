---
title: "Banshee / Palm Pre"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-11-23
When I plug in my Palm Pre, Banshee (used to) pick it up as an ipod and offers to sync my music. Which I'd like it to do.

However the sync process generally hangs. Then when I try to eject the device using Banshee I get a message saying "Could not eject Media Player: org.freedesktop.Hal.Device.Volume.UnknownFailure: Cannot open/media/hal-mta".

I found /media/hal-mta, temporarily deleted it (did nothing, Banshee would no longer find the device). When I restored the file Banshee still won't find the device again.

Has anyone any advice?  Or even, how do I change the default media player that Ubuntu starts when I plug in the player?

---

### Post by blazemore on 2009-11-24
This is a known issue, there are a few threads on it.
The generally accepted workaround is this.

[LIST=1]
[*]Make sure your ipod/device is unplugged
[*]Kill nautilus with pkill -9 nautilus
[*]Kill Banshee
[*]Plug in the device
[*]Wait a minute or so
[*]Reinstate nautilus
[*]Reinstate Banshee
[/LIST]
It's a pain, I know.

---

### Post by aquascrotum on 2009-11-24
Will try this, thanks.

---

### Post by aquascrotum on 2009-11-24
> **blazemore said:**
> This is a known issue, there are a few threads on it.
The generally accepted workaround is this.

[LIST=1]
[*]Make sure your ipod/device is unplugged
[*]Kill nautilus with pkill -9 nautilus
[*]Kill Banshee
[*]Plug in the device
[*]Wait a minute or so
[*]Reinstate nautilus
[*]Reinstate Banshee
[/LIST]
It's a pain, I know.

Just out of interest, how do I reinstate nautilus and banshee?

---

